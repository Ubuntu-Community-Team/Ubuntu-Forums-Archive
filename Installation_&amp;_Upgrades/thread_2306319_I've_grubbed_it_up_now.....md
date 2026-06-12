---
title: "I've grubbed it up now...."
date: 2015-12-14
forum: Installation &amp; Upgrades
---

### Post by randy31 on 2015-12-14
Alright, I installed Lubuntu on an ext HDD (usb) so i could have a persistence install. Great. Then.. me being me, I also want to be able to boot HBCD via grub or syslinux also. So while I was logged into my USB Linux in ran ```
sudo apt-get install grub2
```
 I was hoping by installing grub2 it would detect my HBCD on my 2nd partition. 
Now... I now realize that i probably did not install grub correctly. 
I then went back and ran ```
sudo apt-get install grub2 /dev/sdg1
```

heres the problem. My portable OS does not boot now... Do I have to wipe it or can i fix grub?  I normally run Mint (..sorry) so i still have access to all the files and a term. 

any ideas on how to get my usb linux back up with out redoing everything? Also.. what else do I need to do to do my dual boot USB thing?

---

### Post by sudodus on 2015-12-14
Welcome to the Ubuntu Forums :-)

Maybe you can have a look at the following links to three posts a tutorial thread about persistent live drives.

Post #6.   [A smaller and simpler pendrive for all PC (Intel/AMD) computers - 'grub-n-iso']("http://ubuntuforums.org/showthread.php?t=2259682&p=13300523#post13300523") - Lubuntu  32-bit

Post #7. [Multiboot pendrive system for all PC (Intel/AMD) computers]("http://ubuntuforums.org/showthread.php?t=2259682&p=13302264#post13302264")

Post #8. [Build your own single boot or multiboot pendrive for all PC (Intel/AMD) computers]("http://ubuntuforums.org/showthread.php?t=2259682&p=13302278#post13302278")

And in Post #8 there are these external links, that might help you include systems, that are not based on Ubuntu.

> D 2. If you download an iso file with another distro,

you need to configure the menuentry in grub.cfg manually. The following links may help

[https://wiki.archlinux.org/index.php/Multiboot_USB_drive](https://wiki.archlinux.org/index.php/Multiboot_USB_drive)

[https://help.ubuntu.com/community/Grub2/ISOBoot](https://help.ubuntu.com/community/Grub2/ISOBoot)

[https://help.ubuntu.com/community/Grub2/ISOBoot/Examples](https://help.ubuntu.com/community/Grub2/ISOBoot/Examples)

[https://help.ubuntu.com/community/Grub2/CustomMenus](https://help.ubuntu.com/community/Grub2/CustomMenus)

---

### Post by yancek on 2015-12-14
If you did a full install of Lubuntu to a usb drive, it already had Grub installed as that is the standard boot loader.
If you installed it to a usb drive as a Live CD with something like unetbootin or pendrivelinux then it is probably using syslinux.
Which did you do?
Where is HBCD?  Which drive, the same as Lubuntu or another?
Installing Grub2 won't detect other operating systems.  You need to run sudo update-grub from Lubuntu with the other systems installed on their own partitions for that to work.

Several methods for reinstalling Grub2 on Ubuntu and derivatives are expalined at the page below.  This will only work if it is an actual install not a Live CD on a flash drive. 
The entry below placed in the grub.cfg file of Lubuntu should work to boot HBCD, worked for me from Ubuntu.  You would need to change the set root line as in the example below it is on the first partition of the first drive. 

> menuentry 'CHAINLOAD HBCD' {
insmod part_msdos
insmod chain
set root=(hd0,1)
chainloader +1
}

---

### Post by oldfred on 2015-12-14
I have used grub to boot just about everything.
And I think Yancek's entry above will actually boot the live installer, since it refers to first partition.
Live installer uses syslinux which is a Windows type boot loader that goes from MBR->PBR->boot. So a chainload into PBR should boot the second part of syslinux.

So not know how HBCD boots.

---

### Post by yancek on 2015-12-14
> And I think Yancek's entry above will actually boot the live installer, since it refers to first partition

I'm not really sure what the OP has, if he did a full install or a Live CD to a flash drive.  The example I posted above boots HBCD which is on the first partition of the flash drive.  I created a second partition with Peppermint Linux on it to boot from.  In most cases, I would expect the Live CD to be on the first partition.

---

### Post by randy31 on 2015-12-16
Thank you for all the replies. After carefully looking over everything, I decided to scrap what I had. Redo all partitions. Installed MiniXp and then install Lubuntu so the install would pick up the Win boot loader. That got me going.. Now I have a dual-boot USB HDD.  :-)

---

