---
title: "Synaptic Package Manager Broken"
date: 2007-06-11
forum: Installation &amp; Upgrades
---

### Post by Pumalite on 2007-06-11
Synapted crashed wile installing Java sdk. Now opens with Error: 'dpkg was interrupted, you must manually run "dpkg --configure -a" to correct the problem. When I run the command in terminal I get:

'command not found' even though I'm using sudo. What to do now. Without synaptic manager I'm done. Help please. I just reinstalled 7.04.

---

### Post by Pumalite on 2007-06-11
> **Pumalite said:**
> Synapted crashed wile installing Java sdk. Now opens with Error: 'dpkg was interrupted, you must manually run "dpkg --configure -a" to correct the problem. When I run the command in terminal I get:

'command not found' even though I'm using sudo. What to do now. Without synaptic manager I'm done. Help please. I just reinstalled 7.04.

This is the output in my Terminal:

pumalite@pumalite-desktop:~$ sudo pkdg --configure -a
sudo: pkdg: command not found
pumalite@pumalite-desktop:~$ sudo install pkdg
install: missing destination file operand after `pkdg'
Try `install --help' for more information.
pumalite@pumalite-desktop:~$ sudo install --help
Usage: install [OPTION]... [-T] SOURCE DEST
  or:  install [OPTION]... SOURCE... DIRECTORY
  or:  install [OPTION]... -t DIRECTORY SOURCE...
  or:  install [OPTION]... -d DIRECTORY...
In the first three forms, copy SOURCE to DEST or multiple SOURCE(s) to
the existing DIRECTORY, while setting permission modes and owner/group.
In the 4th form, create all components of the given DIRECTORY(ies).

Mandatory arguments to long options are mandatory for short options too.
      --backup[=CONTROL] make a backup of each existing destination file
  -b                  like --backup but does not accept an argument
  -c                  (ignored)
  -d, --directory     treat all arguments as directory names; create all
                        components of the specified directories
  -D                  create all leading components of DEST except the last,
                        then copy SOURCE to DEST
  -g, --group=GROUP   set group ownership, instead of process' current group
  -m, --mode=MODE     set permission mode (as in chmod), instead of rwxr-xr-x
  -o, --owner=OWNER   set ownership (super-user only)
  -p, --preserve-timestamps   apply access/modification times of SOURCE files
                        to corresponding destination files
  -s, --strip         strip symbol tables
  -S, --suffix=SUFFIX override the usual backup suffix
  -t, --target-directory=DIRECTORY  copy all SOURCE arguments into DIRECTORY
  -T, --no-target-directory  treat DEST as a normal file
  -v, --verbose       print the name of each directory as it is created
  -P, --preserve_context (SELinux) Preserve security context
  -Z, --context=CONTEXT  (SELinux) Set security context of files and directories
      --help     display this help and exit
      --version  output version information and exit

