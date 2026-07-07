# ls_custom 

A partial reimplementation of the Unix `ls` command in C, written to learn the
filesystem syscall layer `opendir`/`readdir` for directory iteration and
`lstat` for per-file metadata.

## Features

- Lists the contents of a directory (defaults to the current directory)
- `-a` — include hidden entries (names starting with `.`)
- `-l` — long format: permissions, link count, owner, group, size, modification time
- Flags combine (`-la`, `-al`, `-l -a` all work)

## Build

```sh
gcc -Wall -Wextra -o ls_custom ls_custom.c
```

## Usage

```sh
./ls_custom              # list current directory
./ls_custom -a           # include hidden files
./ls_custom -l /tmp      # long format for /tmp
./ls_custom -la          # hidden files, long format
```

## Example

```
$ ./ls_custom -l
drwxr-xr-x 2 user group  4096 Jul  7 14:32 src
-rw-r--r-- 1 user group 1204 Jul  7 14:30 ls_custom.c
-rw-r--r-- 1 user group 312 Jul  7 14:31 README.md
```

## Work in progress

This is a project for learning and not a drop-in `ls` replacement.

- No column padding/alignment output is space separated
- No sorting entries appear in filesystem order (real `ls` sorts alphabetically)
