---
title: "Partitions on new HD for Ubuntu and others"
date: 2006-03-29
forum: Installation &amp; Upgrades
---

### Post by Ichido on 2006-03-29
I have purchased a new 2nd, 40 GB hard drive which I want to partition  in order to have 3 to 4 other GNU/Linux OSes to expirement with.
My first hard drive has Linspire installed, which I don't want to 'screw up', for now. ;-)
Searching Posts only talk about M$ Windo$ :confused: 
Can I make my second drive into hdb0, hdb1, hdb2 & hdb3?
Will Ubuntu be able to install and run in hdb0 using a 10GB partition?
Does Ubuntu prefer ext3?
Does Ubuntu need a separate partition for a 'swap file'?
I purchased the 'Live CD' of Kubuntu 5.10 from [www.linuxcd.org](www.linuxcd.org), but it doesn't install.
It keeps freezing at: "retrieving dhcp-client-udeb 16%" and "enter preinstalled session" and both problems then give the Error: "CD-ROM integrity Failed!"
I have tried other 'Live CD's which all work, execpt Kubuntu. :-(
Your Ubuntu 5.10 Live does install and runs Great.
Why? What is the difference between Kubuntu & Ubuntu?
ANY help is welcomed, Thanks!

---

### Post by Stealth on 2006-03-29
> Can I make my second drive into hdb0, hdb1, hdb2 & hdb3?

Yes, or atleast, you can make 4 partitions. Don't know if they'll be named that exactly ;)

> Will Ubuntu be able to install and run in hdb0 using a 10GB partition?

Sure! :)

> Does Ubuntu prefer ext3?
Well, it defaults to it on install, but you can choose Reiser or some other if you'd prefer.

> Does Ubuntu need a separate partition for a 'swap file'?

Maybe someone can correct me on this, but I'm sure I've had multiple distros use the same swap space without problems...

> What is the difference between Kubuntu & Ubuntu?
Ubuntu uses Gnome, Kubuntu uses KDE. To install kubuntu (without Gnome) you can do a server install with your Ubuntu CD, and then in the terminal do a:
```
sudo apt-get install kubuntu-desktop
```

And it'll be just as if you installed it with a Kubuntu CD :)

---

### Post by Ichido on 2006-03-29
Thanks for your help.
I hope to receive the new drive in a couple of days, so I'm 'gett'n smarts' before I attempt anything.
Do I understand you correctly that I will need at least one swap file on the new drive for all distros to use?

PS. does this Forum have a spell'n checkker? :)

Does the swap file(s) need their own partition?

---

### Post by greenstar on 2006-04-06
Ichido,

If you're still watching this thread, here are the answers to your questions.

> Do I understand you correctly that I will need at least one swap file on the new drive for all distros to use?

You can share a single swap among multipe distros without any problem (in my experience). If you have lots of RAM (1GB+), you will be fine without a swap partition. (some say that your box will run faster without a swap if you have a gig or more RAM)
I have 1GB of RAM and no swap partition. I don't know yet if it's faster, but I get to use more of my disk space.

> Does the swap file(s) need their own partition?

Linux doesn't use a swap file in the windows sense (where the swap or paging file is a file that can be located on pretty much any disk or partition available to windows), but rather uses a separate partition formatted as linux swap. When I need to use a swap partition, I usually make it 512 MB and I usually make it the 1st or 2nd partition on a disk. Your mileage may vary on that last part.

> PS. does this Forum have a spell'n checkker?

Not to my knowledge. I've looked around the interface and haven't seen one, anyway.

Hope this helps you.
Greenstar

---

### Post by Ichido on 2006-04-06
Thanks for the reply,
I am very busy so sometimes it's days or weeks before I get a chance to check for posts.
I have a 512mb and a 256mb chip for RAM.
My system shows it as 725.51MB of RAM?!?
256 + 512 = 768MB !?
The hard drive will be the second drive, 'hdb'.
So hdb1 is Linux Swap? ext3? 
You say 1 GB for Linux Swap?
hdb2 - Ubuntu
hdb3 - Knoppix
hdb4 - Gentoo

