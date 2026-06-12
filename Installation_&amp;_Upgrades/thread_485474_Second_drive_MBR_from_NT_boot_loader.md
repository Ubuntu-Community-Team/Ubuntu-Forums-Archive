---
title: "Second drive MBR from NT boot loader?"
date: 2007-06-26
forum: Installation &amp; Upgrades
---

### Post by mattrees on 2007-06-26
I just finished installing Feisty on a second hard drive on my XP pc.  It did not go smoothly, though.  When I finally got it to work, I used the alternate CD and I had disconnected the XP drive completely.  Grub installed to the MBR of the Ubuntu drive.  So at the moment to switch systems I have to connect or disconnect the Ubuntu drive, or change the boot order in the BIOS.

I'd like to leave my XP drive as the first drive to boot, and I don't want to mess with the MBR on that drive.  Is there any way to just add an Ubuntu option to the XP boot loader and get it to go to the MBR of the second drive?  This seems like it should be simple enough, but I can't find any references to anybody doing this.

-Matt

---

### Post by confused57 on 2007-06-26
> **mattrees said:**
> I just finished installing Feisty on a second hard drive on my XP pc.  It did not go smoothly, though.  When I finally got it to work, I used the alternate CD and I had disconnected the XP drive completely.  Grub installed to the MBR of the Ubuntu drive.  So at the moment to switch systems I have to connect or disconnect the Ubuntu drive, or change the boot order in the BIOS.

I'd like to leave my XP drive as the first drive to boot, and I don't want to mess with the MBR on that drive.  Is there any way to just add an Ubuntu option to the XP boot loader and get it to go to the MBR of the second drive?  This seems like it should be simple enough, but I can't find any references to anybody doing this.

-Matt
It would be much easier to set your system up to boot first to your Ubuntu drive, add an entry to boot Windows to your /boot/grub/menu.lst, the entry in this thread should work:
[http://ubuntuforums.org/showthread.php?t=179902](http://ubuntuforums.org/showthread.php?t=179902)

If your Windows is on the 2nd partition, the root would be (hd1,1)...you can determine the location of your Windows partition by opening a terminal(Applications---Accessories---Terminal), enter:
```
sudo fdisk -l
```
-l is a small "L"

---

### Post by mattrees on 2007-06-28
Thanks for the help, confused57.  I knew setting my linux hard drive as the master would be an option, but I also thought the NT loader MUST be capable of referring to another MBR!  I guess maybe not.

I did exactly as you described and now everything seems to be working.  Thanks again.

---

### Post by confused57 on 2007-06-28
> **mattrees said:**
> Thanks for the help, confused57.  I knew setting my linux hard drive as the master would be an option, but I also thought the NT loader MUST be capable of referring to another MBR!  I guess maybe not.

I did exactly as you described and now everything seems to be working.  Thanks again.
Glad it worked...yes, the NT loader can boot linux, but grub has to be installed to the root partition, there's several howto's in the forum for doing this, although I've never tried it myself.

---