The backup suffix is `~', unless set with --suffix or SIMPLE_BACKUP_SUFFIX.
The version control method may be selected via the --backup option or through
the VERSION_CONTROL environment variable.  Here are the values:

  none, off       never make backups (even if --backup is given)
  numbered, t     make numbered backups
  existing, nil   numbered if numbered backups exist, simple otherwise
  simple, never   always make simple backups

Report bugs to <bug-coreutils@gnu.org>.
pumalite@pumalite-desktop:~$

I don't know where to install pkdg.

---

### Post by Pumalite on 2007-06-11
> **Pumalite said:**
> This is the output in my Terminal:

pumalite@pumalite-desktop:~$ sudo pkdg --configure -a
sudo: pkdg: command not found
pumalite@pumalite-desktop:~$ sudo install pkdg
install: missing destination file operand after `pkdg'
Try `install --help' for more information.
pumalite@pumalite-desktop:~$ sudo install --help
Usage: install [OPTION]... [-T] SOURCE DEST
  or:  install [OPTION]... SOURCE... DIRECTORY
  or:  install [OPTION]... -t DIRECTORY SOURCE...
  or:  install [OPTION]... -d DIRECTORY...
In the first three forms, copy SOURCE to DEST or multiple SOURCE(s) to
the existing DIRECTORY, while setting permission modes and owner/group.
In the 4th form, create all components of the given DIRECTORY(ies).

Mandatory arguments to long options are mandatory for short options too.
      --backup[=CONTROL] make a backup of each existing destination file
  -b                  like --backup but does not accept an argument
  -c                  (ignored)
  -d, --directory     treat all arguments as directory names; create all
                        components of the specified directories
  -D                  create all leading components of DEST except the last,
                        then copy SOURCE to DEST
  -g, --group=GROUP   set group ownership, instead of process' current group
  -m, --mode=MODE     set permission mode (as in chmod), instead of rwxr-xr-x
  -o, --owner=OWNER   set ownership (super-user only)
  -p, --preserve-timestamps   apply access/modification times of SOURCE files
                        to corresponding destination files
  -s, --strip         strip symbol tables
  -S, --suffix=SUFFIX override the usual backup suffix
  -t, --target-directory=DIRECTORY  copy all SOURCE arguments into DIRECTORY
  -T, --no-target-directory  treat DEST as a normal file
  -v, --verbose       print the name of each directory as it is created
  -P, --preserve_context (SELinux) Preserve security context
  -Z, --context=CONTEXT  (SELinux) Set security context of files and directories
      --help     display this help and exit
      --version  output version information and exit

The backup suffix is `~', unless set with --suffix or SIMPLE_BACKUP_SUFFIX.
The version control method may be selected via the --backup option or through
the VERSION_CONTROL environment variable.  Here are the values:

  none, off       never make backups (even if --backup is given)
  numbered, t     make numbered backups
  existing, nil   numbered if numbered backups exist, simple otherwise
  simple, never   always make simple backups

Report bugs to <bug-coreutils@gnu.org>.
pumalite@pumalite-desktop:~$

I don't know where to install pkdg.

This is the output from synaptic when I try to open it:

pumalite@pumalite-desktop:~$ sudo pkdg --configure -a
sudo: pkdg: command not found
pumalite@pumalite-desktop:~$ sudo install pkdg
install: missing destination file operand after `pkdg'
Try `install --help' for more information.
pumalite@pumalite-desktop:~$ sudo install --help
Usage: install [OPTION]... [-T] SOURCE DEST
  or:  install [OPTION]... SOURCE... DIRECTORY
  or:  install [OPTION]... -t DIRECTORY SOURCE...
  or:  install [OPTION]... -d DIRECTORY...
In the first three forms, copy SOURCE to DEST or multiple SOURCE(s) to
the existing DIRECTORY, while setting permission modes and owner/group.
In the 4th form, create all components of the given DIRECTORY(ies).

Mandatory arguments to long options are mandatory for short options too.
      --backup[=CONTROL] make a backup of each existing destination file
  -b                  like --backup but does not accept an argument
  -c                  (ignored)
  -d, --directory     treat all arguments as directory names; create all
                        components of the specified directories
  -D                  create all leading components of DEST except the last,
                        then copy SOURCE to DEST
  -g, --group=GROUP   set group ownership, instead of process' current group
  -m, --mode=MODE     set permission mode (as in chmod), instead of rwxr-xr-x
  -o, --owner=OWNER   set ownership (super-user only)
  -p, --preserve-timestamps   apply access/modification times of SOURCE files
                        to corresponding destination files
  -s, --strip         strip symbol tables
  -S, --suffix=SUFFIX override the usual backup suffix
  -t, --target-directory=DIRECTORY  copy all SOURCE arguments into DIRECTORY
  -T, --no-target-directory  treat DEST as a normal file
  -v, --verbose       print the name of each directory as it is created
  -P, --preserve_context (SELinux) Preserve security context
  -Z, --context=CONTEXT  (SELinux) Set security context of files and directories
      --help     display this help and exit
      --version  output version information and exit

