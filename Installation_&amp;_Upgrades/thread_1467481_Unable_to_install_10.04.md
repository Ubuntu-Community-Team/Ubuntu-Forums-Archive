---
title: "Unable to install 10.04"
date: 2010-04-30
forum: Installation &amp; Upgrades
---

### Post by weaver4 on 2010-04-30
After installation I get a error on reboot.

```
"Gave up waiting for root device."

It also give the error "Missing modules (cat /proc/modules; ls /dev"

And Finally it says:
ALERT: /dev/disk/by-uuid/90eoad56....11d9 does not exist. Dropping to shell!"
```

I looked and the directory /dev/disk/by-uuid does not exist.

Some help would be appreciated.

---

### Post by djchandler on 2010-04-30
> **weaver4 said:**
> After installation I get a error on reboot.

```
"Gave up waiting for root device."

It also give the error "Missing modules (cat /proc/modules; ls /dev"

And Finally it says:
ALERT: /dev/disk/by-uuid/90eoad56....11d9 does not exist. Dropping to shell!"
```I looked and the directory /dev/disk/by-uuid does not exist.

Some help would be appreciated.
That file is simply a symbolic link to one of the disk partitions. It doesn't hold any data itself.

Tell us about the hard drive you installed Ubuntu to. Is this a dual boot system (or more)? Is it IDE or SATA? How old is the drive? How old is the rest of the computer? Have you upgraded a component lately? It sounds to me as if a probe of the hard drive firmware failed to return all the necessary information to complete the configuration.

We could give you hoops to jump through, but if the installer, Ubiquity, wasn't able to properly set up these files, that (to me) means something else could be wrong, perhaps at the hardware level. I had something similar occur after the Gutsy (7.10) install due to a flaky power supply that affected the power going to the hard drive.

I'm fanatic about power supplies. They are usually the first part of a system to fail. I've recovered several systems from the local computer recycling center where the only problem was a bad power supply. That kind of a problem produces intermittent errors that are difficult to reproduce.

---

### Post by sunrex on 2010-05-01
I'm confirming this issue. I setup a RAID10 array and a RAID1 array (raid1 for boot). 4x500GB SATA2 drives with IDE mode enable (ACHI does the same thing).

Surprisingly when its in easybox the raid10 array is building (since it still has to sync that first time its run), but RAID1 is not listed at all.

However, when I boot into the recovery shell from the alternative disk, raid1 and raid10 is listed just fine and it continues to build raid10 from the shell.

Currently it goes like this on startup:

Error: fd0 read error.
Error: file not found.
Gave up waiting for root device, common problems:

long list of problems goes here.

Alert! /dev/disk/by-uuid/uuidlonglablething (obviously not the UUID) does not exist. Dropping to a shell!.

And then I'm back in easy box.

From what I'm seeing, it either doesn't load grub or this is grubs recovery shell.

It's not my hardware because I can get raid10 and raid1 working fine in centos 5.4 64bit, but I hate centos so I'm trying to get this to work in ubuntu.

---

### Post by djchandler on 2010-05-01
@ sunrex:

Yeah, you could probably teach me a thing or two when it comes to hardware. RAID 10 is something I'm not familiar with.

If you keep encountering problems you may want to post your help request(s) over in the [Server Platforms]("http://ubuntuforums.org/forumdisplay.php?f=339") forum. Furthermore, this has the feel of a professional support request. You may want to look into a getting in touch with Canonical's [professional support services and other free support options]("http://www.ubuntu.com/support")  for Ubuntu.

Good luck!:)

In the meantime, have you seen these resources?

