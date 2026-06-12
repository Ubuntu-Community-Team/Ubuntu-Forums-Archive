---
title: "Grub error 17 Help Please"
date: 2007-05-03
forum: Installation &amp; Upgrades
---

### Post by pizzicar on 2007-05-03
Hope someone is up late :)

Ran the install for 7.04 kbuntu desktop. I have Windows XP on my first drive and created space on my second drive to install kbuntu on. The install seemed to go just fine. On reboot, I get a grub error 17. I have tried reading the forums for help on this but still can't get anywhere. Any help would be appreciated.

Ran the following to try and provide enough info to help

ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 320.0 GB, 320072933376 bytes
240 heads, 63 sectors/track, 41345 cylinders
Units = cylinders of 15120 * 512 = 7741440 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       41345   312568168+   7  HPFS/NTFS

Disk /dev/sdb: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       18142   145718968+   7  HPFS/NTFS
Partition 1 does not end on cylinder boundary.
/dev/sdb2           18143       37697   157075537+  83  Linux
/dev/sdb3           37698       38913     9767520    5  Extended
/dev/sdb5           37698       38913     9767488+  82  Linux swap / Solaris

title           Ubuntu, kernel 2.6.20-15-generic
root            (hd1,1)
kernel          /boot/vmlinuz-2.6.20-15-generic root=UUID=182afdd5-d602-415c-a0e2-3ab19a4e5c42 ro quiet splash
initrd          /boot/initrd.img-2.6.20-15-generic
quiet
savedefault

title           Ubuntu, kernel 2.6.20-15-generic (recovery mode)
root            (hd1,1)
kernel          /boot/vmlinuz-2.6.20-15-generic root=UUID=182afdd5-d602-415c-a0e2-3ab19a4e5c42 ro single
initrd          /boot/initrd.img-2.6.20-15-generic

title           Ubuntu, memtest86+
root            (hd1,1)
kernel          /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title           Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title           Microsoft Windows XP Professional
root            (hd0,0)
savedefault
makeactive
chainloader     +1

---

### Post by pizzicar on 2007-05-03
Just a quick update - I needed to get into xp so I went ahead and did a fixmbr so I could boot the computer (could not boot either OS). Also, this is the second install I have tried - both with grub error 17. Because of the fixmbr, I'll need to reinstall grub I assume. So - two questions then - is there an obvious reason why the error 17...and is there a link for a good step by step guide for installing grub (assuming I'm running from the live CD)?

Thanks

---

### Post by undecidable on 2007-05-03
pizzacar

Nothing I can see obviously wrong.
It is worth checking that the uuids in the fstab match the partitions you are actually trying to boot form.

I think your Linux partition is on /dev/sdb2 so do
  vol_id /dev/sdb2
and check that the uuid is 182afdd5-d602-415c-a0e2-3ab19a4e5c42.

Another thing worth checking is when you get to the grub menu
type 'c' to go to the grub command line and enter
find vmlinuz
to ensure grub can actually find your vmlinuz kernel.
(obviously after you have reinstalled grub)

Another thing to check: if from the Grub menu you select to boot Windows
does it work or still error 17.  

