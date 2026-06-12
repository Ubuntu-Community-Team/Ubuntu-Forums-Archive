---
title: "Problem loading windows 7 loader with GRUB 2"
date: 2009-11-22
forum: Installation &amp; Upgrades
---

### Post by nscott1989 on 2009-11-22
Hello,

I recently installed GRUB 2 on my laptop which is triple booted with Ubuntu 9.10, Windows XP, and Windows 7 all on one hard drive. During the installation, GRUB 2 detected the linux kernels as well as the Windows 7 loader which allows me to then choose between Windows 7 and XP. However, when I select the Windows 7 loader, the screen goes blank except for the word "GRUB" with a blinking cursor. I have read many threads on adding Windows 7 to the boot menu, but none address this specific problem. Does anyone know how to fix this problem?

Also, I am extremely new to Linux and do not know many of the commands.

**Contents of fdisk -l:**
### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda1)" {
    insmod ntfs
    set root=(hd0,1)
    search --no-floppy --fs-uuid --set 78a461afa4617094
    chainloader +1
}
### END /etc/grub.d/30_os-prober ###

**Related contents of grub.cfg:**
### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda1)" {
    insmod ntfs
    set root=(hd0,1)
    search --no-floppy --fs-uuid --set 78a461afa4617094
    chainloader +1
}
### END /etc/grub.d/30_os-prober ###

Any help would be appreciated. Thank You.

-Nathan

---

### Post by oldfred on 2009-11-22
I would try rerunning the osprober by:

sudo update-grub

It may be that it is seeing the XP install even though the win7 install has the windows boot or vice-versa. All the windows boot files are in only one of the windows partitions.

Vista (and Win7) copies boot manager to one 
[http://members.iinet.net/~herman546/p15.html#BOOTMGR_is_missing](http://members.iinet.net/~herman546/p15.html#BOOTMGR_is_missing)
Moral of the story - look on other NTFS partitions for the missing bootmgr and Boot directory.

---

### Post by nscott1989 on 2009-11-22
Ok, I tried booting to the second partition, which is my Windows 7 partition by creating the file "11_Windows" in /etc/grub.d. The result in the grub.cfg gile was:

### BEGIN /etc/grub.d/11_Windows ###
menuentry “Windows&#8243; {
set root=(hd0,2)
chainloader +1
}
### END /etc/grub.d/11_Windows ###

When I selected this new entry in the menu I got the error: NTLDR missing.
I thought this meant that the files for booting are not found, so I tried running the Windows 7 disk to restore the system, but no problem was detected. I suppose the next thing to try would be running the Windows XP disk and trying to recover the boot files since XP is on my first partition.

---

### Post by oldfred on 2009-11-23
Then windows combined its boot loader into the XP partition. I do not know if this would work on a repair but it does on an install.

Try setting boot flag on the windows 7 partition and then run the repair from the win7 install disk.

restore boot loaders Ubuntu Win xp Vista
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)

To get each MS to have its own boot loader make a partition and set its boot flag on, then install the 2nd product in it. Multibooters, Pictures here worth 1000+ words
[http://www.multibooters.co.uk/multiboot.html](http://www.multibooters.co.uk/multiboot.html)
A user who installed two windows & it worked to boot from grub directly
[http://ubuntuforums.org/showthread.php?t=1271600](http://ubuntuforums.org/showthread.php?t=1271600)

If your PC did not come with a complete Vista or Win7 installation CD, you can download a Recovery/Repair Disc (only for repairs) at the following links:
Windows Vista Recovery Disc 
[http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/](http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/)
[http://neosmart.net/blog/2009/windows-7-system-repair-discs/](http://neosmart.net/blog/2009/windows-7-system-repair-discs/)
Vista will not repair XP(they create the boot sectors differently)
[http://neosmart.net/blog/2009/windows-7-system-repair-discs/](http://neosmart.net/blog/2009/windows-7-system-repair-discs/)

---

### Post by nscott1989 on 2009-11-23
I changed the boot flag to the Windows 7 partition and ran the Windows 7 recovery disk(had to run it a few times to fix all errors). I then got to a Linux terminal and ran "sudo update-grub" which detected my second partition as Windows 7. This new menu entry now loads Windows 7. I still do not have access to XP, but I will have to fix it at a later time. I just needed one Windows OS to be running for now.

I have not yet read the articles on multibooting so when I have a chance, I will try to recover XP and post the results.

Thank you for the quick and helpful replies.

---

### Post by wilee-nilee on 2009-11-23
If W7 was a upgrade for XP your not supposed to use XP anyway after W7 verification is this the case? This sounds like W7 install from XP if XP has the W7 boot in it.

---

### Post by nscott1989 on 2009-11-23
No, I did a full install of Windows 7 on a separate partition. I was too skeptical of a new Windows OS to wipe out XP which runs perfectly fine.

---

### Post by phillw on 2009-11-23
Hi,

The How-Tos for reinstalling Grub legacy & Grub2 are lurking this way ---> [http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)

For other things Grub2, drs has both a wiki and Grub2 stuff over here -->  [http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)  [http://ubuntuforums.org/showthread.php?t=818177](http://ubuntuforums.org/showthread.php?t=818177) and various other places ... Find a thread that is active, with his name in it & he'll be along to sort out anything you cannot fathom out from the how-to's currently posted. The HowTo's are still being written, so each new scenario is checked and the howto's will be amended as time goes by.

He's a real nice guy, as well :D

Regards,

Phill.

---

