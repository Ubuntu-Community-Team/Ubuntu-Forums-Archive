---
title: "Power failure during upgrade to Lynx - Kernel Panic!!"
date: 2010-05-02
forum: Installation &amp; Upgrades
---

### Post by Shekibobo on 2010-05-02
So, I learned yesterday that doing a massive upgrade on my system while moving was a BAAAD idea.  The upgrade process was going along just fine, it was all downloaded and was actually installing that last time I saw it.  I unplugged my laptop to move a bookcase out, and completely forgot to plug it back in.  After I got back from moving a load, I found my computer was off.  I tried to boot up, and I got an error that kind of freaked me out.  It reads as follows:

```
kernel panic not syncing vfs unable to mount root fs on unknown-block(0,0)
```

I'm able to get to grub just fine, and my windows partition loads up just fine, but any of the linux kernels fail similarly when I attempt to load them.

I'm sure that I can fix this, I just have no idea how.  Probably has something to do with a live cd.  Can anyone help?  This is pretty devastating, and I need this fixed by the end of the week. Thanks for checking this out.

---

### Post by Shekibobo on 2010-05-02
I'm downloading the live cd now, but that says it'll take about a day.  Can anyone help with my kernel panic situation?

---

### Post by Shekibobo on 2010-05-02
I've got the live cd working, and all my files still seem to be intact. I'd hate to have to transfer all my files over to a backup drive and end up doing *yet another* full reinstall if it's not necessary.  If I do, though, home partition all the way.  Is there any way I can use the live cd to repair the system?  

I tried using the advice here: [http://ubuntuforums.org/showthread.php?t=296809&highlight=kernel+panic](http://ubuntuforums.org/showthread.php?t=296809&highlight=kernel+panic) using AgenT's advice.  I got the the mounting to work with a few minor adjustments, but after trying to run apt-get, I get some problems.  I tried running apt-get update and most of the repositories, if not all, failed to update, and the error "E: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem.


...


This may be fixing the problem - seems like it's going through and actually installing the updates that were downloaded. I'll keep you updated.

---

### Post by dino99 on 2010-05-02
you can goto synaptic (system admin synaptic) and reinstall the kernel packages

sudo dpkg --configure -a
sudo apt-get update
sudo apt-get install -f

---

