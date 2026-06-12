---
title: "install problems/grub issues on Software Raid system"
date: 2012-06-05
forum: Installation &amp; Upgrades
---

### Post by lseg on 2012-06-05
Hi guys,

I am trying to set up a home server with software raid.
My new system has a MSI B75MA-P45 motherboard with Intel G620 and 3 WD Caviar Green 2.5Tb hard disks

I followed following instructions:
[http://wiki.graven-ict.nl/index.php/Installatie_Linux_software_RAID_5](http://wiki.graven-ict.nl/index.php/Installatie_Linux_software_RAID_5)

Using ubuntu alternate on a USB drive to install it.

Basically I am making a partition of 256 MB on each disc
setting it up as Raid1 and making it ext4 for /boot. So boot partition is in Raid1.

secondly I made a partition with rest of data, making it Raid5.
In the raid5 I make an LVM with a swap partition of 4Gb and rest is set to root (/). (on website they use seperate partition for /home and /, tried that too)


I got 2 problems:
1) during installations of the applications, it suddenly stopped and gave an error with no extra info
2) when trying to install the bootloader it also failed, could not write to mbr, not to sda, not to sda1 etc. Not so sure what to do here.

First thing I changed after that is to add a small extra Bios partition on each disc (after reading I needed that on a GPT disc). Unfortunately I got exactly same issues.

Now I am stuck with Grub rescue (which is probably a leftover from when I tried to install Ubuntu on that 1 disc, just to check if that at least worked).

I am really stuck here. I have no idea why installing the application failed, and especially why I have problems with Grub.

Is this related to my 2.5Tb discs (GPT partioned) or to my UEFI enabled motherboard?

kind regards,

Luc

---

### Post by darkod on 2012-06-05
Can your board boot only in UEFI or also in standard bios mode?

Some boards try to boot in bios mode if they can't find UEFI boot.

You can try looking in the bios and disable UEFI if you can, and try it like that. Otherwise, if the board can boot only in UEFI you also need an UEFI System partition on the disk(s). It needs to be the first partition, approx 300MB and FAT32. It needs to be of type EFI System partition.

Maybe that's what's missing.

But I haven't worked with UEFI, still too new, and many unknowns about it. If you can disable it, I would do that. Don't see any advantage over bios boot anyway.

---

### Post by steeldriver on 2012-06-05
Hi Luc, I have just built a mythbuntu (11.10) HTPC with RAID1 using 2 x 2TB Greens -  there are some issues using WDC Green drives in RAID that you should know before you go too much further.

It seems to be the power saving features causing excessive parking / unparking. There is supposedly a firmware fix but it is only available as a Windows exe:

