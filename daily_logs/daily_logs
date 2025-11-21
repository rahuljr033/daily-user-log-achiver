#!/bin/bash

USER_NAME=$(whoami)

LOG_DIR="$HOME/daily_logs"
ARCHIVE_DIR="$LOG_DIR/archive"

mkdir -p "$LOG_DIR"
mkdir -p "$ARCHIVE_DIR"

logfile="$LOG_DIR/log_$(date +%Y-%m-%d).txt"

{
    echo "User: $USER_NAME"
    echo "Date: $(date)"
    echo "Uptime: $(uptime -p)"
    echo ""

    echo "Disk usage of home directory:"
    du -sh "$HOME"
    echo ""

    echo "Top 5 CPU processes:"
    ps -eo pid,comm,%mem,%cpu --sort=-%cpu | head -n 6
} >> "$logfile"

find "$LOG_DIR" -name "log_*.txt" -mtime +7 -exec mv {} "$ARCHIVE_DIR" \;

tar -czf "$LOG_DIR/weeklyLogs_$(date +%Y-%m-%d).tar.gz" "$ARCHIVE_DIR"