[http://ubuntuforums.org/showthread.php?t=319903](http://ubuntuforums.org/showthread.php?t=319903)

[http://ubuntuforums.org/showthread.php?t=1128145](http://ubuntuforums.org/showthread.php?t=1128145)

[http://ubuntuforums.org/showthread.php?t=1020182](http://ubuntuforums.org/showthread.php?t=1020182)

[http://www.linuxplanet.com/linuxplanet/tutorials/6514/1/](http://www.linuxplanet.com/linuxplanet/tutorials/6514/1/)

[http://www.linuxplanet.com/linuxplanet/tutorials/6518/1/](http://www.linuxplanet.com/linuxplanet/tutorials/6518/1/)

[http://www.howtoforge.com/install-ubuntu-with-software-raid-10](http://www.howtoforge.com/install-ubuntu-with-software-raid-10)

[http://www.howtoforge.com/creating-a-dual-boot-system-on-raid10-ubuntu-windows](http://www.howtoforge.com/creating-a-dual-boot-system-on-raid10-ubuntu-windows)

---

### Post by sunrex on 2010-05-01
I'm going to give [http://www.howtoforge.com/install-ubuntu-with-software-raid-10](http://www.howtoforge.com/install-ubuntu-with-software-raid-10) a try.

I've been at this for about 9 hours now none stop, so yeah I think I'm pretty damn dedicated/stubborn :P.

Thanks!.

---

### Post by weaver4 on 2010-05-01
It is a rather new ASUS UL50 laptop, which uses the new Intel CULV laptop.  The hard drive is a SATA.

I did bring the system up using SystemRescue Linux and tested the drive and it says the drive is OK.

It is a dual boot system and Win7 runs fine on the machine.  It was a dual boot Ubuntu 9.10 and Win7.  Ubuntu 9.10 ran great on the machine.

To build the system I deleted the two partitions that held Ubuntu 9.10 and told Ubuntu 10.04 to use the free space.

One other "odd" thing is that it took 30 minutes from when I booted the Live-CD to the welcome screen.  Thinking this was a problem with the Live-CD I downloaded a second copy and put it on a USB drive, but I got the same results.  During the 30 minute "delay" it is accessing the hard drive; why is that?

One last "clue" when booting "SystemRescue" it stalled quite a while on the RAID test, but my laptop does not use raid and there is no bios setting for it.

---

### Post by Rususeruru on 2010-05-01
Looks like we were having a the same or similar problems.
Installation took forever on my system (Toshiba NB205)
I successfully install Ubuntu several times but could never boot from the installation.

I just went into my BIOS and changed **SATA Controller Mode** to **Compatibility **from** AHCI** and viola successful boot!

I'm guessing there is a driver for AHCI which may be disabled or not loading at boot before it tries to mount / but this is just conjecture based on a similar problem with Windows installations I've had with these machines.

--EDIT--

Looks like this has been an issue before with Karmic [http://ubuntuforums.org/showthread.php?t=1310496](http://ubuntuforums.org/showthread.php?t=1310496)
Funny 9.10 worked fine on this system without changing SATA settings in BIOS

---

### Post by weaver4 on 2010-05-01
Like your link I also see the errors like:

ERROR: asr:
ERROR: ddf1:
ERROR: nivida:
ERROR: lsi:

I have no idea what to do about them.  I brought up gParted and deleted all of my partitions but when I try to boot various Linux distributions like SystemRescue they show up.

There has got to be some utility to bring my hard disk back to "new condition" with nothing stored in it.

BTW:  I reinstalled window without problem.

Help!!

---

### Post by sunrex on 2010-05-01
I like how nobody seems to have a solution to this problem.

I decided to completely abolish raid1 and just go with raid10 and have /boot on another partition on one hard drive.

Unfortunately, the same crap happened to me again.

This is starting to look more and more like an installation issue then a raid problem, I bet if I installed it with only one hard drive and no raid the same thing would happen.

I am using the alternative x64 DVD for this, and not the desktop iso.

---

### Post by happ on 2010-05-01
Try to change disk configuration in BIOS to IDE (Compatibility). It worked to me. You can change it back after installation.

---

### Post by weaver4 on 2010-05-01
I tried changing the bios and had the same problem, except windows would no longer boot.

---

### Post by eombah on 2010-05-01
Same problem here, I've spent the whole evening trying to install Lucid in a raid0 configuration with no succes.

I have /dev/md0 mounted on / , /dev/md1 is swap.
When I am dropped in busybox I only see /dev/md1.

Rescue mode allows me to mount /dev/md0 just fine.

-Bart

---

### Post by djchandler on 2010-05-01
> **sunrex said:**
> I like how nobody seems to have a solution to this problem.

I decided to completely abolish raid1 and just go with raid10 and have /boot on another partition on one hard drive.

Unfortunately, the same crap happened to me again.

This is starting to look more and more like an installation issue then a raid problem, I bet if I installed it with only one hard drive and no raid the same thing would happen.

I am using the alternative x64 DVD for this, and not the desktop iso.
Your issue may be beyond the scope of amateurs' ability to provide support--it's certainly beyond my experience.

You have several other choices for free support.

[http://www.ubuntu.com/support/community/chatirc](http://www.ubuntu.com/support/community/chatirc)

[http://www.ubuntu.com/support/community/mailinglists](http://www.ubuntu.com/support/community/mailinglists)

[https://wiki.ubuntu.com/LoCoTeamList](https://wiki.ubuntu.com/LoCoTeamList)

[https://answers.launchpad.net/ubuntu](https://answers.launchpad.net/ubuntu)

---

### Post by djchandler on 2010-05-01
> **weaver4 said:**
> I tried changing the bios and had the same problem, except windows would no longer boot.
That's exactly what will happen changing between AHCI and IDE mode on a Windows installation. There's a fix for that at [http://technet.microsoft.com](http://technet.microsoft.com) if you need it, but you should probably just change back to AHCI to get your Windows back.

---

### Post by djchandler on 2010-05-01
@ Rususeruru & Weaver 4;

You guys are going to hate this answer, but this could be what's biting you. I know I don't like what I'm telling you one bit, but I feel honesty is the best approach. I had to dig a bit to find some of this on my own.:(

Intel is developing its own Linux distribution, Meego (used to be Moblin). Intel drivers are being submitted for the upcoming kernel version, 2.6.33. Apparently it's up to each distribution to work around Intel driver issues with previous kernels. This LTS release is using 2.6.32-21 at present.

One of the problems just before release was a bad memory leak using xorg  drivers with Intel and Nvidia graphics chips. Using ATI or proprietary  Nvidia graphics drivers circumvented this issue. Apparently we didn't  have nearly enough beta testers with Intel GMA graphics. And those that were testing with Intel GPUs had plenty of problems, in my opinion disproportionate to problems ATI and Nvidia users had.

A couple of us [suggested during beta testing]("http://ubuntuforums.org/showpost.php?p=9087287&postcount=634") that some problems that were troublesome about six weeks to a month ago could cause the delay of this release. Needless to say we were in the minority. My observation is that those existing problems overshadowed problems that have subsequently been revealed since the release on April 29th. As we speak, there is a new ISO being formulated to replace the current 10.04 ISO release.:confused:

[http://www.phoronix.com/scan.php?page=news_item&px=ODE5Ng](http://www.phoronix.com/scan.php?page=news_item&px=ODE5Ng)

As much as I hate to say this, you currently have three choices:

1. Wait for the next ISO. But I don't know if that will affect your issues or not.

2. Use another distribution that has solved or by-stepped the Intel GMA problem in order to use Linux on your systems using Intel GMA GPUs.

3. Install the last LTS (8.04), apply all updates, then perform an upgrade of that installation to 10.04. I have no idea if that will work for you or not.

I have been running this 64-bit installation since the Release Candidate was issued about two and a half weeks ago. All updates have been applied and I'm not having any major issues. But I'm running the very latest proprietary ATI driver available on this Toshiba (L305D-S5959) laptop. Ubuntu and ATI/AMD worked pretty hard to make this particular combination work. Intel doesn't seem to be nearly as cooperative.

Even though these may not directly be relevant to this situation, see these interesting articles about Intel graphics at phoronix.com:

[http://www.phoronix.com/scan.php?page=news_item&px=ODIwMQ](http://www.phoronix.com/scan.php?page=news_item&px=ODIwMQ)
[http://www.phoronix.com/scan.php?page=news_item&px=NzAyOQ](http://www.phoronix.com/scan.php?page=news_item&px=NzAyOQ)

Sorry.

---

### Post by wford002 on 2010-05-02
> **Rususeruru said:**
> Looks like we were having a the same or similar problems.
Installation took forever on my system (Toshiba NB205)
I successfully install Ubuntu several times but could never boot from the installation.

I just went into my BIOS and changed **SATA Controller Mode** to **Compatibility **from** AHCI** and viola successful boot!

I'm guessing there is a driver for AHCI which may be disabled or not loading at boot before it tries to mount / but this is just conjecture based on a similar problem with Windows installations I've had with these machines.

--EDIT--

Looks like this has been an issue before with Karmic [http://ubuntuforums.org/showthread.php?t=1310496](http://ubuntuforums.org/showthread.php?t=1310496)
Funny 9.10 worked fine on this system without changing SATA settings in BIOS

This worked for me (nb200), thanks. Windows 7 is still booting ok it seems. Is there any downside in leaving it switched in the bios?

---

### Post by eombah on 2010-05-02
I got all installed by first installing Karmic Server 64-bit on raid0, this worked on the second try. Then upgraded to lucid and all is ok.

---

### Post by Rususeruru on 2010-05-03
> **wford002 said:**
> This worked for me (nb200), thanks. Windows 7 is still booting ok it seems. Is there any downside in leaving it switched in the bios?
Your welcome!
There is a downside to leaving it in compatibility mode in theory... from what I've read the drive will use a slightly more power and be slightly slower to respond but from my experience the difference seems to be negligible, after all my nb205 is a netbook. Here is a link if you would like more info:

[AHCI vs IDE – Benchmark & Advantage]("http://expertester.wordpress.com/2008/07/24/ahci-vs-ide-–-benchmark-advantage/")


@djchandler

Thanks for the info.  Grub fortunately doesn't appear to be an issue on my system, still able to boot Win7 or Ubuntu. I had been running 9.10 prior to 10.04 so maybe that's why?  Also the graphics info is good to know.
Btw I read your linked forum post, thanks for the chuckle.  I'm a Wyoming native! :D

---

### Post by weaver4 on 2010-05-03
After reading everything I could find on:  DRDY err and error unc I decided to look more at the hard disk.  I checked the disk with window chkdsk and it found no errors; I then ran "Test Drive" on the SystemRescue disk and it found no errors.  I finally downloaded "seatools for dos" (it is a Seagate drive) and it found an error on the hard-drive and gave me an opportunity to repair it; which I did.

After this repair Ubuntu installed and operated normally!

Strange that neither windows or linux could find the error.

---

### Post by erani on 2010-05-03
The same problem on Asus X50N, but in Bios I can not find where to make changes :(

---

### Post by mutrax on 2010-05-09
> **eombah said:**
> Same problem here, I've spent the whole evening trying to install Lucid in a raid0 configuration with no succes.

I have /dev/md0 mounted on / , /dev/md1 is swap.
When I am dropped in busybox I only see /dev/md1.

Rescue mode allows me to mount /dev/md0 just fine.

-Bart

I'm in the same boat.... Something funny however; When I installed (fresh, nu upgrade) lucid raid1 on existing partitions (previously created in 8.04). No problems. When I do this on virgin drives, trouble start.

> 
3. Install the last LTS (8.04), apply all updates, then perform an upgrade of that installation to 10.04. I have no idea if that will work for you or not.


I guess this will be my next attempt. Create the array in the 8.04 installer, then install lucid.

---

### Post by mutrax on 2010-05-09
> **mutrax said:**
> 
I guess this will be my next attempt. Create the array in the 8.04 installer, then install lucid.

So I confirm doing a simple 8.04 install, wich creates a proper raid array, and then just overwrite the md0 and md1 with lucid's / and swap at the installer does work. Problem must be in the partitioner from lucid!

So for me this workaround solves it.
1 install 8.04 with raid
2 install lucid and overwrite and reformat the md's
3 ....
4 profit!

---

### Post by mperrydotnet on 2010-05-20
There is definitely something wrong with the alternative disks and raid configurations. I have had similar problems with raid1. 

In my case I have two drive sda and sdb. If, for the sake of argument, I create 3 partitions on each drive; say 1g for boot 5g for swap and 10g for raid on each drive.  After I am done with the install, during the install I have sda, sda1, sda2, sda3, sdb, sdb1, sdb2, sdb3, and md0. Post install I have sda1, sda2, sda3, sdb, md0, md0p1, md0p2, md0p3. This is beyond odd.


I like to think I have half a clue. I've set up this type of configuration a million times over. It sounds like your workaround may do the trick, but I'm really comprised of low level packages having such huge bugs.

---

### Post by almigi on 2010-05-21
> **eombah said:**
> Same problem here, I've spent the whole evening trying to install Lucid in a raid0 configuration with no succes.

I have /dev/md0 mounted on / , /dev/md1 is swap.
When I am dropped in busybox I only see /dev/md1.

Rescue mode allows me to mount /dev/md0 just fine.

-Bart

From what I've been reading, the graphic installer has problems "seeing" raid0 setups.  The best solution is to download the alternative installer CD (text installer) as that seems to work fine.

---

### Post by Avatar-IT on 2010-05-28
Same thing here! The first RAID1 10.04 system I setup was an upgrade from 8.04LTS, so I totally missed the problem that time. Today while installing on a new system with RAID1, no joy. Going to partition and format from 8.04LTS cd this time....

Sheesh, what a waste of time...

---

