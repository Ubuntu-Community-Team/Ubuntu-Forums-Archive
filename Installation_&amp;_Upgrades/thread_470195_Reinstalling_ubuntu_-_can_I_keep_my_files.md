---
title: "Reinstalling ubuntu - can I keep my files?"
date: 2007-06-10
forum: Installation &amp; Upgrades
---

### Post by InternationalRescue on 2007-06-10
hi, my brother tried to put a program onto the family pc running feisty fawn, and now after logging on all you get is a white screen.(the program was easyubuntu)i have no option but to reinstall, and there are several GBs of family pictures and important word docs etc, so its pretty important the files dont get wiped during reinstall. what is the best way to go about with the installation, and which of the partition options should i choose (ie guided manuat etc)

any help would be great thanks guys

---

### Post by merlinus on 2007-06-10
You might try booting from the live cd, and backup important data before installing and possibly having to re-partition and re-format.

Safer that way....

;)

-merlin

---

### Post by brownknight on 2007-06-10
Have you tried to remove easyubuntu first? I would try pressing ctrl+alt-F1 to open a new TTY. Login and then in there maybe type **sudo apt-get remove easyubuntu**. when that is done you can try pressing Alt-F7 to go back to graphical desktop.

Im a noob so I am not 100% sure but you can try this out. Hope this helps.

---

### Post by InternationalRescue on 2007-06-10
> **merlinus said:**
> You might try booting from the live cd, and backup important data before installing and possibly having to re-partition and re-format.

Safer that way....

;)

-merlin

thanks for the advice, i have tried to do exactly that, but running from the live cd, it doesnt seem to give you access to the folders, ie i can see them but when i try to open them i get a message saying restricted access/do not have user rights etc, and i cant even copy the files over to any removable storage. if i reinstalled onto a new partition do you have any idea whether the old files would remain, and would they be accessible from the new partition install?
thanks again for your help!

---

### Post by brownknight on 2007-06-10
> **InternationalRescue said:**
>  but when i try to open them i get a message saying restricted access/do not have user rights etc, and i cant even copy the files over to any removable storage.

Can you try copying these files using the terminal > open the terminal and type
[B]
sudo cp  filename-of-file-to-copy  location-of-copy-file-and-filename[/B]

---

### Post by InternationalRescue on 2007-06-15
hey thanks for your help again, i have tried using the terminal to copy files but i usually get error messages. the files i want to copy are in:
**/media/disk/home/charlie/Pictures**
and i want to copy them to:
**/media/KINGSTON/**
below is the code i attempted to use, will this work? Does this method copy single files or can it be used to copy folders (which would be ideal)

```
sudo cp /media/disk/home/charlie/Pictures /media/KINGSTON/
```

Many thanks again!

---

### Post by InternationalRescue on 2007-06-15
This is the help that the the terminal provides, still a bit confused though, what exactly would i put to copy a folder from one source to another destination?

```
ubuntu@ubuntu:~$ cp --help
Usage: cp [OPTION]... [-T] SOURCE DEST
  or:  cp [OPTION]... SOURCE... DIRECTORY
  or:  cp [OPTION]... -t DIRECTORY SOURCE...
Copy SOURCE to DEST, or multiple SOURCE(s) to DIRECTORY.

Mandatory arguments to long options are mandatory for short options too.
  -a, --archive                same as -dpR
      --backup[=CONTROL]       make a backup of each existing destination file
  -b                           like --backup but does not accept an argument
      --copy-contents          copy contents of special files when recursive
  -d                           same as --no-dereference --preserve=link
  -f, --force                  if an existing destination file cannot be
                                 opened, remove it and try again
  -i, --interactive            prompt before overwrite
  -H                           follow command-line symbolic links
  -l, --link                   link files instead of copying
  -L, --dereference            always follow symbolic links
  -P, --no-dereference         never follow symbolic links
  -p                           same as --preserve=mode,ownership,timestamps
      --preserve[=ATTR_LIST]   preserve the specified attributes (default:
                                 mode,ownership,timestamps), if possible
                                 additional attributes: links, all
  -c                           same as --preserve=context
      --no-preserve=ATTR_LIST  don't preserve the specified attributes
      --parents                use full source file name under DIRECTORY
  -R, -r, --recursive          copy directories recursively
      --remove-destination     remove each existing destination file before
                                 attempting to open it (contrast with --force)
      --sparse=WHEN            control creation of sparse files
      --strip-trailing-slashes remove any trailing slashes from each SOURCE
                                 argument
  -s, --symbolic-link          make symbolic links instead of copying
  -S, --suffix=SUFFIX          override the usual backup suffix
  -t, --target-directory=DIRECTORY  copy all SOURCE arguments into DIRECTORY
  -T, --no-target-directory    treat DEST as a normal file
  -u, --update                 copy only when the SOURCE file is newer
                                 than the destination file or when the
                                 destination file is missing
  -v, --verbose                explain what is being done
  -x, --one-file-system        stay on this file system
  -Z, --context=CONTEXT        set security context of copy to CONTEXT
      --help     display this help and exit
      --version  output version information and exit

By default, sparse SOURCE files are detected by a crude heuristic and the
corresponding DEST file is made sparse as well.  That is the behavior
selected by --sparse=auto.  Specify --sparse=always to create a sparse DEST
file whenever the SOURCE file contains a long enough sequence of zero bytes.
Use --sparse=never to inhibit creation of sparse files.

The backup suffix is `~', unless set with --suffix or SIMPLE_BACKUP_SUFFIX.
The version control method may be selected via the --backup option or through
the VERSION_CONTROL environment variable.  Here are the values:

  none, off       never make backups (even if --backup is given)
  numbered, t     make numbered backups
  existing, nil   numbered if numbered backups exist, simple otherwise
  simple, never   always make simple backups

As a special case, cp makes a backup of SOURCE when the force and backup
options are given and SOURCE and DEST are the same name for an existing,
regular file.

```

---

### Post by sweetcancer on 2007-06-30
i did it with live cd just typing sudo nautilus /media to get the super user acces to my files and then just copy paste to my external drive. ican give you more detailed description when i get home.

---