Do I have the right idea?
Can I partition hdb from Linspire or do I need to use a LIVE-CD?
Which partitioning program do you recommend?
Sorry for so many question :-)

---

### Post by johnpipe on 2006-04-06
Hi Ichido,

[Ichido wrote]

<SNIP>
> The hard drive will be the second drive, 'hdb'.
> So hdb1 is Linux Swap? ext3? 
> You say 1 GB for Linux Swap?
> hdb2 - Ubuntu
> hdb3 - Knoppix
> hdb4 - Gentoo

> Do I have the right idea?

I don't think that's quite right. Swap is of course up to you, but I suspect 1GB of HD swap may be excessive, I've got about 512MB; I mave have used mkswap to create it, it's been so many years ago I don't remember for sure.

Note, tab-spacing in the files doesn't always show in the posting online, I see this in the fstab listing when previewing this post.

Here is how I've got mutltiple partitions on my box, from dmesg:

linus:/u2/home2/johnpipe$ dmesg | grep hda
    ide0: BM-DMA at 0xe000-0xe007, BIOS settings: hda:DMA, hdb:DMA
hda: FUJITSU MPE3084AE, ATA DISK drive
hda: FUJITSU MPE3084AE, 8063MB w/512kB Cache, CHS=1027/255/63
 hda: hda1 hda2 < hda5 hda6 hda7 hda8 hda9 hda10 > hda3 hda4

linus:/u2/home2/johnpipe$ dmesg | grep hdb
    ide0: BM-DMA at 0xe000-0xe007, BIOS settings: hda:DMA, hdb:DMA
hdb: WDC WD800JB-00JJA0, ATA DISK drive
hdb: WDC WD800JB-00JJA0, 76319MB w/8192kB Cache, CHS=9729/255/63
 hdb: hdb1 < hdb5 hdb6 hdb7 hdb8 hdb9 >

