---
title: "Ubuntu LTS 12.04 takes 15-20 minutes to boot"
date: 2012-06-15
forum: Installation &amp; Upgrades
---

### Post by Prescilla on 2012-06-15
Please help.

My Ubuntu Precise Pangolin installation was booting up pretty fast, it takes about 10-15 seconds to boot until today.

When I turn on my PC this morning it was taking a very long time to boot maybe about 5 minutes that I decided to press the reset button then encountered unknown file system and grub rescue error. But I was able to fix this by booting on the LiveUSB, check and fix the filesystem via gparted.

I decided to purge grub2 and reinstall it, update grub and restart, because I was thinking that the boot time has something to do with grub.

But the next time I boot, it took about 18 minutes for Ubuntu to boot!!!
I don't know what could be the problem.
I do not see any error messages on the screen.
Just the Ubuntu logo and the dots indicating that it is booting.
Can someone please help me????
I really don't want to reinstall Ubuntu.

---

### Post by Hari5g900 on 2012-06-15
Why not reinstall? Maybe if you boot it from the LiveUSB again and try the recovery installation mode, the problem may be fixed.

---

### Post by Prescilla on 2012-06-15
I was able to boot, in fact I am running Ubuntu now, but it took about 18 minutes or so before I was able to get to my desktop.

I only purged and reinstalled grub while running Ubuntu. I was afraid of rebooting again cos I know it will take me that long again to be able to use Ubuntu.

I don't want to reinstall the entire OS.

---

### Post by Hari5g900 on 2012-06-26
Well then, you should check whether you have any problems with your hardware??????????(Just a wild guess)

---

### Post by cortman on 2012-06-26
Boot up, and right after boot up run

```
dmesg > ~/dmesg.t
```

Then copy/paste the contents of the new dmesg.t file in your home directory here, between [CODE] tags (the hash symbol on the editing toolbar).

---

### Post by oldfred on 2012-06-26
+1 on cortman suggestion.

But you may be able to review dmesg and see if there is a long time between entries. Or some entry posted multiple times and then timing out. You could then just post that part.

Every 40 or so reboots it also does a file check fsck or e2fsck to verify file system. With ext4 that check goes very fast, but if ext3 or ext2 it may take a while.

---

### Post by efflandt on 2012-06-26
**dmesg | less**
can let you look though things that happened during and since booting, but I am not sure how far back that goes until you lose the beginning (may depend upon memory).

Otherwise look through **/var/log/dmesg** or **/var/log/syslog** for anything unusual or errors, especially anything related to drive access, if something got corrupted on a drive or a drive is acting up.

But as mentioned, Linux fsck's drives occasionally during boot and unfortunately Ubuntu no longer provides indication of progress, and that could take awhile for a large partition.

---

### Post by josephmills on 2012-06-26
> **Prescilla said:**
> 
I don't know what could be the problem.
I do not see any error messages on the screen.
Just the Ubuntu logo and the dots indicating that it is booting.
Can someone please help me????
I really don't want to reinstall Ubuntu.

Press the left arrow or up arrow when this is happening this will give you a screen of what is going on. Also I say run 
```
dmesg
``` and look for any errors and what not dmesg gives us a list of what the kernel sees at boot time :) Hope that this helps.

**EDIT**
Dang cortman is a fast  :)

---

### Post by Prescilla on 2012-06-30
> **josephmills said:**
> Press the left arrow or up arrow when this is happening this will give you a screen of what is going on. Also I say run 
```
dmesg
``` and look for any errors and what not dmesg gives us a list of what the kernel sees at boot time :) Hope that this helps.

**EDIT**
Dang cortman is a fast  :)

Thank you guys for all the response.
I ended up reinstalling Ubuntu.
But now I've encountered another problem, please help, I've posted a thread for my problem and here's the link

[http://ubuntuforums.org/showthread.php?t=2013484](http://ubuntuforums.org/showthread.php?t=2013484)

---

