---
title: "&quot;Boot Error&quot; during startup"
date: 2011-05-17
forum: Installation &amp; Upgrades
---

### Post by h2o4444 on 2011-05-17
Hello,
 I have a 2004 Gateway 702GE desktop and I am currently running Windows XP. Recently the start button won't work properly and it keeps starting up the machine after I shut it down. So I decide to give Ubuntu 11.04 a try to see if it'll solve the problem.
 I've followed the directions on the Ubuntu download website and created a USB stick with Ubuntu on it (I couldn't create a CD because there's something wrong with my DVD burner, it can't read anything... but that's another problem for another day).
 Anyways, now when I boot from the USB stick, I get the BIOS screen first then I get a black screen with the words "Boot Error" at the top. That's the only message I get with no explanation what so ever. I don't get the grub screen because Ubuntu is not installed yet.
 My USB stick is formatted as FAT32.
 I also tried to install Ubuntu within windows using Wubi but I get an error message that says, "Exception Processing Message c0000013 Parameters 75b6bf7c 4 75b6bf7c 75b6bf7c". And this message refuses to go away after I tried to close it or hit either "Cancel", "Try Again", or "Continue".
 Can anyone help me with the "Boot Error" or suggest another way to install Ubuntu?

Thanks in advance.

---

### Post by oldfred on 2011-05-17
How much memory do you have? And a computer that old may not let you boot from a USB port, so it is just trying to boot from Hard drive. You need to use a CD, but may need a lightweight version or even not Ubuntu if you do not have much memory.

[https://help.ubuntu.com/community/Installation/SystemRequirements](https://help.ubuntu.com/community/Installation/SystemRequirements)
[https://help.ubuntu.com/10.10/installation-guide/i386/minimum-hardware-reqts.html](https://help.ubuntu.com/10.10/installation-guide/i386/minimum-hardware-reqts.html)


Light Linux Distros
[http://ubuntuforums.org/showthread.php?t=1582027](http://ubuntuforums.org/showthread.php?t=1582027)
Lighter weight Versions use with Chromium browser as it is lighter than firefox:
Firefox 4, Chromium is much faster than FF3.6.
[http://www.psychocats.net/ubuntu/minimal](http://www.psychocats.net/ubuntu/minimal)
Light Linux Distributions - Hardware Testing (RAM)
[http://ubuntuforums.org/showthread.php?t=1582027](http://ubuntuforums.org/showthread.php?t=1582027)
Lubuntu, which uses the LXDE desktop environment, targeted at "normal computers" with 128 MB
With 512Mb of RAM and almost any processor, Lubuntu will perform more than adequately out-of-the box. 
Xubuntu, a "lightweight" distribution based on the Xfce desktop environment or add LXDE desktop (is not lubuntu)
        with Gnumeric and AbiWord by default
Crunchbang: based on Debian Squeeze (stable).

---

### Post by h2o4444 on 2011-05-17
I have 1 GB of memory and the computer is a Pentium 4 3.2 GHz.

---

### Post by oldfred on 2011-05-17
That's plenty of memory, but it was only about 5 years ago they converted USB ports to bootable and removed floppy drives.

Actually in some cases they removed floppy before they made USB ports bootable, then everyone wondered how to boot. Only CD and Harddrive were choices.

---

### Post by h2o4444 on 2011-05-17
Well, I just reinstalled XP on the computer and see if that'll help. The computer still has the shutdown problem. I hope I get Ubuntu to install right then maybe the shutdown problem will disappear in Ubuntu.

---

### Post by h2o4444 on 2011-05-17
I can't seem to get Ubuntu to work on my machine. I guess this problem will left unsolved.

---

### Post by h2o4444 on 2011-05-18
Got Ubuntu to install by using an external DVD drive with 11.04 CD. Told BIOS to boot from USB and it worked. Somehow my other Ubuntu CDs didn't work but the 11.04 copy did. The shutdown problem is solved in Ubuntu but since I dual boot with XP, XP still has the shutdown problem. I'm guessing it must be a software problem on Windows part. Case closed.

---

### Post by Dutch70 on 2011-05-18
Glad to hear you got it worked out. I agree it must be a problem with XP if Ubuntu is shutting down properly. 

If you're satisfied that this thread is solved, please mark it "solved" with "Thread Tools" at the top of the page. :)

---

