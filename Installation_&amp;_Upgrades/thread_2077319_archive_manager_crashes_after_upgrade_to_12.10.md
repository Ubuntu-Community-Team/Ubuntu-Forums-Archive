---
title: "archive manager crashes after upgrade to 12.10"
date: 2012-10-28
forum: Installation &amp; Upgrades
---

### Post by wa1d0rf on 2012-10-28
I've discovered that the archive manager crashes every time I try to extract files from an archive.  it seems to begin to open, then immediately closes without an error message/dialog or anything.  I want to extract some theme packages but I can't get this to work as it did before the upgrade.  

I've shutdown and restarted the system, I have done all system updates.  I've even tried to uninstall it and re-install.  Nothing seems to change the condition.

Anyone have any ideas?

---

### Post by verymadpip on 2012-10-28
Same here.  I can't offer any help either, except to try extracting the file from CLI, which works for me:
[http://askubuntu.com/questions/25961/how-to-install-a-tar-gz-or-tar-bz2-file](http://askubuntu.com/questions/25961/how-to-install-a-tar-gz-or-tar-bz2-file)
This includes the commands for the extraction.

I think this is the bug:
[https://bugs.launchpad.net/ubuntu/+source/file-roller/+bug/1037844](https://bugs.launchpad.net/ubuntu/+source/file-roller/+bug/1037844)

---

### Post by tophill on 2012-10-30
me too!

---

### Post by Frogs Hair on 2012-10-30
GTK themes not compatible with Gnome 3.6 can cause this problem. Test with a default theme to eliminate this possibility.

---

### Post by verymadpip on 2012-10-31
This happens in Xubuntu 12.10 too.  Surely that's nothing to do with Gnome 3.6?  I could be missing something there though.

---

### Post by pqwoerituytrueiwoq on 2012-10-31
downgrade fileroller (worked great for me)
[http://packages.ubuntu.com/precise/file-roller#pdownload](http://packages.ubuntu.com/precise/file-roller#pdownload) (bottom of page)
run ```
sudo apt-get purge file-roller
``` before installing the deb

---

### Post by cb951303 on 2012-11-01
same here. this is really annoying

---

### Post by tophill on 2012-11-02
Newest version of file-roller 3.6.1.1, which is currently in proposed updates, fixes this.
See [http://fileroller.sourceforge.net/](http://fileroller.sourceforge.net/)
It worked for me.

---

### Post by shankru85 on 2012-11-04
try installing xarchiver for now as a workaround, which is what i did.

---

### Post by jcruiz on 2012-11-27
> **pqwoerituytrueiwoq said:**
> downgrade fileroller (worked great for me)
[http://packages.ubuntu.com/precise/file-roller#pdownload](http://packages.ubuntu.com/precise/file-roller#pdownload) (bottom of page)
run ```
sudo apt-get purge file-roller
``` before installing the deb

Thanks this solves the issue. In my case I wasn't able to work with EAR or war files. I've updated the bug with the file type.

Thanks for the workaround

JC

---