The backup suffix is `~', unless set with --suffix or SIMPLE_BACKUP_SUFFIX.
The version control method may be selected via the --backup option or through
the VERSION_CONTROL environment variable.  Here are the values:

  none, off       never make backups (even if --backup is given)
  numbered, t     make numbered backups
  existing, nil   numbered if numbered backups exist, simple otherwise
  simple, never   always make simple backups

Report bugs to <bug-coreutils@gnu.org>.
pumalite@pumalite-desktop:~$ 

pumalite@pumalite-desktop:~$ sudo pkdg --configure -a
sudo: pkdg: command not found
pumalite@pumalite-desktop:~$ sudo install pkdg
install: missing destination file operand after `pkdg'
Try `install --help' for more information.
pumalite@pumalite-desktop:~$ sudo install --help
Usage: install [OPTION]... [-T] SOURCE DEST
  or:  install [OPTION]... SOURCE... DIRECTORY
  or:  install [OPTION]... -t DIRECTORY SOURCE...
  or:  install [OPTION]... -d DIRECTORY...
In the first three forms, copy SOURCE to DEST or multiple SOURCE(s) to
the existing DIRECTORY, while setting permission modes and owner/group.
In the 4th form, create all components of the given DIRECTORY(ies).

Mandatory arguments to long options are mandatory for short options too.
      --backup[=CONTROL] make a backup of each existing destination file
  -b                  like --backup but does not accept an argument
  -c                  (ignored)
  -d, --directory     treat all arguments as directory names; create all
                        components of the specified directories
  -D                  create all leading components of DEST except the last,
                        then copy SOURCE to DEST
  -g, --group=GROUP   set group ownership, instead of process' current group
  -m, --mode=MODE     set permission mode (as in chmod), instead of rwxr-xr-x
  -o, --owner=OWNER   set ownership (super-user only)
  -p, --preserve-timestamps   apply access/modification times of SOURCE files
                        to corresponding destination files
  -s, --strip         strip symbol tables
  -S, --suffix=SUFFIX override the usual backup suffix
  -t, --target-directory=DIRECTORY  copy all SOURCE arguments into DIRECTORY
  -T, --no-target-directory  treat DEST as a normal file
  -v, --verbose       print the name of each directory as it is created
  -P, --preserve_context (SELinux) Preserve security context
  -Z, --context=CONTEXT  (SELinux) Set security context of files and directories
      --help     display this help and exit
      --version  output version information and exit

The backup suffix is `~', unless set with --suffix or SIMPLE_BACKUP_SUFFIX.
The version control method may be selected via the --backup option or through
the VERSION_CONTROL environment variable.  Here are the values:

  none, off       never make backups (even if --backup is given)
  numbered, t     make numbered backups
  existing, nil   numbered if numbered backups exist, simple otherwise
  simple, never   always make simple backups

Report bugs to <bug-coreutils@gnu.org>.
pumalite@pumalite-desktop:~$ 

???

---

### Post by lizzard on 2007-06-11
Looks like a typo. You should run "dpkg --configure -a" ** not ** "pkdg --configure -a" .

---

### Post by Pumalite on 2007-06-11
> **Pumalite said:**
> This is the output from synaptic when I try to open it:

pumalite@pumalite-desktop:~$ sudo pkdg --configure -a
sudo: pkdg: command not found
pumalite@pumalite-desktop:~$ sudo install pkdg
install: missing destination file operand after `pkdg'
Try `install --help' for more information.
pumalite@pumalite-desktop:~$ sudo install --help
Usage: install [OPTION]... [-T] SOURCE DEST
  or:  install [OPTION]... SOURCE... DIRECTORY
  or:  install [OPTION]... -t DIRECTORY SOURCE...
  or:  install [OPTION]... -d DIRECTORY...
In the first three forms, copy SOURCE to DEST or multiple SOURCE(s) to
the existing DIRECTORY, while setting permission modes and owner/group.
In the 4th form, create all components of the given DIRECTORY(ies).

