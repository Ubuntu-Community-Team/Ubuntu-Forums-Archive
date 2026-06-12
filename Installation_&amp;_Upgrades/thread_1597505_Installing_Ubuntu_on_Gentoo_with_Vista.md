---
title: "Installing Ubuntu on Gentoo with Vista"
date: 2010-10-15
forum: Installation &amp; Upgrades
---

### Post by dabek63 on 2010-10-15
Hi,
a long time ago i wanted to start an adventure with linux. I have installed Gentoo next to windows vista. Installing gentoo was quite hard, and the only thing i managed is to install it in text mode. It was so awfull that i left it that way for a couple of months. I have created this partitions:

          type     size    used
sda8 | ext3 |  41MB   |  10MB
sda9 | swap | 1028MB | 0MB
sda10 | ext3 | 11655MB  | 2390MB

As farest i know i can't simply format them all, becase i won't be able to start vista installed on my laptop ( there will be no GRUB ).
I have downloaded ubuntu 10.04.1 and installed it. I have formatted sda10 and made it primiary partition, and installed bootlader on sda8.
Still got gentoo GRUB, of course after choosing gentoo it won't start. Vista works fine.

What should i do now to use this partitions and install on them Ubuntu and still have the option to start both vista and ubuntu ?

thanks for any help !

---

### Post by Elfy on 2010-10-15
Choose the advanced/manual partition option. You can then select specific partition to install - mountpoint from the Edit partition / 

swap will get recognised and dealt with 

XP should get added to the new grub2 menu

---

### Post by coffeecat on 2010-10-15
> **forestpiskie said:**
> Choose the advanced/manual partition option.

If I read the OP correctly, they have already installed Ubuntu to sda10, but installed grub stage 1 to the partition boot sector of sda8, which looks like it may be the /boot partition set up by Gentoo.

> **dabek63 said:**
> a long time ago i wanted to start an adventure with linux. I have installed Gentoo next to windows vista.

Well, I salute your spirit of adventure. :-s I used Gentoo for a couple of years, but only after I had used Linux for quite some time.

If you have already installed Ubuntu, you can install Ubuntu's grub2 to the mbr and use that to boot Ubuntu, Vista and Gentoo. Here's a link which tells you how:

[https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202]("https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202")

But first you need to clarify a couple of things. When you say, "Still got gentoo GRUB, of course after choosing gentoo it won't start" do you mean Gentoo won't start, Ubuntu won't start or neither will start?

Boot up with the Ubuntu live-CD (or Ubuntu if you can boot it up on the hard drive), open a terminal and post the output of:

```
sudo fdisk -lu
```Last question: if you followed the Gentoo handbook you would have created a separate /boot partition - which is an unnecessary (in my opinion) complication much beloved of the geekier distros. When (and if) you installed Ubuntu, did you use the /boot partition for that too?

---

### Post by dabek63 on 2010-10-15
Hi,
thanks for replies :)

Gentoo won't start because on it's partition there is Ubuntu now.
Can't start Ubuntu because there is NO option to do so in GRUB ( only Vista nad gentoo ). 

