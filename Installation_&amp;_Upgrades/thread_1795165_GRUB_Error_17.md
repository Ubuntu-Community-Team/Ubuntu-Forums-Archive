---
title: "GRUB Error 17"
date: 2011-07-02
forum: Installation &amp; Upgrades
---

### Post by binukavumkal on 2011-07-02
Hi All,

I have been successfully using  Ubuntu for the last 4 years now and currently using 10.04 LTS on a Desktop

I have a dual booting having Windows XP.

Recently I had to replace the Mother board battery and after that and verified BIOS are set up and saved successfully.

After that the system does not boot due to following error

GRUB Loading... GRUB error 17.

I booted with a Live CD 10.04 and able to access the hard disk (Total 80GB )and 

sudo fdisk -l shows

  Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        2420    19438618+   7  HPFS/NTFS
/dev/sda2            2434        9729    58605120    5  Extended
/dev/sda3            2421        2433      104422+  82  Linux swap / Solaris
/dev/sda5            2434        4866    19543041    7  HPFS/NTFS
/dev/sda6            4867        7299    19543041    7  HPFS/NTFS
/dev/sda7   *        7300        9729    19518943+  83  Linux

I see /dev/sda2 is partitioned wrongly since I have 4 partitions  of 20GB.

Only 20GB is allocated to Linux 83.

But as you see in the screen shot attached, somehow 60GB partition is created.

Also Linux partition is not detected.

Please help me to retrieve the System into Original State.

Can I remove the 60 GB partition?
How can I set up Linux Partition to be detected by the system?

---

### Post by binukavumkal on 2011-07-02
Please see the screenshot of the current partitions in the Harddisk

---

### Post by gradinaruvasile on 2011-07-02
Grub error 17:

```

17 : "Invalid device requested"

 This error is returned if a device string is recognizable but does not fall under the other device errors.

```

Check the disk drive order + boot order in the BIOS settings - probably it switched your dvd and hdd order after it was reset.
You see, you have 2 drives - a hdd and a dvdrw. The BIOS has a device order in it. From Linux point of view you wil have 2 devices - sda and sdb - but if the BIOS decides to switch them, your hdd will no longer be sda, but sdb (or viceversa).
Grub begins to load from the boot device and looks for say sda, but if the BIOS switched the order, that device is the DVDRW so it throws an error because he does not fint the /boot directory on that one.

So here you have to do the following: go into the BIOS and set the order of your drives.

If that doesnt work, reinstall grub from the live cd:

1. boot the CD
2. mount the Linux partition by opening disk utility, select the linux partition then click "mount".
3. right-click on the link of the mounted location that appears afterwards, select "copy link address"
4. Open a terminal and type:

```

grub-install --boot-directory=/mnt/boot /dev/sda1

```

where:

/mnt/boot - this is the directory your /boot partition is mounted - paste the copied link location AND DELETE  the "file://" part so that it will look like (the long ID will differ):

```

/media/e3ecaf06-0ad8-42d1-889a-a8a8edbb87c3/boot/

```

Example:

```

grub-install --boot-directory=/media/e3ecaf06-0ad8-42d1-889a-a8a8edbb87c3/boot/ /dev/sda1

```

PS: If the Linux partition is damaged, you will also get this error even the device order is right. In that case you will have to check the damaged partition:

1. boot the live cd
2. Unmount the partition (if mounted) in question from disk utility - VERY IMPORTANT! 
3. open a terminal and type:

```

fsck -f /dev/sda1

```

cross fingers... :)

---

### Post by YesWeCan on 2011-07-02
Your partitions look ok. The sda2 "extended" is just a container for logical partitions, specifically your two 20GB NTFS and your 20GB linux.

I am a little concerned that Disk Utility does not recognise your sda7 partition type. If you browse it does it look ok - contain /boot, /media, /home, /usr and so on?

Your SWAP partition is ineffectively small at just 107MB. If you are going to have a SWAP at all it should be a couple of GB or the same as your RAM size  if you want to "hibernate".

The boot flag is set on sda7 and this serves no purpose as Grub doesn't use it, but Windows does so you should really have it set on sda1. To do this:
[COLOR=DarkGreen]sudo sfdisk /dev/sda -A1[/COLOR]

I think "GRUB error 17" is a legacy Grub error message. So you must have upgraded from an earlier version of Ubuntu. It would be good to upgrade to Grub2 at some point. See [https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)