Mandatory arguments to long options are mandatory for short options too.
      --backup[=CONTROL] make a backup of each existing destination file
  -b                  like --backup but does not accept an argument
  -c                  (ignored)
  -d, --directory     treat all arguments as directory names; create all
                        components of the specified directories
  -D                  create all leading components of DEST except the last,
                        then copy SOURCE to DEST
  -g, --group=GROUP   set group ownership, instead of process' current group
  -m, --mode=MODE     set permission mode (as in chmod), instead of rwxr-xr-x
  -o, --owner=OWNER   set ownership (super-user only)
  -p, --preserve-timestamps   apply access/modification times of SOURCE files
                        to corresponding destination files
  -s, --strip         strip symbol tables
  -S, --suffix=SUFFIX override the usual backup suffix
  -t, --target-directory=DIRECTORY  copy all SOURCE arguments into DIRECTORY
  -T, --no-target-directory  treat DEST as a normal file
  -v, --verbose       print the name of each directory as it is created
  -P, --preserve_context (SELinux) Preserve security context
  -Z, --context=CONTEXT  (SELinux) Set security context of files and directories
      --help     display this help and exit
      --version  output version information and exit

The backup suffix is `~', unless set with --suffix or SIMPLE_BACKUP_SUFFIX.
The version control method may be selected via the --backup option or through
the VERSION_CONTROL environment variable.  Here are the values:

  none, off       never make backups (even if --backup is given)
  numbered, t     make numbered backups
  existing, nil   numbered if numbered backups exist, simple otherwise
  simple, never   always make simple backups

Report bugs to <bug-coreutils@gnu.org>.
pumalite@pumalite-desktop:~$ 

pumalite@pumalite-desktop:~$ sudo pkdg --configure -a
sudo: pkdg: command not found
pumalite@pumalite-desktop:~$ sudo install pkdg
install: missing destination file operand after `pkdg'
Try `install --help' for more information.
pumalite@pumalite-desktop:~$ sudo install --help
Usage: install [OPTION]... [-T] SOURCE DEST
  or:  install [OPTION]... SOURCE... DIRECTORY
  or:  install [OPTION]... -t DIRECTORY SOURCE...
  or:  install [OPTION]... -d DIRECTORY...
In the first three forms, copy SOURCE to DEST or multiple SOURCE(s) to
the existing DIRECTORY, while setting permission modes and owner/group.
In the 4th form, create all components of the given DIRECTORY(ies).

Mandatory arguments to long options are mandatory for short options too.
      --backup[=CONTROL] make a backup of each existing destination file
  -b                  like --backup but does not accept an argument
  -c                  (ignored)
  -d, --directory     treat all arguments as directory names; create all
                        components of the specified directories
  -D                  create all leading components of DEST except the last,
                        then copy SOURCE to DEST
  -g, --group=GROUP   set group ownership, instead of process' current group
  -m, --mode=MODE     set permission mode (as in chmod), instead of rwxr-xr-x
  -o, --owner=OWNER   set ownership (super-user only)
  -p, --preserve-timestamps   apply access/modification times of SOURCE files
                        to corresponding destination files
  -s, --strip         strip symbol tables
  -S, --suffix=SUFFIX override the usual backup suffix
  -t, --target-directory=DIRECTORY  copy all SOURCE arguments into DIRECTORY
  -T, --no-target-directory  treat DEST as a normal file
  -v, --verbose       print the name of each directory as it is created
  -P, --preserve_context (SELinux) Preserve security context
  -Z, --context=CONTEXT  (SELinux) Set security context of files and directories
      --help     display this help and exit
      --version  output version information and exit

The backup suffix is `~', unless set with --suffix or SIMPLE_BACKUP_SUFFIX.
The version control method may be selected via the --backup option or through
the VERSION_CONTROL environment variable.  Here are the values:

  none, off       never make backups (even if --backup is given)
  numbered, t     make numbered backups
  existing, nil   numbered if numbered backups exist, simple otherwise
  simple, never   always make simple backups

Report bugs to <bug-coreutils@gnu.org>.
pumalite@pumalite-desktop:~$ 

???

Fixed!!! Installed dpkg. Ran sudo dpkg --configure -a and done!!!

---

