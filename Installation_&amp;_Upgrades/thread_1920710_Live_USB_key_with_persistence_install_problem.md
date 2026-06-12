---
title: "Live USB key with persistence install problem"
date: 2012-02-05
forum: Installation &amp; Upgrades
---

### Post by dakkar9999 on 2012-02-05
Hello,

I've installed a Ubuntu live install with persistence on a USB stick using Unibootin [http://unetbootin.sourceforge.net/](http://unetbootin.sourceforge.net/)

I'm able to install some programs (ex. Chromium) and have persistence in my settings.  However, I am not able to install some other software.  (Ex. Wine, Synaptic...) as well as some plugins (ex. Flash).  It seems I cannot have root privilege.  I have created a password for the user Ubuntu (which I understand to be root), but I still get this error message if I try to install anything.

"installArchives() failed: dpkg: error: unable to stat triggers deferred file `/var/lib/dpkg/triggers/Unincorp': Input/output error
Error in function: "

It seems the problem is with the Unicorp file because I get this message : "/var/lib/dpkg/triggers/Unicorp': No such file or directory"


Thanks!

---

### Post by sudodus on 2012-02-05
Hi

The default in the live session is that you do not need password, not even to run sudo. But you still need to run sudo to get root privileges
```
sudo apt-get install synaptic
``` It works like that for me. An important thing is to give the system plenty of time at log-out and shut-down to write the cached data to the USB drive. Otherwise the system will be corrupted. Also it is important to have space left in the casper-rw file or partition. Please check how much space is left in your system partition!

---

### Post by dakkar9999 on 2012-02-05
I've tried your suggestion and I get this error message.

dpkg: error: unable to stat triggers deferred file `/var/lib/dpkg/triggers/Unincorp': Input/output error
E: Sub-process /usr/bin/dpkg returned an error code (2)

also I've tried running this command dpkg --clear-avail and I get this error message 

dpkg: error: unable to stat triggers deferred file `/var/lib/dpkg/triggers/Unincorp': Input/output error
E: Sub-process /usr/bin/dpkg returned an error code (2)

So it seems my problem is tied in with dpkg still being in read only mode...

---

### Post by sudodus on 2012-02-05
Why do you select to run a persistent boot system? There might be other alternatives to run your system, that is more stable or easier to manage. For example you can install (in the 'normal' way) to an external drive, which gives you unlimited possibilities to update and upgrade your system (including the kernel). But disable frequent writing, I suggest you mount your system partition with noatime.

If you have problems, and want to continue with a persistent system, I suggest that you make a new (and empty) casper-rw file and start all over. It might be that your system is so corrupted, that it is easier to start all over again.

---

