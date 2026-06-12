---
title: "How to Convert from Fedora to Ubuntu Easily?"
date: 2007-02-05
forum: Installation &amp; Upgrades
---

### Post by dealmaker on 2007-02-05
Hi,
  I am currently using Fedora Core 6.  I want to convert to Ubuntu.  Is there a easy way to do it without reinstalling everything?
Thanks.

---

### Post by alxjl on 2007-02-05
Sorry, you'd have to wipe out Fedora for you to use Ubuntu. If it were Debian, then there'd be a way to convert to Ubuntu. Fedora is an RPM based distro like Red Hat, Mandriva, etc.so no luck, i think.

---

### Post by kairu0 on 2007-02-05
Maybe there is a way, but you wouldn't want to. The two distros have grown in different directions, and it's better to start anew.

---

### Post by kebes on 2007-02-05
Well one thing you can do to ease the transition is to copy *all* the contents of your home partition on Fedora to your home partition on a new Ubuntu install. This includes all the hidden files and directories (which start with a dot, "."). These hidden files store the config data for many of your apps and desktop settings.

You will still have to re-install all your software, but once done, much of the software should at least have the settings you remember (such as bookmarks, user prefs, etc.).

Note that this is only for user programs... things like servers store their config data elsewhere. You should make copies of all of those files (samba, xorg, etc.), which will make it easier to get up-and-running in a new Ubuntu install.

---

### Post by Dylnuge on 2007-02-05
You **can** transfer files. Put them on a disk, then load them in Ubuntu. Just make sure to tell Ubuntu to use the same file system your Fedora system used (if you had ext2 files, ext3 might work, but if you had ext3 files you will want to use ext3 on the new system). Software wise, you will be reloading everything.

Any and all files in your /usr/ directory should be enough. Some programs will store themselves in other folders, in which case it is best to start anew with them.

---

