---
title: "Error in uninstalling VirtualBox"
date: 2020-03-15
forum: Installation &amp; Upgrades
---

### Post by insert.memories.here on 2020-03-15
Hey folks!

Ubuntu 18.04.4 LTS

I recently installed Oracle VM Virtualbox through the Ubuntu Software app, however processing issues haven't allowed it to open and run at any time.

Now that I'm trying to uninstall though the terminal, this error appears...

```
sudo apt-get remove --purge virtualbox-6.1
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libqt5opengl5 libqt5printsupport5 libqt5x11extras5 libsdl-ttf2.0-0
  libsdl1.2debian
Use 'sudo apt autoremove' to remove them.
The following packages will be REMOVED:
  virtualbox-6.1*
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
After this operation, 216 MB disk space will be freed.
Do you want to continue? [Y/n] Y
debconf: DbDriver "config": /var/cache/debconf/config.dat is locked by another process: Resource temporarily unavailable
(Reading database ... 180935 files and directories currently installed.)
Removing virtualbox-6.1 (6.1.4-136177~Ubuntu~bionic) ...
debconf: DbDriver "config": /var/cache/debconf/config.dat is locked by another process: Resource temporarily unavailable
dpkg: error processing package virtualbox-6.1 (--remove):
 installed virtualbox-6.1 package pre-removal script subprocess returned error exit status 1
debconf: DbDriver "config": /var/cache/debconf/config.dat is locked by another process: Resource temporarily unavailable
vboxdrv.sh: failed: modprobe vboxdrv failed. Please use 'dmesg' to find out why.

There were problems setting up VirtualBox.  To re-start the set-up process, run
  /sbin/vboxconfig
as root.  If your system is using EFI Secure Boot you may need to sign the
kernel modules (vboxdrv, vboxnetflt, vboxnetadp, vboxpci) before you can load
them. Please see your Linux system's documentation for more information.
Errors were encountered while processing:
 virtualbox-6.1
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

It says config.dat is locked by another process and can't be accessed, however I'm sure there were no other processes running in my computer. But I'm a noob so what would I know.

Nothing has occurred, I still have VirtualBox in my computer.

---

### Post by insert.memories.here on 2020-03-16
Just came back to say I still have this problem. Bumping it so it can have some attention. I see that not so many people use this site as much anymore so I'm also going to bring this question up in askubuntu-stackexchange, and oracle themselves if I can.

---

### Post by deadflowr on 2020-03-16
Look over these,
[https://askubuntu.com/questions/136881/debconf-dbdriver-config-config-dat-is-locked-by-another-process-resource-t]("https://askubuntu.com/questions/136881/debconf-dbdriver-config-config-dat-is-locked-by-another-process-resource-t")
[https://wiki.ubuntu.com/DebuggingInstallationIssues#DbDriver_.22config.22_is_locked]("https://wiki.ubuntu.com/DebuggingInstallationIssues#DbDriver_.22config.22_is_locked")

---

### Post by insert.memories.here on 2020-03-17
Thanks! I didn't know this can be an issue for other applications as well. You're doing god's work!

---

### Post by insert.memories.here on 2020-03-17
Alright, this is what came up...

when trying ```
  ~$ sudo fuser -v /var/cache/debconf/config.dat 
```

```
 ~$ sudo fuser -v /var/cache/debconf/config.datCannot stat file /proc/3679/fd/4: Permission denied
Cannot stat file /proc/3679/fd/7: Permission denied
Cannot stat file /proc/3679/fd/8: Permission denied
Cannot stat file /proc/3679/fd/9: Permission denied
Cannot stat file /proc/8693/fd/25: Permission denied
Cannot stat file /proc/8693/fd/26: Permission denied
Cannot stat file /proc/8693/fd/27: Permission denied
Cannot stat file /proc/8693/fd/28: Permission denied
Cannot stat file /proc/8693/fd/29: Permission denied
Cannot stat file /proc/8693/fd/79: Permission denied
Cannot stat file /proc/8693/fd/80: Permission denied
Cannot stat file /proc/8693/fd/1023: Permission denied
Cannot stat file /proc/27899/fd/6: Permission denied
Cannot stat file /proc/27899/fd/7: Permission denied
Cannot stat file /proc/27899/fd/8: Permission denied
Cannot stat file /proc/27899/fd/9: Permission denied
Cannot stat file /proc/27899/fd/10: Permission denied
Cannot stat file /proc/27899/fd/11: Permission denied
Cannot stat file /proc/31410/fd/6: Permission denied
Cannot stat file /proc/31410/fd/7: Permission denied
Cannot stat file /proc/31410/fd/8: Permission denied
Cannot stat file /proc/31410/fd/9: Permission denied
Cannot stat file /proc/31410/fd/10: Permission denied
Cannot stat file /proc/31410/fd/11: Permission denied
Cannot stat file /proc/31410/fd/16: Permission denied
Cannot stat file /proc/31410/fd/17: Permission denied
                     USER        PID ACCESS COMMAND
/var/cache/debconf/config.dat:
                     root       8182 F.... frontend

```

Permission denied for stat files. Continuing with the killing process, I tried...

```
 $ sudo kill PID
kill: failed to parse argument: 'PID'

```

...and...

```
 ~$ sudo kill -9 PID
kill: failed to parse argument: 'PID'
  
```

I figure that I should run as root and try this process over again.

---

### Post by insert.memories.here on 2020-04-05
Bump. This is still an issue for me, the code above are the errors that show up after trying the fuser command.

---

### Post by roundrock90210 on 2020-04-05
Ubuntu has software that looks for packages that need updating. If it is doing this, it will not allow you to install using the command line. Look on the task bar for something that has taken control of the ability to install. If you see an icon that when you hover over it says, these packages are ready for updating could be the problem.

---

### Post by deadflowr on 2020-04-05
PID is a corresponding number which at the time you ran the commands was 8182,
but might have changed since so you'd have to run the command again.

---

### Post by pbear42 on 2020-04-06
Every once in a while, sudo doesn't quite work.  Try dropping to root with **sudo -i** and running the command again.  
Whether works or not, exit before doing anything else, cuz you can do a lot of damage while logged in as root.

---

