---
title: "FakeRAID on 8.04"
date: 2008-05-01
forum: Installation &amp; Upgrades
---

### Post by Siyfion on 2008-05-01
Has anyone else had any problems installing 8.04 from fresh on a fakeRAID? As I can't seem to get mine to install no matter WHAT I try!

Raid support in Ubuntu REALLY need's some work, we are so so so far behind Fedora in terms of RAID ease of install. If they can do it, we can! :(

---

### Post by Jens7677 on 2008-05-01
What problems do you have?

I'm already stuck at setting up dmraid :(
([http://ubuntuforums.org/showthread.php?t=777471](http://ubuntuforums.org/showthread.php?t=777471))

---

### Post by Siyfion on 2008-05-01
Well I can get wayyy past that, after installing dmraid and setting up the partitions and even formatting them, I can't get GRUB to install using the old method. Seems some of the directories have changed?

Where are you stuck? Maybe I can help you at least!?

---

### Post by Jens7677 on 2008-05-01
see the thread I'm refering to. The physical capacities of my harddisks are read wrong. When I try do dmraid -ay I got a device mapper error. See:
[https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.22/+bug/141435](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.22/+bug/141435)

I know now that I don't have to rebuild my kernel to get hpa honored, but don't know how to teach the live cd to accept kernel module parameters to get access to my disks again.

Where are you stuck exactly? My Ubuntu Gutsy run perfectly well with dmraid. 

Regards,
Jens

---

### Post by deepc2006 on 2008-05-01
I did an debootstrap Installation with dmraid and lvm, following [http://www.realriot.de/index.php/2007/04/25/fakeraid-howto-ubuntu/](http://www.realriot.de/index.php/2007/04/25/fakeraid-howto-ubuntu/) and [http://www.ubuntu-forum.de/artikel/32723/grub-konfiguration-auf-fakeraid-0-will-nicht-oder-liegts-nicht-am-raid.html](http://www.ubuntu-forum.de/artikel/32723/grub-konfiguration-auf-fakeraid-0-will-nicht-oder-liegts-nicht-am-raid.html) and [http://ubuntuforums.org/showthread.php?t=630644&highlight=lvm+dmraid](http://ubuntuforums.org/showthread.php?t=630644&highlight=lvm+dmraid).

I used the Live CD and installed dmraid, lvm and debootstrap
With fdisk i was able to partition my fakeraid
Then after reboot i created a lv and mounted it.
with debootstrap i did a standard install, and added dmraid and lvm.
After grub install i booted the system.

Now i have following errors:

At "Setting up dmraid devices ..."
i get
"device-mapper: table: 254:1: mirror: device lookup failed
...
xfs internal error ...

and then a lot of input/output errors.
It seams to be an error in initramfs.
My fakeraid isn't initialized at boottime.

---

### Post by Siyfion on 2008-05-01
Hmmm can't say I know the answer to either of those problems.. 

Im trying to use this post to wade through it as I did with Gutsy: 
[http://ubuntuforums.org/showthread.php?t=630644](http://ubuntuforums.org/showthread.php?t=630644)

But some of the "Installing Grub" section no longer works properly. :(

---

### Post by Jens7677 on 2008-05-02
At least I found a solution for my problem, see
[http://ubuntuforums.org/showthread.php?p=4859992](http://ubuntuforums.org/showthread.php?p=4859992)

I'll report back what I found during the installation process..

---

### Post by finite9 on 2008-05-02
You used the LiveCD??

I was under the impression that RAID and lvm were only supported on the alternate CD.  I use lvm and dmcrypt and I used the alternate CD for installing 8.04.

Grub 0.97 does not have support for lvm.  Only the dev version 2.x has support for this.

---

### Post by Siyfion on 2008-05-02
Doesn't seem to matter which CD I use, neither recognise the array.. So I may as well have a nice graphical front end to set it all up on! :D

---

### Post by Siyfion on 2008-05-02
And then get seemingly nowhere. :(

It really sucks, because I have two drives in a RAID 1, which MUST be kept safe, and two in a RAID 0. If it weren't for the RAID 1 drive i'd happily un-RAID the other just to install ubuntu! But alas! :(

---

### Post by Jens7677 on 2008-05-02
I don't use lvm or any other raid manager. Just dmraid to get my existing fakeraid discovered. I'm now able to boot the live cd with the libata option, setting up dmraid and mounting my existing partitions.

See: [http://ubuntuforums.org/showthread.php?t=630644&highlight=gutsy+dmraid+how+to](http://ubuntuforums.org/showthread.php?t=630644&highlight=gutsy+dmraid+how+to)

---

### Post by Siyfion on 2008-05-02
Ok so once you have dmraid installed.. what else different from a "normal" install do you have to do?

---

### Post by Jens7677 on 2008-05-03
Ok, finally I got everything up en running again. The former upgrade to ubuntu 8 broke my installation and I thought I had to reinstall everything again, but with mounting my existing partition and with chroot I could fix everything that was wrong (grubs menu.lst was not complete and update-initramfs helps to). So my Ubuntu 8 now lives and works on fakeraid/dmraid partitions.

What do you mean with "normal" installation? I guess you can follow the tutorials for gutsy to get it installed. But I can't say for certain because I could skip several steps because of my previous installation.

This is the tutorial I used for installing gutsy:
[http://backports.ubuntuforums.com/showthread.php?t=464758](http://backports.ubuntuforums.com/showthread.php?t=464758)

---

### Post by Siyfion on 2008-05-03
A normal installation being one where you simplyu use the default installer application to set up partitions and drives, and grub. :)

---

### Post by Jens7677 on 2008-05-03
According to an earlier posting of you it seems like you already got access to your partitions and got the installation fine, but stumbled somewhere at setting up grub after chroot in your target. I'm pretty sure that this is the right way to do, but I cant help you there because I didn't had to do that step again, because grub was already set up fine at the time when I installed gutsy on my partition.

---

### Post by ViRMiN on 2008-05-03
I'm running it on RAID0, installed using this HowTo:

[https://help.ubuntu.com/community/FakeRaidHowto](https://help.ubuntu.com/community/FakeRaidHowto)

---

### Post by Siyfion on 2008-05-03
I'll give that method a go now then :D

---

### Post by ViRMiN on 2008-05-07
Just wondering how you got on?

---

### Post by Siyfion on 2008-05-07
Didn't work, I ended up using the method I linked to first, just had to install dmraid as chroot and it worked! :D

---

### Post by Cerin on 2008-05-30
> **Global_Inferno said:**
> Has anyone else had any problems installing 8.04 from fresh on a fakeRAID? As I can't seem to get mine to install no matter WHAT I try!

Raid support in Ubuntu REALLY need's some work, we are so so so far behind Fedora in terms of RAID ease of install. If they can do it, we can! :(

Sadly yes. I've wasted a whole day trying to get any sort of RAID-1 working on a fresh install of 8.04, and it's simply not happening. I couldn't even find any option to do RAID in the installer. I tried the "alternate install CD", but that just blew-up in my face with the error "Kernel panic: linux-generic". I'm not a huge fan of Fedora's installer, but I managed to setup a basic RAID-1 in the last three releases. This is my first try with Ubuntu and it's a complete nightmare.

---

### Post by ViRMiN on 2008-05-30
> **Cerin said:**
> Sadly yes. I've wasted a whole day trying to get any sort of RAID-1 working on a fresh install of 8.04, and it's simply not happening. I couldn't even find any option to do RAID in the installer. I tried the "alternate install CD", but that just blew-up in my face with the error "Kernel panic: linux-generic". I'm not a huge fan of Fedora's installer, but I managed to setup a basic RAID-1 in the last three releases. This is my first try with Ubuntu and it's a complete nightmare.

I have a RAID-0 workng with 8.04 but, it's a manual install via the live CD :)

---

### Post by Siyfion on 2008-05-31
Even when I did finally get the RAID working, it wasn't as intended, and I had loads of problems with random non-mountable drives appearing, etc.. In the end I got so fed up with it I went back to Vista! (Now that IS desperate!)

---

### Post by Cerin on 2008-05-31
> **Global_Inferno said:**
> Even when I did finally get the RAID working, it wasn't as intended, and I had loads of problems with random non-mountable drives appearing, etc.. In the end I got so fed up with it I went back to Vista! (Now that IS desperate!)

Yeah, I wasted my entire Friday trying to fix this mess. Then I found that this bug was reported in launchpad...back in January! Moreover, it was deemed not worth fixing! I'm giving up on Ubuntu for a couple years until it gets its act together. I'm not wild about Fedora, but I never had these many problems just trying to get a basic install working. This kind of crap has really given me a loathing for Linux evangelicals.

---

