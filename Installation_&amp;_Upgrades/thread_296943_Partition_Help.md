---
title: "Partition Help"
date: 2006-11-10
forum: Installation &amp; Upgrades
---

### Post by j o e l on 2006-11-10
Hello, I am in need of some assistance from this great community. :) 

For various reasons, I have a new HDD (100GB) I'd like to setup with Windows XP and Ubuntu.  I'd also like the availability to test other distros from time-to-time.  What would be the best way to go about this?  Would VMWare, Xen, or something like that be the answer for testing different distros?

What would be an example of a partitiong scheme which would fit this scenario?  I've also read about mounting your /home directory separate to help protect your data in the event of a system failure.  I'm just not sure how this would look in the partition scheme.  Of the four primary partitions, I know Win XP will have one, and I think another is needed for the swap? :confused:

I'm just not very experienced at this, so I'm not sure what is the best scheme for this scenario.  Any help you can give would be greatly appreciated.

Thanks!

joel

---

### Post by ReaderRat on 2006-11-10
To dual boot in Ubuntu: [**Dual-Booting (One HDD)**](http://users.bigpond.net.au/hermanzone/)
Be sure to install Windoze first, or it will overwrite the GRUB menu.As always, **[COLOR="Red"]Back up everything important before messin' with the partitions.[/COLOR]**
Here is a guide on partitioning: [**Partitioning (XP & Ubuntu)**](http://psychocats.net/ubuntu/partitioning)
Good luck with Ubuntu.

---

### Post by bulldog on 2006-11-10
Well your /home and swap can be used for other distro's too,so you need only one of those.

How big should your windows be..........I don't know,you have to decide for that one.

For Ubuntu,
Make a /  (root) partition of about 10GB
Make a swap about 1GB
Make a /home as you desire.

For other distro's to test,
Let some unused space of about 15GB to test other distro's.
Remember you can use your swap and /home with those if you want to.

The rest is for you to decide.
About partitions,you can have only four primary's,but if you make an extended partition you can fill it with logical drives so there is almost no limitation.
Just make your windows primary,your / (root) primary and create an extended partition for swap, /home and the unused space for testing distro's.

---

### Post by dannyboy79 on 2006-11-10
You are going to get tons of different answers, it really boils down to preference. Although most would probably agree about having home on a different partition even maybe a different hdd, then I beleive you can share it with different linux distros (i think, don't quote me)
this is my 20gb HDD
/dev/hdc1 is 50mb
/dev/hdc2 is 10gb             
/dev/hdc3 is 1.5gb (i have 512mb ram)
/dev/hdc4 is 7gb

hdc1= /boot
hdc2= /
hdc3= swap
hdc4= /home

So for you, you would just add some more partitions so that you could some day install linux distro's onto them. You don't really need a boot partition and I can't tell you for sure why I did it, I read it somewhere and there is a reason (maybe not the best reason but I know there is 1) but it escapes me right now. So your first 3 paritions will be primary and then your 4th will be an extended and then you just create as many logical partitions as you want within the extended partition. the live cd installer will help you with this, you'll want to chose manual installation so you can be specific as to what you are going to do, plus you wouldn't want to chose auto and have ubuntu overwrite your winbloz installation. Yeah, you're gonna want to install windows first I know that much. look for a dual booting guide, that'll be your best bet. I have never done it. I thought I would put in my 2 cents here though. Good luck

---

### Post by louieb on 2006-11-10
I have an old 433mhz 256mb e-machine that I use to try diffrent distros.
It has a 40 gig hard drive. hda1 is the boot partition for Ubuntu whch is installed in partition hda2.
hda3 is an extended partition which means it contains partitions hda5 - hda11. 
and hda4 used by all installed distros for their swap partition. 

Here is what the fdisk look like:

```
lou@emach:~$ sudo fdisk -l
Password:

Disk /dev/hda: 41.1 GB, 41110142976 bytes
255 heads, 63 sectors/track, 4998 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1          13      104391   83  Linux
/dev/hda2              14         650     5116702+  83  Linux
/dev/hda3             651        4933    34403197+   5  Extended
/dev/hda4            4934        4998      522112+  82  Linux swap / Solaris
/dev/hda5             651        1288     5124703+  83  Linux
/dev/hda6            1289        1925     5116671   83  Linux
/dev/hda7            1926        2562     5116702   83  Linux
/dev/hda8            2563        3200     5124703+  83  Linux
/dev/hda9            3201        3837     5116671   83  Linux
/dev/hda10           3838        4475     5124703+  83  Linux
/dev/hda11           4476        4933     3678853+  83  Linux

```
What I do when I install a diffrent distro is point its installer to whater partiton I want it in. I let the installer do its thing until it wants to install the boot loader (grub or lilo). 
I skip the installation of the boot loader and manually enter the grub entry in the menu.lst in hda1.
  
Here is what my menu.lst currently looks like. 
```
## ## End Default Options ##

title		Ubuntu, kernel 2.6.15-27-386 (/boot hda1, / hda2)
root		(hd0,0)
kernel		/vmlinuz-2.6.15-27-386 root=/dev/hda2 ro quiet splash
initrd		/initrd.img-2.6.15-27-386
savedefault
boot

title		Ubuntu, kernel 2.6.15-27-386 (recovery mode)
root		(hd0,0)
kernel		/vmlinuz-2.6.15-27-386 root=/dev/hda2 ro single
initrd		/initrd.img-2.6.15-27-386
boot

title		Ubuntu, memtest86+
root		(hd0,0)
kernel		/memtest86+.bin 
boot

### END DEBIAN AUTOMAGIC KERNELS LIST
##
title ZenWalk 2.6.17.11 (on hda5)
      root		(hd0,4)
      kernel /boot/vmlinuz-2.6.17.11 root=/dev/hda5 ro 
      boot
title Puppy Linux (on hda6)
      root (hd0,5)
      kernel /boot/vmlinuz root=/dev/hda6 ro 
      boot
title xUbuntu kernel 2.6.15-27-386 (on hda7)
      root (hd0,6)
      kernel /boot/vmlinuz-2.6.15-27-386 root=/dev/hda7 ro quiet splash
      initrd /boot/initrd.img-2.6.15-27-386
      boot
title Slackware 10.2 kernel 2.4.31 (on hda 8)
      root (hd0,7)
      kernel /boot/vmlinuz-ide-2.4.31 root=/dev/hda8 ro quiet splash
      boot

title=SBM-Boot a CD
               kernel   /memdisk
               initrd   /sbm.bin

```
Each partition is around 5 gig. that is plenty of space for all distros except for maybe Suse or Fedora. 

The last entry is for the Smart Boot Manager. This is one of those machines that will not boot from a Linux CD even after changing the boot order in BIOS. I got tired of putting in the SMB floppy every time I wanted to boot to CD so I installed the SMB programs in hda1 and made a grub entry for it.

---

### Post by j o e l on 2006-11-10
Thank you everyone for your quick replies.  I've setup dual-boot scenarios before, but never more than just one version of linux and one version of windows at a time.  I wasn't sure about how to go about setting up multiple versions of linux.

Thank you for the many links and, louieb, thank you for "attaching" some examples.  I really appreciate everyone's help!

---

### Post by dannyboy79 on 2006-11-11
> **louieb said:**
>  title=SBM-Boot a CD
               kernel   /memdisk
               initrd   /sbm.bin 

The last entry is for the Smart Boot Manager. This is one of those machines that will not boot from a Linux CD even after changing the boot order in BIOS. I got tired of putting in the SMB floppy every time I wanted to boot to CD so I installed the SMB programs in hda1 and made a grub entry for it.

I have a computer that can't boot to a cd as well, what is this smart boot manager all about? could you explian a little or point me to the file I am suppose to download to put on a floppy?? you put that you installed the smb programs in hda1, i think you meant SBM instead of SMB but I think I understand what you meant.

---

### Post by louieb on 2006-11-11
How to make a Smart Boot Manager floppy:

[LIST]
[*]The first thing you need to find and download is a program sbm.bin also sometimes called sbm.img or sbm.dsk It is apparently not being maintained. If you try the SBM homepage  the download link is broken. any way you can get it here for now.
[*][http://slackware.at/data/slackware-current/rootdisks/sbootmgr.dsk](http://slackware.at/data/slackware-current/rootdisks/sbootmgr.dsk)
[*]In linux insert a floppy and at the terminal dd if=sbootmgr.dsk of=/dev/fd0
[*]In windows get a copy of RaWriteWin here
[*][http://www.chrysocome.net/rawwrite](http://www.chrysocome.net/rawwrite)
[*]Just follow the directions on the page
[/LIST]

---

### Post by j o e l on 2006-11-11
Okay, I finally settled on a partitioning scheme and went to work.  But now, I have a new problem.

I used the live CD for Edgy to restructure my partitions.  I noticed for some reason, the Gnome Partition Manager viewed my 100 GB HDD as a +93 GB.  I found that strange, but made my changes.  I basically reformatted the "entire" drive and setup the drive as follows:

hda1 - primary - ntfs (intended for Win XP Pro)
hda2 - primary - ext3 (intended for Ubuntu)
hda3 - extended
logical  hda5 - ext3 (intended for /home)
logical  hda6 - ext3 (intended for /opt)
logical  hda7 - ext3 (intended for testing other flavors of Ubuntu and Linux)
hda4 - primary - linux-swap

What I expected was that this would wipe my HDD clean and allow me to do add Win XP (only needed for work-related stuff), do a fresh install of Edgy, etc.  I threw in my Win XP CD to load that first, knowing Windows always screws up the boot loader, if you don't.  However, when I reboot, the CD spins a few times (like it's being read) and then tries to boot from  a copy of grub from somewhere (I now assume the missing @7 GB?).  Since everything else is wiped, it spits out an "error 17" from grub.

I tried deleting all of the partitions, thinking I would let Win XP use it all, defrag the drive, and then use the live Edgy CD to resize the XP partition, and reset my new partition scheme.  But it was the same result, the Win XP disk would not boot, and instead went to the grub loader again.

I checked the CD on another system, and the CD works fine - the PC booted right up from the CD.  I can get my live Edgy CD to boot just fine on my laptop (the 100 GB HDD I am working on), so I'm not sure what the problem is.

What am I missing that I don't understand?  Can someone kindly explain to me what I need to do next?

Thanks again, in advance.

---

### Post by j o e l on 2006-11-12
Sorry to keep posting, but does anyone have any ideas?  I'm not sure what to do now...

Thanks.

---

