---
title: "Can GRUB2 work as independent bootmanager?"
date: 2011-05-25
forum: Installation &amp; Upgrades
---

### Post by j.jansen on 2011-05-25
I assume that I have not understand grub2 correct and need help.
 In the past I have used grub legency in the following configuration.
 SDA6 = 2 GB partition ONLY for grub as bootmanager.
 I have sda1-sda3 and sda7 to sda9 as system partitions.
 As backup I used TAR to an nas system and this way I could restore any partition from the tar file to any partition on my harddisk.
 The only part which I did manual was edit FSTAB on the recovered partition and modified the grub menu.cfg.
 This way my bootmanager was independent from any operating system and partition (except sda6).
 When I replace the harddisk, a recovery of grub legency was easy and after I copied the backup files back to sda6, I could continue to to restore the tar files and my system was up and running again.
 

 Now with grub2 each linux installation thinks it is the master of my harddisk and takes over control from my sda6. Yes it discovers other linux versions etc but I loose control over my bootmanager.
 

 How can I use grub2 with an independent bootpartition (sda6) and how can I configure this bootpartition (sda6) from each installed linux partition? With other words no FIXED linux partition is responsible for my bootmanager.
 

                                  - for someone asked why I need more versions of linux – the free vmware server 2 does not work on newer versions of linux. The latest vmplayer can not work with newer version of firefox. This is ONLY an example why I have more as one version of linux.

---

### Post by srs5694 on 2011-05-25
You can do it exactly the way you did with GRUB Legacy. The problem you describe is with OS installers insisting on installing their boot managers. Some enable you to not do so, and some enable you to install their boot loaders to a boot partition rather than to the MBR. Either approach will enable you to keep your dedicated boot loader partition in control of the computer as a whole, no matter what boot loader it uses. If any OS insists on overwriting the MBR's boot loader, you'll have problems with it no matter what boot loader you installed there (and on a dedicated partition, if applicable) originally.

---

### Post by oldfred on 2011-05-25
Part of the advantage of grub2 is the os-prober which finds most all other systems and sets up booting of them. I stopped using my dedicated grub legacy partition, but do add custom entries to 40_custom and use os-prober less.

Grub2 does not like to be installed to a partitions boot sector as it is larger and then has to use blocklists or hard coded addressed to load the rest of grub. If the grub file moves due to updates or even a e2fsck then you have to reinstall grub2's boot loader.

But grub2 will let you directly boot just about anything and you can still chainload to any grub legacy installs. You just have to know the differences in the boot stanza. I have not done much with grub 1.99, but it now checks for more errors as an old error I had in my 40_custom prevented it from working where all the older grub2's worked (but I was missing one stanza and did not notice as it was something I did not really use anymore).

