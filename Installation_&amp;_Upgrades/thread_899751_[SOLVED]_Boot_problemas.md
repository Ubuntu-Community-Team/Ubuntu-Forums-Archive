---
title: "[SOLVED] Boot problemas"
date: 2008-08-24
forum: Installation &amp; Upgrades
---

### Post by Alabamian on 2008-08-24
Wow, I've really messed things up.  I have a system with two HD's, one IDE for data-only (NTFS) and one SATA that used to only have Vista, but now has Ubuntu 8.0.4.1 and Vista.  After I installed Ubuntu, the Vista Boot Loader ignored it completely (surprise).  I could get GRUB to come up only if I went into my Boot sequence controller from the BIOS on my Compaq CPU.  I decided to try out EasyBCD but that turned out to be a disaster, so I told it to just delete the MBR and I'd try out everything with GRUB.  Now I can't get anything to work.  I've successfully managed to re-install GRUB, but nothing works on the menu.  All my Linux installations give me ...

Error 22:  No such partition

Press any key to continue

On the other hand, my Vista now just hangs when I select it.  I get ...

Starting up ...

and there it sits till I finally reboot.

Here's what I've got so far.  When I boot from the InstallCD, with sudo fdisk -l I get ...

ubuntu@ubuntu:/dev/disk$ sudo fdisk -l

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x04b0f99c

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       19457   156288321    7  HPFS/NTFS

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xcab10bee

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        9025    72493281    7  HPFS/NTFS
/dev/sdb2           18339       19457     8981280    c  W95 FAT32 (LBA)
Partition 2 does not end on cylinder boundary.
/dev/sdb3            9026       18338    74806672+   5  Extended
/dev/sdb5            9026       17954    71722161   83  Linux
/dev/sdb6           17955       18338     3084448+  82  Linux swap / Solaris

Partition table entries are not in disk order

Disk /dev/sdc: 4047 MB, 4047502848 bytes
4 heads, 32 sectors/track, 61759 cylinders
Units = cylinders of 128 * 512 = 65536 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1       61760     3952623+   b  W95 FAT32
ubuntu@ubuntu:/dev/disk$ 


BTW, just for grins, I thought I'd see what the system thinks before I actually mount anything, and so I issued this ...

ubuntu@ubuntu:/dev/disk/by-path$ ls
pci-0000:00:0b.1-usb-0:2.1:1.0-scsi-0:0:0:0
pci-0000:00:0b.1-usb-0:2.1:1.0-scsi-0:0:0:0-part1
pci-0000:00:0d.0-scsi-1:0:0:0
pci-0000:00:0d.0-scsi-1:0:1:0
pci-0000:00:0d.0-scsi-1:0:1:0-part1
pci-0000:00:0e.0-scsi-0:0:0:0
pci-0000:00:0e.0-scsi-0:0:0:0-part1
pci-0000:00:0e.0-scsi-0:0:0:0-part2
pci-0000:00:0e.0-scsi-0:0:0:0-part3
pci-0000:00:0e.0-scsi-0:0:0:0-part5
pci-0000:00:0e.0-scsi-0:0:0:0-part6
ubuntu@ubuntu:/dev/disk/by-path$ 

The pertinent portions of my GRUB menu.lst file (sans #'s) are this:

title		Ubuntu 8.04.1, kernel 2.6.24-20-generic
root		(hd1,5)
kernel		/boot/vmlinuz-2.6.24-20-generic root=UUID=36bc1771-2b7b-4b37-bb9d-aa478f39d397 ro quiet splash
initrd		/boot/initrd.img-2.6.24-20-generic
quiet

title		Ubuntu 8.04.1, kernel 2.6.24-20-generic (recovery mode)
root		(hd1,5)
kernel		/boot/vmlinuz-2.6.24-20-generic root=UUID=36bc1771-2b7b-4b37-bb9d-aa478f39d397 ro single
initrd		/boot/initrd.img-2.6.24-20-generic

title		Ubuntu 8.04.1, kernel 2.6.24-19-generic
root		(hd1,5)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=36bc1771-2b7b-4b37-bb9d-aa478f39d397 ro quiet splash
initrd		/boot/initrd.img-2.6.24-19-generic
quiet

title		Ubuntu 8.04.1, kernel 2.6.24-19-generic (recovery mode)
root		(hd1,5)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=36bc1771-2b7b-4b37-bb9d-aa478f39d397 ro single
initrd		/boot/initrd.img-2.6.24-19-generic

title		Ubuntu 8.04.1, memtest86+
root		(hd1,5)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdb1
title		Windows Vista/Longhorn (loader)
root		(hd1,0)
savedefault
makeactive
chainloader	+1


Please be aware that I've already tried 'e' editing my menu.lst and changing the partitions of my Linux install -- (hd1,2) (hd1,3) (hd1,4) & (hd1,5) all still produce Error 22.

Okay ye Linux brain surgeons, I'm clearly in need of some help, and yes, my brain is rather weary.

---

### Post by SkonesMickLoud on 2008-08-24
By deleting your MBR you also deleted your partition table.  Simply put, GRUB doesn't know where anything is.

Boot into your Ubuntu Live CD and install testdisk:

```
sudo aptitude install testdisk
```

Then run it:

```
sudo testdisk
```

Then just follow the prompts to have it rebuild your partition table.

---

### Post by caljohnsmith on 2008-08-24
If fdisk can still see your partitions fine, and Grub still loads on startup, then I don't think your HDD's partition table was completely deleted; thus I don't think testdisk is necessary at this point.

If you are booting off your Vista + Ubuntu HDD, then all your Ubuntu entries in menu.lst should be (hd0,4) and not (hd1,X), since Ubuntu is on the boot HDD, not the second HDD. Try that and let me know if it works.

---

### Post by Alabamian on 2008-08-24
California John, it worked!  You were absolutely right!  I just changed all my Linux entries to (hd0,4) and now I'm writing this post from Firefox on my own CPU (as opposed to my wife's XP laptop like I had to start this thread with).  Muchas gracias, amigo!

