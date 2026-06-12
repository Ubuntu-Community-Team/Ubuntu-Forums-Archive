---
title: "Boot error, GRUB Error 17"
date: 2006-11-30
forum: Installation &amp; Upgrades
---

### Post by Tyler5690 on 2006-11-30
I just installed Dapper on my desktop. It is dual booting with Windows XP.  The installation went smoothly, and I restarted when it was finished. After the reboot, I got the error 

GRUB Loading stage 1.5.  
GRUB loading, please wait...
Error 17

What can I do so I can boot into my operating system(s)?

---

### Post by Jose Catre-Vandis on 2006-11-30
Here is the definitive dual boot guide
[http://users.bigpond.net.au/hermanzone/](http://users.bigpond.net.au/hermanzone/)

if this doesn't help, you will need to boot up your Ubuntu Live CD, open up a terminal, run grub, identify the correct place to install it, and reinstall. There are many howtos anf posts on this subject on the forum, so please search.

---

### Post by Tyler5690 on 2006-11-30
I have reinstalled GRUB, and everything seems to be okay when I am in the LiveCD.  However, everytime I boot, I get the same error. I looked up the error, and it says it means that GRUB finds my partition, but doesn't recognize the file system.  How do I fix this?

---

### Post by Herman on 2006-11-30
Hello Tyler5690, 
My guess is that maybe your menu.lst file has the wrong partition numbers or hard disk number in the boot entry for your Ubuntu partition in your /boot/grub/menu.lst file.

You can check to see if that's the problem or not, and fix it if it is, by mounting your Ubuntu partition in your LiveCD this way, 
Mount a Ubuntu ext3 or reiserfs filesystem in the Ubuntu 'Desktop' Live/Install CD...........[GO]("http://users.bigpond.net.au/hermanzone/p10.htm#Mounting_Ubuntu_with_Dapper_Desktop_LiveCD")

Try that first, and you need more specific detailed help then please post your output from 'sudo fdisk -lu', along with a copy of the bottom part of your /boot/grub/menu.lst file and someone will be able to offer you more precise help. 
```
sudo fdisk -lu
```If you are feeling excited and impatient to boot your new operating system, or there are urgent things you need to access your old operating system for, you can easily boot both with a [Super Grub Disk]("http://supergrub.forjamari.linex.org/") for now.

Regards, Herman :-D

---

### Post by Tyler5690 on 2006-11-30
Okay, here's what I've got.

Disk /dev/hda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *          63   286406819   143203378+   7  HPFS/NTFS
/dev/hda2       286406820   311436089    12514635   83  Linux
/dev/hda3       311436090   312576704      570307+   5  Extended
/dev/hda5       311436153   312576704      570276   82  Linux swap / Solaris

And

title		Ubuntu, kernel 2.6.15-23-386
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.15-23-386 root=/dev/hda2 ro quiet splash
initrd		/boot/initrd.img-2.6.15-23-386
savedefault
boot

title		Ubuntu, kernel 2.6.15-23-386 (recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.15-23-386 root=/dev/hda2 ro single
initrd		/boot/initrd.img-2.6.15-23-386
boot

title		Ubuntu, memtest86+
root		(hd0,1)
kernel		/boot/memtest86+.bin 
boot

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda1
title		Microsoft Windows XP Professional
root		(hd0,0)
savedefault
makeactive
chainloader	+1

Is all this correct, or is there something I need to change?

---

### Post by Herman on 2006-11-30
>  Is all this correct, or is there something I need to change? That looks all correct to me. 

If you have or can get a [GParted -- LiveCD]("http://gparted.sourceforge.net/livecd.php"), another test would be to boot that and see how your partitions are recognized. Perhaps you have some other kind of a partitioning or filesystem error that doesn't come up in fdisk.  We should  check that. You could use GParted in your Ubuntu Desktop Live/Install  CD equally as well for taking a look at that. Does your Ubuntu partition look healthy or does it come up with a black rectangle instead of colored? Is you hard disk recognized or does it cone up blank? 

What filesystem do you have for your Ubuntu '/' partition? If it is ext2, ext3 or reiserfs it should be okay. If it is some other type you might need to make a special ext2 /boot partition. I can look up more information on using Grub with other Linux filesytems if we need to.

Can you get a grub [Command Line Interface]("http://users.bigpond.net.au/hermanzone/p15.htm#cli") (CLI) by pressing your 'c'  key from where you got the error 17 or not?
If you can get a  grub CLI, them you should be able to  try using the instructions in the rest of that link. If not, then Super Grub Disk can give you a Grub  CLI which might help to find out how Grub sees (or fails to see) you hard disk and partitions.

---

### Post by Tyler5690 on 2006-12-01
In GParted, /dev/hda1 is recognized as NTFS, /dev/hda2 as ext3 (my Ubuntu partion), and /dev/hda3 as extended (a blue box), with /dev/hda5 as linux-swap. I cannot enter into the GRUB CLI at the error screen.

Using Super Grub, I see that on hd0, partition 0 has "Filesystem type unknown, partition type 0x7" and it can not find data for patition 1. When I type "cat (hd0,1)/boot/grub/menu.lst" , I get "Error 18: Selected cylinder exceeds maximum supported by BIOS".

---

### Post by Herman on 2006-12-01
> Using Super Grub, I see that on hd0, partition 0 has "Filesystem type unknown, partition type 0x7" and it can not find data for patition 1. When I type "cat (hd0,1)/boot/grub/menu.lst" , I get "Error 18: Selected cylinder exceeds maximum supported by BIOS". Aha! :D Possibly you have a BIOS with  hard disk drive size limit and a new hard disk that is a little more than the size your BIOS can support.
You might just simply  try resizing your Ubuntu  partition some with   [GParted -- LiveCD]("http://gparted.sourceforge.net/livecd.php"),
if I recall correctly, if it is inside the 140.0 GB is one of the BIOS limits, 80 GB is another one.  I'll have to look those up somewhere to make sure, but reducing the size of the Ubuntu  partition has fixed error 18 problems in the past. 
Make sure LBA is enabled in your BIOS. If LBA is already enabled, try switching to 'normal' mode and see if that helps.
Regards, Herman :D

EDIT: Here's a link I'm looking at right now from the PC Guide, [http://www.pcguide.com/ref/hdd/bios/size.htm](http://www.pcguide.com/ref/hdd/bios/size.htm)
Do you think this might have anything to do with your problem? I'm still reading it more...
Here's what I was looking for, it's the 137 GB barrier, not 140 GB, I was a little bit out, [http://www.pcguide.com/ref/hdd/bios/sizeGB128-c.html](http://www.pcguide.com/ref/hdd/bios/sizeGB128-c.html)
And this is another associated link, read here, [http://www.pcguide.com/ref/hdd/bios/sizeHandling-c.html](http://www.pcguide.com/ref/hdd/bios/sizeHandling-c.html)

It am not 100% sure that this is your problem yet or not, without seme feedback from you, but it seems like a good possibility.

Regards, Herman

---

### Post by Tyler5690 on 2006-12-01
Well, when I had just Windows, I was using a 160 GB drive and a 250 GB drive, both fully recognized and supported in Windows.
EDIT: The Ubuntu partition is only 11 GB.  Windows has nearly 150 GB.  I'm pretty sure it's not a BIOS issue.

---

### Post by Herman on 2006-12-01
> Well, when I had just Windows, I was using a 160 GB drive and a 250 GB drive, both fully recognized and supported in Windows.
EDIT: The Ubuntu partition is only 11 GB.  Windows has nearly 150 GB.  I'm pretty sure it's not a BIOS issue. Okay then, we'll presume it isn't a BIOS issue for now then. 
What happens when you try to boot Ubuntu with Super Grub Disk's Grub? You can use either Super Grub's GUI menu boot methods, 
1) 'English Super Grub Disk'-->'Gnu/Linux'-->'Boot Gnu/Linux' should bring up your Grub menu from your new Ubuntu installation, but it appears in Super Grub Disk colors.
or,
2) 'English Super Grub Disk'-->'Gnu/Linux'-->'Boot Gnu/Linux Directly'-->(select either IDE or SCSI hard disk type), should boot your new Ubuntu installation, via symlinks in the root of your Ubuntu filesystem to your kernel and initrd.img in /boot/grub.

Otherwise, you should be able to boot from CLI mode, with either of these methods, which do pretty near the same as the GUI options, but are entered manually and will give feedback as to what Grub is doing.
****[B]
               [/B]**3) Configfile Boot**..................................................[GO]("http://users.bigpond.net.au/hermanzone/p15.htm#Second_method_configfile_boot")

**4)Direct (kernel) Boot**..........................................[GO]("http://users.bigpond.net.au/hermanzone/p15.htm#First_method:_direct_kernel_boot.")

Remember, we are now using Grub from Super Grub Disk to boot with, so if Ubuntu still can't boot it isn't a problem related to Ubuntu's own Grub , we are bypassing that.

Just try any of those methods you like and see what error messages you get then, and we'll decide what to do next after that. 

Regards, Herman :D
                [B]
               [/B]

---