[http://www.storagereview.com/how_stop_excessive_load_cycles_western_digital_2tb_caviar_green_wd20ears_wdidle3](http://www.storagereview.com/how_stop_excessive_load_cycles_western_digital_2tb_caviar_green_wd20ears_wdidle3)

There are some non-RAID specific OS level workarounds suggested by WDC here (but obviously you would need to be able to install/boot to apply them):

[http://wdc.custhelp.com/app/answers/detail/a_id/5357/session/L3RpbWUvMTMzMTMwMTI1OS9zaWQvbzdOemNGU2s%3D]("http://wdc.custhelp.com/app/answers/detail/a_id/5357/session/L3RpbWUvMTMzMTMwMTI1OS9zaWQvbzdOemNGU2s%3D")

In my case it's not critical because the RAID is only mounted as a data volume (/var/lib/mythtv) with the system on a separate SSD except for /var and /tmp on small non-RAID volumes - I have a similar partitioning scheme to yours except each Green has a 64GiB non-RAID sd[ab]1 with a single RAID1 array assembled from the remaining ~1.8TiB sd[ab]2 - in fact I did a regular (non-RAID) install and then added mdadm and configured and mounted the RAID array after. 

My symptoms are that as soon as I start mythtv (the only thing that accesses the array) the drives begin thrashing. After my last boot it took more than 2 days to resync. I can't say that your install issues are related but it is something to bear in mind.

---

### Post by lseg on 2012-06-05
Darkod,

I believe I can set my BIOS to boot from BIOS instead of UEFI. But how would that affect my installation ?
Should I first change my BIOS settings and reinstall everything ?
I am just wondering how this BIOS change could have affected my installation problems.

Kind regards,

Luc

---

### Post by lseg on 2012-06-05
Steeldriver,

Did you actually change something to your drives ? Did you change the logging settings in Linux or the idle time from the Hard disks ?

I noticed your /var is on the HD, so the logs will be stored on it.

Thank you to both of you for the replies.

Kind regards,

Luc

---

### Post by steeldriver on 2012-06-05
I haven't changed anything yet - right now I am trying to create a bootable WinXP CD to see if that will let me apply the wdidle.exe fix

If that fails, I have a new Win7 desktop system arriving soon and I will swap the Greens into that and try the wdidle fix from there

If I get time before that I will try at least the hdparm fix... it's kind of ironic that I put /var on the WDC to minimize writes to the SSD :rolleyes:

If I had to guess I would guess the disk idle issue *may* have contributed to the stalled install but there's something bigger preventing grub writing your boot info (at least after you created a separate non-RAID partition for /boot) 

I purposely left sda1 empty for now and I *could* reinstall /boot and/or / to that just to see if it works... hmmm

---

### Post by darkod on 2012-06-05
Like I said, if the board tried to boot in EFI and only EFI, it will never boot without the EFI system partition. And you didn't mention you have one. That is how it would affect the boot.

Changing to bios boot eliminates the need for a EFI system partition.

You will still need to have the bios_grub partition because you are using gpt. Note that this partition should NOT have a filesystem, only the partition. Not sure if it works with a filesystem on it.

One tool to create only partition without filesystem is parted for example.

---

### Post by steeldriver on 2012-06-05
Well I now realize this is probably OT but since it may come up in searches here's an update on my situation - mods please feel free to move or split, I'm new here so I hope this doesn't offend anyone

My disk thrashing turned out to be continuous log writes from a failed mythbackend EIT (broadcast schedule info) grab (doh!) . **Nevertheless, smartctl *was* showing Load_Cycle_Counts already up into the 20k range on both drives (BAD!)**

I had no luck with hdparm (these are WD20EAR**X** drives; most of the results I could find on the web are for WDxxEAR**S** drives) 

```
$ sudo hdparm -B 255 /dev/sdb

/dev/sdb:
 setting Advanced Power Management level to disabled
 HDIO_DRIVE_CMD failed: Input/output error
 APM_level    = not supported

``````
$ sudo hdparm -B /dev/sdb

/dev/sdb:
 APM_level    = not supported

```However I did NOT have to resort to the WDC wdidle.exe fix - it turns out there is a Linux-native project called idle3-tools (had to build from the - small - tarball but it looks like a binary package might be available in newer repos) and it was able to disable the timers

```

$ sudo ./idle3ctl -d /dev/sdb
Idle3 timer disabled
Please power cycle your drive off and on for the new setting to be taken into account. A reboot will not be enough!

$ sudo ./idle3ctl -d /dev/sdc
Idle3 timer disabled
Please power cycle your drive off and on for the new setting to be taken into account. A reboot will not be enough!


AFTER POWER CYCLE (NB the drive assignments have changed from sd[bc] to sd[ab])
=================

$ sudo ./idle3ctl -g103 /dev/sdb
Idle3 timer is disabled

$ sudo ./idle3ctl -g103 /dev/sda
Idle3 timer is disabled

```[http://idle3-tools.sourceforge.net/](http://idle3-tools.sourceforge.net/)

---

### Post by lseg on 2012-06-06
New Update:

I put the BIOS in legacy mode instead of UEFI. And by doing this I got problems with my USB stick with linux live CD.
So I burned a CD instead and installed it from there.

1st succes: the installation took much longer, but did not give any problem (where it previously failed when installing applications and when installing GRUB). So no failure, but unfortunately I did not see all messages, since I could not wait for so long.
I am guessing this installing from a USB stick is not working 100%.

But: I still can not boot, if if I change to legacy or to uefi in my BIOS. I just get a blinking cursor, nothing else.

I am pretty sure this issue is not related to UEFI or Legacy mode, since I was able to install Ubuntu, when using a standard installation on 1 disc (so no raid, other discs disconnected). This Ubuntu installation also did not make an UEFI partition, but just made 1 BiosGrub partition, 1 swap and 1 big root ext4.

So I am guessing I need to install grub somehow and fix it. Question is: where should I install grub, how should I do it and what should it point to.

Kind regards,

Luc

---

### Post by darkod on 2012-06-06
The blinking cursor can be a video driver issue too. Do you have nvidia?

Ubuntu might be installed correctly this time, only a video driver stopping you load it.

Try to set the nomodeset parameter. You have instructions here both for live mode and for already installed system:
[http://ubuntuforums.org/showpost.php?p=10069997&postcount=1](http://ubuntuforums.org/showpost.php?p=10069997&postcount=1)

---

### Post by lseg on 2012-06-07
Hi,

I basically solved this issue by using the Boot Repair tool. Problem was 100% related to Grub problem.

Thanks for all help.

Kind regards,

Luc

---

### Post by lseg on 2012-06-08
I had to do the installation again, since my partitions were not aligned, so maybe it is useful if I explain how I did it.

I decided to make 3 partitions on all discs:
1) Bios partition of 1Mb
2) Partition of 100Gb in Raid1 for root
3) Partition of 2.3Tb in Raid5 for /home

I did not use LVM anymore, dont see the use for it, in my personal case.
here are the steps I used:
1) configuring the partitions
To get the partition ok, I used cgdisk, this tool will get the alignments ok. Unfortunately it did not work on Ubuntu Live Cd, and used Fedora Live CD instead. Open terminal, do "su -" and start with cgdisk.
2) installing everything
used CDrom (not USB stick, got into trouble with that one)with Ubuntu alternate.
Setup the raid device, using Partitions I made in step1. Doing the whole installation.
3) unfortunately the installation is still not booting (grub problem), I needed to boot with Ubuntu Secure CD. This to run Boot Repair ([http://ubuntuforums.org/showthread.php?t=1769482&highlight=boot+repair](http://ubuntuforums.org/showthread.php?t=1769482&highlight=boot+repair)), which will fix the faulty Grub installation.

Hope this helps.

Kind regards,

Luc

---