Everything's better, Linux-wise, now.  Unfortunately, I didn't have near as much luck with Vista.  I changed it to (hd0,0) but it still says 

Starting up ...

and hangs.  I realize this is NOT a Vista forum, but any advice is appreciated.  John, you have indeed proven your Linux brain surgeon credentials.  If anyone has comparable dual-boot to Vista operable abilities, that'd be great.

---

### Post by caljohnsmith on 2008-08-25
> **Alabamian]California John, it worked! You were absolutely right! I just changed all my Linux entries to (hd0,4) and now I'm writing this post from Firefox on my own CPU (as opposed to my wife's XP laptop like I had to start this thread with). Muchas gracias, amigo![/quote]
De nada, amigo. :) I'm glad at least Ubuntu is working at this point.
[QUOTE=Alabamian said:**
> Unfortunately, I didn't have near as much luck with Vista.  I changed it to (hd0,0) but it still says 

Starting up ...

and hangs.  I realize this is NOT a Vista forum, but any advice is appreciated.
I believe (hd0,0) should be correct as you tried, Alabamian; but since that doesn't work, I'm wondering, did you use Vista to repartition your HDD to make room for Ubuntu, or did you use Ubuntu's partition editor gparted? If you use anything other than Vista to repartition your HDD, I've heard it can cause problems because Vista will not recognize the newly repartitioned structure.

If I remember correctly, the solution to your problem might be as simple as booting your Vista Recovery CD, and running the following command:
```
bootrec /rebuildbcd
```
That will rebuild Vista's partition table. If you don't have a Vista Recovery CD, you can download one from [this website]("http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/"). Good luck and let me know how it goes. :)

---

### Post by Alabamian on 2008-08-27
California John,

Thanks for the advice, but I figured it out in a less technical, but effective way.  First, thanks again for all your previous advice -- worked like a charm.  Actually, what you write above was right as well in my case, but I fixed things in a simpler, more stubborn way.

I had booted from my Vista disk and run the "Repair Installation" option.  Every time, I got a message that the BootClusterSumpinortheother was messed up.  Vista gave me a clue, though, when I first started down this road with the statement I might need to run it a few times.  Try five times over two different nights.  I was about at my wit's end, ready to re-format and install XP when it finally gave me the message that it had worked.  It also told me Vista was installed on D:  That's weird, D:  But that's what it said.

I tried rebooting but it hung again.  Then, I had the presence of mind to just try it one more time, but this time I 'e' edited it at GRUB and told it to use (hd1,0).  Sure enough, the sucker worked!  Yee haw!  Now I've got BOTH Vista AND Ubuntu 8.0.4.1 working fine.  I do NOT use EasyBCD, only GRUB, and after my experiences with it, I HIGHLY recommend avoiding EasyBCD and just sticking with tried and true GRUB.  I admit it's not as flashy as the Vista Bootloader, but I'll take functionality over functionless form anyday.

So, California John, your observations about gparted are correct.  That's all I used and it made Vista think it was on the D: drive.  Of course, these are just two different partitions on the SAME physical drive, but it can't be too much of a surprise to people that gparted and Vista look at partions from a different *vista*, ha!  Therefore, what is hd0 for Ubuntu is hd1 for Vista.  That's Microsoft for you, and it's crazy.  But that's okay, cause GRUB just told Vista to go ahead and boot from the D: drive and Vista submitted.  Sometimes you just get lucky.  Thanks again!

---