A good page on grub is:
[http://users.bigpond.net.au/hermanzone/p15.htm#Re-install_Grub_with_Live_CD](http://users.bigpond.net.au/hermanzone/p15.htm#Re-install_Grub_with_Live_CD)
and you will see a section titled "Re-install Grub with Live CD".

The man page for grub will also tell you,
though you will need to read it 23 times before you understand what it is trying to tell you.

hope this helps.

---

### Post by pizzicar on 2007-05-03
Good tips and link - thanks. I'll check it out when I get off work today. Part of my problem may be LBA addressing - I think I will try a boot manager from Acronis that works with disk managers. This would require me to install grub to the Linux partition so I'll read the grub link and see if I can re-install it there. I'll let you know how it goes :)

Thanks again

---

### Post by psusi on 2007-05-03
The disk is too large for the bios to address the whole thing, so grub has to be on the lower part of the disk to load.  Reinstall ubuntu but this time make a /boot partition at the start of the disk.  It should be 50-100 megs.

---

### Post by pizzicar on 2007-05-03
psusi,

I don't have my partitioning software in front of me (at work :( ) but if I have a partition already existing on the drive - how would I create a new one in front of it? is this a normal feature of partitioning software. What is the best way to accomplish this?

---

### Post by psusi on 2007-05-03
You can use gparted on the livecd to move and resize partitions, but I don't think it can move the start of an NTFS partition due to certain poor choices Microsoft made in the NTFS boot sector.  If this is the case, and you have an NTFS partition at the start of the drive, then you will need to blow away the windows partition and recreate it after the boot partition, then reinstall windows.

---

### Post by undecidable on 2007-05-03
Are you using a very old bios?
In that case you might find it helpful to know you exactly what the limitation is to know how close to the beginning you need to move things.  This page has excellent info on this problem and some bios solutions:
[http://www.storagereview.com/guide2000/ref/hdd/bios/size.html](http://www.storagereview.com/guide2000/ref/hdd/bios/size.html)
I have never had this problem - even with bios's last updated in 2002.

psusi's solution cuts through all that, and just says put the /boot partition right at the beginning which will also work.
I use partitionmagic, and it can move ntfs partitions (I am not smart enough for gparted).  I can confirm that  NTFS or Windows partitons do not need to be at the start of the disk - I have them everywhere, as long as they are in a primary partition on the 1st disk it is easy.  (Unless of course you were using the MS MBR to boot to ntldr in which case you would have the same bios addressing problem as above. )

wrt boot managers you mentioned above, in fact I prefer an independent boot manager, as if something happens to the particular partition that has grub stage 1 then I can't boot.  
I use XOSL, also open source & GPL, but with a graphical interface for configuration.    It's main code (the equivalent to grub stage 1 & 2 on the Lx partition or NTLdr on the W) can live in a very small fat partitoin inside an extended partition, is independent of any OS and is easily restored from floppy if your disk gets corrupted.   It stopped being developed in 2001, but that is probably all for the better.
It now lives at [http://www2.arnes.si/~fkomar/xosl.org/shots.html](http://www2.arnes.si/~fkomar/xosl.org/shots.html)
and [http://www.ranish.com/](http://www.ranish.com/) as well as a few other places

Though of couse as you are unlikely to have the extended partition at the beginning of the disk, you still need to solve the problem above as you still won't be able to address the fat partition.   Though, if you are not using your full 4 primary partitions, you could make 50mb of space at the beginning of the disk and put a fat primary partiton there.  This would be roughly equivalent to putting a /boot partition at the beginning of the disk.

---

### Post by pizzicar on 2007-05-03
Very helpful guys - thanks. I'm going to take some time to digest the information in the links (my bios is 2001 - ya I know - time for an upgrade :) )

At least I now understand the issue and can spend some learning time figuring out the best solution for my setup.

Edit:  Reading some from the site you provided undecidable - it may make sense to buy a new ide controller - not very expensive and I have an extra hard drive laying around. This would allow me to dedicate a third drive to ubuntu to get around the issues. Any of you used one of these [Promise Controllers]("http://www.newegg.com/Product/Product.aspx?Item=N82E16816102027")

---

### Post by undecidable on 2007-05-03
The simplest solution might be to just flash the bios to a later version.
Takes 10 minutes.
Usually they will be on the manufacturer's site
(unless you built it yourself)

---

### Post by pizzicar on 2007-05-03
That was my first thought - it's an HP 9795c computer - I went to HP's site but the only bios listed is dated 2001 - same date that I have.

---

### Post by MudCrab on 2007-05-04
**pizzicar**,

Since you have Acronis Disk Director, have you booted from the rescue cd and started the *safe mode* version? It uses the BIOS to access the hard drives. If it sees the large drives correctly then I'd think that the BIOS is supporting them.

I do remember that I had to update the BIOS on my Dell 8100 computer to support larger hard drives and it's from late 2000 so I suppose it's possible that's the problem.

Does Windows see both drives correctly?

When you boot from the Live Kubuntu cd, does it show the drives correctly? If it installed in the partition you made for it, then it must have.

---

### Post by finalzero on 2007-05-04
Does grub work if you install Ubuntu 6.10 i.e. your able to reboot and access the menu items?

If so then I recommend doing a clean install of Ubuntu, setup your partitions during the install preserving your Windows partition.  Once its complete reboot as normal and then perform an upgrade to 7.04 from your desktop (instructions in the forum sticky post, you can also wait a few minutes and it should prompt you to upgrade).

Do the upgrade and you should have a working 7.04 system. I am not sure why it works like this but I have a feeling the upgrade sees the existing Grub configuration and decides to keep the drive structure and partition layout.

Hope that helps,

Fz

---

### Post by psusi on 2007-05-04
> **MudCrab said:**
> 
Since you have Acronis Disk Director, have you booted from the rescue cd and started the *safe mode* version? It uses the BIOS to access the hard drives. If it sees the large drives correctly then I'd think that the BIOS is supporting them.

Linux NEVER uses the bios to access the hard disk.  "Safe" or "Rescue" mode usually means single user mode, which tells init not to bother starting up all the normal services like Xwindows and any servers like samba, but rather to just start a root shell.  

> 
When you boot from the Live Kubuntu cd, does it show the drives correctly? If it installed in the partition you made for it, then it must have.

The kernel sees it just fine, the problem is that the bios can't, so grub can't.

---

### Post by pizzicar on 2007-05-04
Thanks all for the advise - I have drive manager software running so windows recognizes the larger drives - and of course windows is booting off the front part of the drive. 

I went ahead and ordered an ATA/IDE controller that supports large drives - it's supposed to work without conflicts with the on-board ide controller and because the card has its own controller SW, it recognizes large drives. I will get it tomorrow and install it and a drive that I have laying around. This will give a whole drive to kbuntu. Based on what I know now, I will also download the alternate CD so I can specify where grub will be written. Or actually, if kbuntu is booting from the new drive - it may be ok that grub writes to the c drive mbr.

---

### Post by pizzicar on 2007-05-07
I wanted to bring closure to this thread so that others who might have similar issues may be able to benefit. I received the IDE card (Promise Ultra133 Tx2) and plugged in a spare hard drive that I had. Once I loaded the drivers and made sure the disk was recognized, I started the install process again. I let the system have the entire new drive and let grub load into the boot drive -- and when the system rebooted, It was golden :)

As I type this in my new kbuntu system, I again want to express my appreciation for all those who helped me in my efforts to get this up and running. Now let the learning begin.....

---

