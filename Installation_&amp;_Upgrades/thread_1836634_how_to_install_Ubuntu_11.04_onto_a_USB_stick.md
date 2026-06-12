---
title: "how to install Ubuntu 11.04 onto a USB stick"
date: 2011-08-31
forum: Installation &amp; Upgrades
---

### Post by Dracona on 2011-08-31
hello, I am wanting to install ubuntu 11.04 onto a usb stick, not as a live cd, but actualy install it.
            I am currently running Ubuntu 11.04 on my desktop dual booting with win 7.
I have a 8 gig ScanDisk usb stick that I hopefully will be installing Ubuntu onto.
Once i get Ubuntu 11.04 installed onto it, i am wanting to add ubuntu rescue remix on it as well.
            I am hoping by doing this, i can us the rescue remix from a gui, instead of the command line interface. I really suck at command line if i don't have something like a gui to help me along the way.
            I hope I have gave enough info, and haven't confused anyone.
i will be happy to answer any questions you have, and supply any information that is needed that i did not supply in this post.

                                                      Thank You 

                                                      Dracona

---

### Post by Dracona on 2011-08-31
I forgot to add this, I also will want to install the nvidia video drivers to the ubuntu usb installation.

---

### Post by OakRaider4Life on 2011-08-31
I couldn't really help you with doing anything like adding Nvidia drivers to your live USB or trying to put 2 OS's onto USB, but UNetBootin is a great GUI tool for making a live USB using a distribution iso. Also, depending on what version of Ubuntu you're running, you may already have the tool startup disk creator which can also create bootable USBs.

---

### Post by oldfred on 2011-08-31
If your USB flash drive is 8GB or more, it is just like any install to a second drive. You want to use manual install or Something Else in 11.04 so you can choose to install grub2's boot loader to the MBR of the flash drive. With flash you also want to change a few settings to reduce writes as flash is slower and USB is slower. But full install is functional, just not speedy.

It does not have to be encrypted BIOS based system:
Standard full install with screenshots to flash or SSD:
Ubuntu Encrypted Flash Memory  Installation
[http://members.iinet.net/~herman546/p19.html](http://members.iinet.net/~herman546/p19.html)
More discussion Dec 2010, more SSD info
[http://ubuntuforums.org/showthread.php?t=1643591](http://ubuntuforums.org/showthread.php?t=1643591)
[http://ubuntuforums.org/showthread.php?t=1404664](http://ubuntuforums.org/showthread.php?t=1404664)

HOW TO Avoid Wubi & Install Ubuntu on USB Drive -amjjawad
[http://ubuntuforums.org/showthread.php?t=1650699](http://ubuntuforums.org/showthread.php?t=1650699)

See post #19 C.S.Cameron - recommends disconnection sda so grub can only install to flash drive.
Maverick now only gives combo box on grub location if you use manual install.
Lucid:
[http://ubuntuforums.org/showthread.php?t=1509603](http://ubuntuforums.org/showthread.php?t=1509603)
Step by Step Full install 8GB C.S.Cameron Post #7
[http://ubuntuforums.org/showthread.php?t=1719346](http://ubuntuforums.org/showthread.php?t=1719346)

Use ext2 or ext4 without journal:
tune2fs -O ^has_journal /dev/sda1
No swap or set swapiness or install 'Dynamic Swap Space Manager' from the Ubuntu Software Center
After installing, change the fstab so that everything gets mounted with noatime.
change to noop i/o scheduler
You want journal to speed up system recovery if you have to do repairs or run fsck. But if partition is small then it does not take long to fsck anyway and without journal writing is reduced.
SSD’s, Journaling, and noatime/relatime 
[http://thunk.org/tytso/blog/2009/03/01/ssds-journaling-and-noatimerelatime/](http://thunk.org/tytso/blog/2009/03/01/ssds-journaling-and-noatimerelatime/)
noatime,nodiratime options in fstab to make the ssd last longer when using a ext4 partition

---

### Post by Dracona on 2011-08-31
**_OldFred_** Thank you so much. this is what i was looking for.

---