Note that hda1, hda2 and hdb1 are primary partitions (IIRC it's a maximum of 4 primary partitions that can be created), and the linux installations are on the logical partitions (hda5 or hdb5, and greater); hda1 is the original win95 install which I keep for running dos AutoCad 10.

I probably used cfdisk to do the partitioning of my secondary disk; it holds, as you can see by my redhat fstab below, all the other distributions (ubuntu isn't listed there as it's ext3 which is not supported by the 2.2 redhat kernel and therefore it's partition cannot be mounted under redhat 6.1).

Here is fstab; since my original install is on hda, swap is assigned to hda6, and all installs use this swap.

linus:~$ less /etc/fstab 
/dev/hda9               /               ext2            defaults        1 1
/dev/hda4               /mnt/acad_10    vfat            noauto,owner,ro 0 0
/dev/hda10              /boot           ext2            defaults        1 2
/dev/hda8               /home           ext2            defaults        1 2
/dev/scd1               /mnt/cdrw       iso9660         noauto,user,ro  0 0
/dev/scd0               /mnt/cdrom      iso9660         noauto,user,ro  0 0
/dev/hdb5               /u2             ext2            defaults        1 2
/dev/hda5               /usr            ext2            defaults        1 2
/dev/hda7               /var            ext2            defaults        1 2
/dev/hda3               /win95_2        auto            noauto,owner,ro 0 0
/dev/hda1               /win95          auto            noauto,owner,ro 0 0
/dev/hdb6               /mnt/woody      ext2            noauto,owner,ro 0 0
/dev/hdb8               /mnt/suse71     ext2            noauto,owner,ro 0 0
/dev/hda6               swap            swap            defaults        0 0
/dev/fd0                /mnt/floppy     auto            noauto,user     0 0
none                    /proc           proc            defaults        0 0
none                    /proc/bus/usb   usbdevf s        defaults        0 0
none                    /dev/pts        devpts          gid=5,mode=620  0 0  

Note, I run lilo from redhat to set up boot; I have a copy of the ubuntu /boot/ dir installed on the redhat partition and edit /etc/lilo.conf there.  my redhat / has a dir lilo/ with dirs for suse, mandrake, debian woody, and ubuntu, each having a copy of their respective boot dirs, for example:

linus:/u2/home2/johnpipe$ ll /lilo/
total 16
drwxrwxr-x   3 root     root         4096 Mar 30  2005 mdk82
drwxr-xr-x   3 root     root         4096 Apr 13  2005 suse
drwxr-xr-x   3 root     root         4096 Apr 11  2005 ubuntu
drwxrwxr-x   3 root     root         4096 Mar 30  2005 woody
linus:/u2/home2/johnpipe$
linus:/u2/home2/johnpipe$ ll -d /lilo/ubuntu/boot
drwxr-xr-x   2 root     root         4096 Apr  6 03:53 /lilo/ubuntu/boot
linus:/u2/home2/johnpipe$ 

Here is the /etc/lilo.conf entry for ubuntu under this setup (i.e., managing all boot configuration with lilo under redhat):

image=/lilo/ubuntu/boot/vmlinuz-2.6.10-5-386
        label=ubuntu
        initrd=/lilo/ubuntu/boot/initrd.img-2.6.10-5-386
        read-only
        root=/dev/hdb9
        append=irqpoll # workaround for 2.10 kernel bug that disables IRQ10 used by (eth0).


I had my redhat root partition mounted on /mnt/rh_slash under ubuntu, then cd'd to /mnt/rh_shash/lilo/unbut/boot/, and used "cp -a /boot/" to copy the ubuntu boot directory contents.

HTH,  johnpipe

---

### Post by johnpipe on 2006-04-06
Hi, I did a search (I'm 61 now and my ability to remember all the technicalities is not as good as it once was!) on swap size, and came to the partition HOWTO:

     [http://tldp.org/HOWTO/Partition/](http://tldp.org/HOWTO/Partition/)

and here is the section on swap size:

     [http://tldp.org/HOWTO/Partition/requirements.html#SwapSize](http://tldp.org/HOWTO/Partition/requirements.html#SwapSize)


You will find this HOWTO very helpful. There are many other useful HOWTOs  on that site as well.

HTH, johnpipe

---

### Post by greenstar on 2006-04-10
Ichido,

> The hard drive will be the second drive, 'hdb'.
So hdb1 is Linux Swap? ext3? 
You say 1 GB for Linux Swap?
hdb2 - Ubuntu
hdb3 - Knoppix
hdb4 - Gentoo 
Linux Swap is different than ext3 or reiserfs, it's own format if you will - you'll see when it comes time to format your swap partition.

I prefer to use Reiserfs for my partitions, it's said to be faster than ext3.
I create separate partitions for / & /home directories (for each installed distro). Of course you're free to do as you see fit. I'm just sharing what works for me. :D

<Edit>
Only / partitions need to be bootable. And you can have more than one swap partition, although there's not much point unless each swap is on a separate hard disk. I've read somewhere-or-other that the swap is faster if it's spread over multiple disks, but I've never tried it.
</Edit>

Given what you state above, if I was you, this is how I'd do it.

**/dev/hdb**
** /dev/hdb1:** 5 - 10 GB* partition for Ubuntu
**/dev/hdb2:** 5 - 10 GB* partition for Knoppix
**/dev/hdb3:** 5 - 10 GB* partition for Gentoo (good luck with Gentoo)
**/dev/hdb4:** *Extended partition to contain swap, a storage partition & partitions for each distro's /home (This partition should contain all the remaining disk space.)*
**/dev/hdb5:** 512 MB linux swap partition
**/dev/hdb6:** 5 - 10 GB* partition for Ubuntu /home
**/dev/hdb7:** 5 - 10 GB* partition for Knoppix /home
**/dev/hdb8:** 5 - 10 GB* partition for Gentoo /home
**/dev/hdb9:** use remaining space for large partition to store your files - this can be shared between all OS's. For this I'd use either Ext3 or FAT32 filesystem for maximum accesibility from all OS's. You can use a program called [Explore2fs]("http://uranus.it.swin.edu.au/%7Ejn/linux/explore2fs.htm") to read ext2 & ext3 partitions from within Windows if you dual-boot. FAT32 has the 4GB filesize limitation, don't know about filesize limit with Ext2. (Maybe someone else will help out with this part?) So Ext3 might be the best choice.

* Adjust partition sizes based on your needs & disk capacity.

> Can I partition hdb from Linspire or do I need to use a LIVE-CD?
Which partitioning program do you recommend? 
You can probably partition from Linspire, but I'm not familiar with Linspire's toolset.

You can use one of many Linux LiveCD's to partition ahead of time such as:
[Kanotix,]("http://distrowatch.com/table.php?distribution=kanotix") [Knoppix]("http://distrowatch.com/table.php?distribution=knoppix") & [INSERT]("http://distrowatch.com/table.php?distribution=insert") LiveCD has Qtparted - GUI partitioner
The INSERT LiveCD ISO can be downloaded by itself or you can download the supremely useful [Ultimate Boot CD]("http://ubcd.sourceforge.net/") which contains INSERT LiveCD bootable image plus a plethora of other tools for every imaginable purpose. These can all be found at [Distrowatch.com]("http://distrowatch.com") with the exception of the Ultimate Boot CD. If you like Knoppix, check out Kanotix. I'm sure there are others too, these are my favorites.

<Edit>
You can boot up the Ubuntu LiveCD,  and use synaptic or apt-get to install gparted. If you use apt-get, remember to update before installing; if you use synaptic, remember to reload package information first.
</Edit>

Or you can do it during the disk partitioner phase of Ubuntu's installer. You can create extra partitions even if you're not going to use them with Ubuntu. Just mark other OS's / partition as 'do not mount' in the mount point options (for safety).

>  Sorry for so many question :smile: 
No need to apologize, questions are how we learn. ;)

Glad I can help.

Greenstar

P.S. Please excuse me if I've gone over stuff that you already knew. :)

---

### Post by gmdaneker on 2006-04-14
I am having the same problem with the live cd. I want to try umbuntu before I dedicate another hard drive or a partition on an existing hard drive. I would like some help with this as well. [email]gmdaneker@hotmail.com[/email] subject of umbuntu would be helpfull to filter junk if you could help. Thanks to all that help others, that's what life should be about.

---

### Post by gmdaneker on 2006-04-14
It burns. The complexity of dual booting and disk partitions is pretty confusing. I have 3 hard drive and one of which is dual booted with 2 windows xp pro on them. I want to try another operating system and get away from Microsofts products, but don't want to mess up my files or data. I have tried the live cd, but cannot get past the corrupt cd error message. Any help would be greatly appreciated.

---

### Post by gmdaneker on 2006-04-14
I am having the same problem with the live cd. I want to try umbuntu before I dedicate another hard drive or a partition on an existing hard drive. I would like some help with this as well. [email]gmdaneker@hotmail.com[/email] subject of umbuntu would be helpfull to filter junk if you could help. Thanks to all that help others, that's what life should be about.

---

### Post by Ichido on 2006-04-14
I am in the process of attempting the Partitioning/Formatting/Installation of Kubuntu & Linspire on a laptop drive containing WinXP.
I have "Moved" the WinXP Partition, using Qtparted from a Knoppix CD, down to only 2.5GB and WinXP stills works!
I now have 2 more partitions of about 8GB each.
wish me luck?!
I'll keep posting as I go!

---

### Post by Ichido on 2006-04-17
When I tried to Install Kubuntu, I ran into a snag that has me stopped.
The Installer wants me to Partition my hard drive, which allready is partitioned as:
-------------------------------------
IDE Master (hda) 20GB,
#1 Primary, 2.7GB, ntfs, (which contains WinXP and is set as bootable).
#2 Primary, 7.8GB, ext3, (which is where I want Ubuntu).
#3 Primary, 8.8GB, reiserfs, (want Linspire here).
unuseable, 8.2MB, unuseable (wasted?).
----------------------------------------------------

When I try to proceed, I get the following ERROR:

--------------------------------------
<no Root File System>
No Root File System is defined.
Please correct this from the Partitioning menu.
---------------------------------------

or I get this Screen which i cannot get past:
---------------------------------------
Multidisk (MD) and Software RAID Configuration Menu:
Create MD Device
Delete MD Device
Finish
<go back>
----------------------------------------

I have tried the combinations I thought will work, but none do and I'm stuck in this 'Closed-Loop' and cannot Install.
Help, anyone, PLEASE.

---