The question remains as to why it no longer boots, coincident with you changing the mobo battery and, I assume, upgrading your bios. Grub error 17 is about the Grub boot code not being able to find its files in the /boot/grub partition in sda7.[ http://members.iinet.net.au/~herman546/p15.html#17]("http://members.iinet.net.au/%7Eherman546/p15.html#17")

It would be helpful if you would download and run this and post RESULTS.txt here:[[FONT=Nimbus Sans L, sans-serif]http://bootinfoscript.sourceforge.net/[/FONT]]("http://bootinfoscript.sourceforge.net/")

---

### Post by binukavumkal on 2011-07-02
Thanks a lot gradinaruvasile for your quick analysis.

As you can see the hard disks in my system is identified as sda only (fdisk -l)

From screen shot  /dev/sda7  is my Linux partition and it is not recognized by my disk utility. That is my concern. 

Then I deleted that partition using the disk utility and give Linux ext3 20GB.

I am able to mount but nothing iniside except a lost and found directory...


root@ubuntu:/home/ubuntu# fsck -f /dev/sda7

fsck from util-linux-ng 2.17.2
e2fsck 1.41.11 (14-Mar-2010)
Pass 1: Checking inodes, blocks, and sizes
Pass 2: Checking directory structure
Pass 3: Checking directory connectivity
Pass 4: Checking reference counts
Pass 5: Checking group summary information
Linux: 11/1220608 files (0.0% non-contiguous), 120668/4879735 blocks

---

### Post by binukavumkal on 2011-07-02
**YesWeCan** your analysis is  helpful

I upgraded from the previous version. 
I pasted the output.

How can I know my BIOS is upgraded...

All devices are set to detect automatically.

i.e. Primary Master, Primary Slave, Secondary Master, Secondary Slave etc.

My concern is whether I lost the data in Linux partition.

Please help.

**gradinaruvasile**, 

I dont see any  boot directory in /mnt/Linux which is my Linux Partition
/dev/sda7

Thanks for your prompt reply.

---

### Post by gradinaruvasile on 2011-07-02
> **binukavumkal said:**
> Thanks a lot gradinaruvasile for your quick analysis.

As you can see the hard disks in my system is identified as sda only (fdisk -l)

From screen shot  /dev/sda7  is my Linux partition and it is not recognized by my disk utility. That is my concern. 

Then I deleted that partition using the disk utility and give Linux ext3 20GB.



Hm. You formatted the sda7 partition with the disk utility.

Maybe a bit late now to ask, but did you try fschecking/mounting it after you booted up with the live cd before doing anything else on it?
And did you run any program on Windows that had to do with unknown (for Windows, that is) partitions?

Now you will have to reinstall Ubuntu.

If you want to boot Windows before that you have to boot with a Windows install CD, go in recovery mode and issue a "fixboot /mbr" command.

The lost+found directoy is created automatically by fsck btw if this matters now.

PS. You are right about the hdd naming. CD/DVDs are sr0 or cdrom. My bad. Only if you have 2 or more hdds you can have the issue i described on my previous post.

---

### Post by binukavumkal on 2011-07-02
> **gradinaruvasile said:**
> Hm. You formatted the sda7 partition with the disk utility.

Maybe a bit late now to ask, but did you try fschecking/mounting it after you booted up with the live cd before doing anything else on it?
And did you run any program on Windows that had to do with unknown (for Windows, that is) partitions?

Now you will have to reinstall Ubuntu.



I tried to mount /dev/sda7 before doing anything on that. But not able to mount that using disk utility or root terminal.

It is not recognized at all.
I never ran any Windows programs since I changed my system battery. I am not able to even see the GRUB menu

sudo sfdisk /dev/sda -A1

I ran the above command and restarted the system and Now the error is

**GRUB Error15.**

---

### Post by gradinaruvasile on 2011-07-02
Reinstall Ubuntu. Everything that was on that partition is gone, including the grub settings.

[http://www.uruk.org/orig-grub/errors.html](http://www.uruk.org/orig-grub/errors.html)

---

### Post by YesWeCan on 2011-07-02
> **binukavumkal said:**
> I tried to mount /dev/sda7 before doing anything on that. But not able to mount that using disk utility or root terminal.

It is not recognized at all.
I never ran any Windows programs since I changed my system battery. I am not able to even see the GRUB menu

sudo sfdisk /dev/sda -A1

I ran the above command and restarted the system and Now the error is

**GRUB Error15.**
That's right. You deleted your Ubuntu root partition so Grub cannot find its files.

You'll have to reinstall Ubuntu.

Before you do that, if you wish to boot Windows, you can reinstall the standard MBR (but you may just want to re-install Ubuntu which will install Grub2 and then you can boot both):
[COLOR=Navy]sudo apt-get install lilo
sudo lilo -M /dev/sda mbr[/COLOR]

While you are in GParted, just delete the 107MB swap partition. Reduce the size of the Ubuntu partition to 18GB and add a 2GB swap next to it. :)

---

### Post by YesWeCan on 2011-07-02
> **gradinaruvasile said:**
> 
```

grub-install --boot-directory=/mnt/boot /dev/sda1

```where:

/mnt/boot - this is the directory your /boot partition is mounted

You may have meant sda rather than sda1, which is the Windows partition. This is easy to mix up. :)

For instance,
[COLOR=Navy]grub-install /dev/sda[/COLOR] puts the boot code and 2nd stage code in the MBR area of the disk.
[COLOR=Navy]grub-install /dev/sda1[/COLOR] puts the boot code in the PBR of that partition, which is not what is wanted in this case because that will over-write the Windows PBR code and won't put the Grub boot code in the MBR.

The way I do this sort of operation is:
[COLOR=DarkGreen]sudo mount /dev/sda7 /mnt
sudo grub-install --root-directory=/mnt /dev/sda[/COLOR]

---

### Post by binukavumkal on 2011-07-05
Thanks *gradinaruvasile* and *YesWeCan*

I am going to install 11.04 from a Live CD.

---