Herman on separate grub or grub2 partition:
[http://ubuntuforums.org/showthread.php?t=1320270](http://ubuntuforums.org/showthread.php?t=1320270)

Grub2
[http://members.iinet.net/~herman546/p20/GRUB2%20Bash%20Commands.html#Dedicated_GRUB_Partition_](http://members.iinet.net/~herman546/p20/GRUB2%20Bash%20Commands.html#Dedicated_GRUB_Partition_)

You will have to manually edit your grub.cfg, but with Debian installs a link to the most current kernel in in / (root). The /vmlinux and /initrd.img are links to the newest kernels,

from Ranch hand
Note that this does not define the kernel. It defines the partition. It boots the newest bootable kernel that it finds at that partition.

menuentry "Daily on sda13" {
    set root=(hd0,13)
        linux /vmlinuz root=/dev/sda13 ro quiet splash
        initrd /initrd.img
}

If drive & partition are correct you do not need search as that is when drive numbers may change and then it looks by UUID to find correct partition to boot.

If you have more than one drive you can chainload to other MBRs, but BIOS boot drive will be hd0 so number can change.

```
menuentry "Lucid Lynx on sda (When from sdc) Chainboot" {
set root=(hd1)
chainloader +1
}

menuentry "9.04 on sdb (from sdc) Chainboot" {
set root=(hd2)
chainloader +1
}

menuentry "Chainload Other Systems Grub Menu on sdc1" {
set root=(hd2,1)
chainloader +1
}

menuentry " " {
set root= 
}

```

---

### Post by psusi on 2011-05-25
You mean sda6 was /boot, or /boot/grub?  2gb is HUGE for that.

The tick box to NOT install grub when you install Ubuntu was removed in 10.10.  You have to manually run ubiquity -b I think the switch was, to skip installing grub.

---

### Post by srs5694 on 2011-05-25
> **oldfred said:**
> Part of the advantage of grub2 is the os-prober which finds most all other systems and sets up booting of them. I stopped using my dedicated grub legacy partition, but do add custom entries to 40_custom and use os-prober less.

I've always been wary of auto-probers like this; if done right they work well 95% of the time, but the remaining 5% of the time they cause well over 20x the hassle of doing it by hand the rest of the time. GRUB 2 in particular does suffer from this problem, although you've got to run many and/or exotic installations before you run into serious problems. In my experience, Ubuntu's GRUB 2 failure rate on UEFI systems in particular is abysmal (it's batting 0 for 2 so far for me, and I've seen similar problem reports from others on this forum), although it's much better on the more common BIOS systems.

> Grub2 does not like to be installed to a partitions boot sector as it is larger and then has to use blocklists or hard coded addressed to load the rest of grub. If the grub file moves due to updates or even a e2fsck then you have to reinstall grub2's boot loader.

None of this is relevant if you've got a GRUB 2 in the MBR that points to a dedicated GRUB 2 partition that's not part of a standard installation. You can then install Ubuntu's GRUB 2 to the Ubuntu partition and it'll never be used, so its use of block lists is irrelevant.

---

### Post by oldfred on 2011-05-25
We used to spend all our time helping average dual booters set up windows and Ubuntu as grub legacy did not find it or find it correctly. Early grub2 os-prober while finding windows (but even reverses Vista &  Vista recovery) often missed something on other systems.

But manual set up is difficult for the average user. Even those who liked editing menu.lst would put boot stanzas inside the automagic area and wonder where their custom entry went to on an update. 

I use a totally manual grub.cfg for ISO booting my flash drives and a windows repair CD. But I do not expect an average user to be able to do that. Thus os-prober for many is a good thing. And then we can help those who need it.

Many grub legacy users would chainload to another grub entry in the system or boot partition. That does not work well with grub2, but as you say it is not required with grub2 as you can directly boot most systems.

---

### Post by j.jansen on 2011-06-01
I am still strugling with this.
To be correct, what I am looking for is a independed grub2 partition.
 - yes I know 2 GB is larger as needed for this, but that should not be a problem -

My questions are:
How to mount this partition to EACH active running linux version?
Can I run a automatic update from EACH independed running linux version?
- when sda3 is booted with suse linux, with suse, when ubuntu is booted from sda8, then with ubuntu.
--
- What are the steps when I restore an linux from a backup TAR file to for example sda7?
- my PREVIOUS normal steps are: format of sda7 (to remove any old files), then restore the files to sda7, modify fstab to point to sda7, and mofify the grub menu.

---

### Post by oldfred on 2011-06-01
Youi do not mount it in each install. You cannot run auto updates. It is manual, but for most installs requires little or no maintenance. It is an independent boot loader that is before all installs.

If the version of Linux uses grub legacy you install it to the PBR not MBR. Then you just add a chainboot entry in the grub2 menu like you do with grub legacy to chainload to it. If it is Debian based you can load the links that have the newest kernel. Others may require custom entries that will have to manually be maintained on updates. 

I posted typical chainload entries to a partition- PBR or MBR. And the entry for booting the link that Ranch Hand posted a long time ago.

If reinstalling to a partition you will also have to reinstall grub's boot loader to the PBR. Or backup the partition boot sector also.

---

