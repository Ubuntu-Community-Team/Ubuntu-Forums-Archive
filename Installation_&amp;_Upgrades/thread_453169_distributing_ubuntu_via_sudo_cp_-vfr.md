---
title: "distributing ubuntu via sudo cp -vfr"
date: 2007-05-24
forum: Installation &amp; Upgrades
---

### Post by A-1337 on 2007-05-24
Hello!
I'm trying to copy my ubuntu feisty installation to another hdd. 
+ I've created apropriate hdd layout;
+ I've copied all files via sudo cp -vfr;
+ I've changed /etc/fstab and /boot/grub according to new hdd layout;
+ I've re-installed grub via bootable floppy;

Then I've tried to boot and got first problem:
- I could login to shell but could not start graphical session; It says "mkdtemp: private socket dir"
+ I've changed /tmp permissons of /tmp to xwr for all and ti helped; why do whey changed?

Then I could login to gnome but it gave me one million error messages "can read/write configuration files" and ugly desktop w/o panels and shortcuts.
+I've ensured ownership of $HOME and permissions are ok;

Don't know what to do next. I've heard linux is very veristale and can be distributed by just copying. Am I missing something?

---

### Post by shad0w_walker on 2007-05-24
It looks like the ownership/permissions for your files got lost during the copy. If you still have the drive you copied from, try the same process again but try using:

```
cp -vfrp
```

Instead of:

```
cp -vfr
```

the p in the new command will tell copy not to change any of the files ownerships.

If you dont have the original drive still around it is in theory possible to manually change the file ownership/permissions but it can be a very long and annoying task (Been there, done that) 

If you dont really have any thing essential on your system the easiest option might simply be to backup what you need, make a list of the programs you have installed and reinstall

You can make a list of the programs you have installed by running this command:

```
dpkg --get-selections > installedfiles
```

To set the list of programs to install and then automatically download them (Remember to backup your apt.sources file so all the programs are available) use this command:

```
cat installedfiles | dpkg –set-selection; apt-get dselect-upgrade
```

Also remember to make backups of any important files like fstab, apt.sources, any custom scripts you have, etc.

---