I choosed sda10 for root partition ( primiary ), but i suppose that i have done 
/boot partition ( it was so long ago that i'm not 100% sure :) ) on sda8:

sda8 | ext3 |  41MB   |  10MB

and haven't formatted sda8 and coffecat i haven't chosen it to be /boot partition.

So all i should do is to run live cd and reinstall grub on sda8 ?

what if i would want to reinstall ubuntu one more time and this time i format sda10, made it root and primiary, and also format sda8, made it /boot , next choose to install bootlader on sda8 and as forestpiskie said the swap partition would be recognized.

best regards

---

### Post by coffeecat on 2010-10-15
> **dabek63 said:**
> what if i would want to reinstall ubuntu one more time and this time i format sda10, made it root and primiary, and also format sda8, made it /boot , next choose to install bootlader on sda8 and as forestpiskie said the swap partition would be recognized.

If you want to reinstall Ubuntu, I would suggest having a critical look at your partition layout before doing so. Personally, I would not have a separate boot partition, but that has to be your choice. If sda8 is both your Gentoo and Ubuntu boot partition, that could cause complications, if only because you will have two sets of grub files there: legacy grub for Gentoo and grub2 for Ubuntu.

So - post the output of 'sudo fdisk -lu' as I suggested and tell us whether you want to keep Gentoo or not.

Also - if you install Ubuntu's grub2 to sda8, that means to the partition boot sector of sda8, and that is not a good idea. I've had variable results with trying to install grub2 stage 1 to the partition boot sector - it doesn't seem to be as reliable as with legacy grub. You would be better to install Ubuntu's grub to the MBR and let Ubuntu's grub handle all the booting.

---

### Post by dabek63 on 2010-10-15
> ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x9ac70d2a

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1         192     1536000   27  Unknown
Partition 1 does not end on cylinder boundary.
/dev/sda2   *         192        4856    37468796    7  HPFS/NTFS
/dev/sda3            4857       18040   105900449+   f  W95 Ext'd (LBA)
/dev/sda4           18041       19458    11382784   83  Linux
/dev/sda5            4857       10079    41953716    7  HPFS/NTFS
/dev/sda6           10080       15301    41945683+   7  HPFS/NTFS
/dev/sda7           15302       17910    20956761    7  HPFS/NTFS
/dev/sda8           17911       17915       40131   83  Linux
/dev/sda9           17916       18040     1004031   82  Linux swap / Solaris
My ubuntu is on sda4, sda8 is a boot partition ? and sda9 is swap.

I have made separate boot partition because probobly it was said to do so in gentoo installation guide. Let's say that i want to DELETE all the linux partitions. 

When i delete them, next i create swap partition for example 1024mb , and then a primiary partition for ubuntu with later bootlader installed ?  

i suppose that it will work, but will there be a problem with starting my Vista ?

thanks coffecat for help so far:)

---

### Post by coffeecat on 2010-10-15
If you delete all your Linux partitions, you won't be able to boot Windows until you either:

Install another Linux distro such as Ubuntu and install grub to the mbr.

Or...

Repair the Windows MBR with a Windows install disc/recovery disc or one of the other methods for repairing the Windows MBR.

Before you do anything, let me make a suggestion. Your primary partition sda4 comes after the extended partition sda3 (which contains the logical partitions sda5 to sda9). This is unnecessary. Linux can boot from a logical partition. Unlike Windows it doesn't need a primary partition to boot from. If you were to delete sda4, you could enlarge sda3 to fill the freed space. Then, if you deleted the other Linux partitions sda8 and sda9 you would have all that space as continuous space, which would give you more flexibility and be tidier. You should do all that with Gparted in the live Ubuntu CD. Don't rely on Windows Disk Management which will recognise all your partitions (but not the Linux filesystems) but which doesn't identify primary/extended/logical partitions as such.

I'll have to log off soon, so I may not be able to post again for some hours. In the meantime, why do you have three NTFS partitions, sda5, 6 and 7? If you are rethinking your Linux partitions, you might want to rethink them as well.

---

### Post by dabek63 on 2010-10-15
thanks coffeycat :)

i think that i will delete all linux partitions, and install grub with the link that you gave me.

i will post the results :)

---

### Post by dabek63 on 2010-10-16
yeaa :) i'm on ubuntu now :)
i deleted all linux partitions, and simply installed ubuntu. I was to fast and didn't check the Advanced button and the end of installation where the bootloader is ( but as farest i rember there was selected option to install bootloader on sda [ on all disks ?] ) .

after restarting my computer there was ubuntu ( 4 modes ) and my vista :)
easy and simple :)

thanks for help coffecat, what i should do next to improve my linux skills ?:p

---

### Post by coffeecat on 2010-10-16
> **dabek63 said:**
> i think that i will delete all linux partitions, and install grub with the link that you gave me.

If you're doing a fresh install of Ubuntu from the live CD you don't need the link I posted. The installer will install grub to the mbr for you and will detect Windows and set up a dual-boot menu for you.

---

### Post by dabek63 on 2010-10-16
yea, that's right, everything works fine :)
how can i change the topic to SOLVED ?

---

### Post by dabek63 on 2010-10-16
one additional quick question, for example: i'm using amarok and when i'm closing it -> it should go to system tray, but i can't see it there ? what should i do to see it ?

---

