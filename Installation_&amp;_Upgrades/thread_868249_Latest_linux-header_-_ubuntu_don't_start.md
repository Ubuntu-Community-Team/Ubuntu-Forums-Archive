---
title: "Latest linux-header - ubuntu don't start"
date: 2008-07-23
forum: Installation &amp; Upgrades
---

### Post by inzaghi89 on 2008-07-23
Today i've update my linux-headers:   linux-headers-2.6.24-20 linux-headers-2.6.24-20-generic
  linux-image-2.6.24-20-generic linux-restricted-modules-2.6.24-20-generic
  linux-ubuntu-modules-2.6.24-20-generic
after that, when i've bootscreen and i've chose Ubuntu 8.04.1, kernel 2.6.24-20-generic nothing happens. Only one what i can see is a text: Starting... and nothing else. On Ubuntu 8.04.1, kernel 2.6.24-19-generic all works fine.

---

### Post by Dark Angel on 2008-07-23
I have the same problem.

Installed update, rebooted as requested ... nothing.  Stops at "Starting Up..."

I tried it in recovery mode and it did get as far as checking the 'hlt' command at which point it ... well ... halts.

I have tried re-downloading the updates and reinstalling everything but no good.

This is the generic kernel on a 32bit AMD XP3000+ with 1Gb or RAM.

My 64bit AMD machine, however, had no problems with it.

---

### Post by Shazaam on 2008-07-23
+1 for me too. It stops at the 'hlt' line. All of my older kernels work so it's not a show stopper for me.

---

### Post by Rogee on 2008-07-23
Same problem here.  My computer will not start, after installing the update.

All I get is "Starting Up..."

This is not good at all.  I have no idea what to do.

---

### Post by Shazaam on 2008-07-23
Hit "esc" at the grub boot menu and choose an older kernel.

---

### Post by steveneddy on 2008-07-23
Is anyone going to list their hardware?

What hardware is this happening on?

---

### Post by Shazaam on 2008-07-23
Soyo KT600 mb
AMD ATHLON XP 3200
2gig ram
2 IDE hd's
1 SATA hd
1 dvdrw
1 cdrw
SoundBlaster Live! 5.1
BFG 7800GS agp video card
onboard nic.
32bit Hardy
Anything else?

---

### Post by Deuce on 2008-07-23
Same issue here, Dell Latitude laptop, Pent3  1 GHZ with 512 ram

---

### Post by nelinata on 2008-07-24
same problem
my hardware: amd athlon 1800+ 
             ram 1g
             nvidia geforce

---

### Post by Polygon on 2008-07-24
Im getting the same problem

please follow this bug report:

[https://bugs.launchpad.net/ubuntu/+bug/251344](https://bugs.launchpad.net/ubuntu/+bug/251344)

---

### Post by Dark Angel on 2008-07-24
> **steveneddy said:**
> Is anyone going to list their hardware?

What hardware is this happening on?

I did, but since that was too general for you my problematic machine's details in depth are:

CPU: AMD Athlon XP 3000+ (running at STOCK SPEED)
Motherboard: A7N8X (latest BIOS, otherwise UNmodified)
RAM: 1Gb DDR333 in dual channel mode (stock timings)
Video: GeForce FX-5200 128Mb DDR RAM
HDD: 40Gb running at ata66
Optical: One(1) only 52x CD-ROM

There is no software on this machine from outside the repositories and none from the backports repositories.

---

### Post by Polygon on 2008-07-24
i highly doubt its related to any specific hardware as 5 people with completely different computers are getting the same thing, im sure its just some error or bug in the kernel that they overlooked.

course it makes me wonder why this wasnt tested before it went out.....

---

### Post by wroobel on 2008-07-24
I have the same problem.

AMD Athlon XP 2200+
ECS L7VTA (KT400)
Nvidia GF6600

---

### Post by PinkFloyd102489 on 2008-07-24
Same just happened to me.

Pentium 3 Katmai 450Mhz
No idea on the mobo, it's an old Gateway computer. I think it's Asus.
Nvidia GeForce 5200FX 256Mb

---

### Post by dragon caiman on 2008-07-24
Same problem:
Compaq Deskpro EN
Pentium III 1GHz
512 MB RAM

Restarted using previous kernel.

---

### Post by commbba on 2008-07-24
Same problem , in me.I pressed ''esc'' and chose an older version and the system booted normally , as normally you can say this action.
My system is an Acer F3000 series (Aspire 1450 platform)laptop with AMD 1800+ ,512 mb RAM , 55 GB HDD , 128 mb Graphic RAM.

---

### Post by inzaghi89 on 2008-07-24
So it isn't only my problem.

I forgot... my pc is:
1gb ddr
gf 6600gt
amd athlon xp 1800+@1540mHz

---

### Post by gcee on 2008-07-24
I just added my 2cents to the bug report as well
amd athlon 2000+
pny verto 6200 vid w/ nvidia drivers
1gb ram

hangs at the checking hlt line

starting grub at previous kernel works

I think I need to remove the newer kernel, anybody done this without ripping the guts out of the system.

this was an upgrade from the latest 710 to 804 via update manager to begin with.

---

### Post by chrisccoulson on 2008-07-24
> **Polygon said:**
> i highly doubt its related to any specific hardware as 5 people with completely different computers are getting the same thing, im sure its just some error or bug in the kernel that they overlooked.

course it makes me wonder why this wasnt tested before it went out.....

This update is currently in the hardy-proposed repository, which is a testing repository for Hardy updates. People using the testing repository should be prepared for some breakage from time to time. If you've got the update, then you have enabled this repository yourself.

This kind of thing is exactly what the '*-proposed' testing repositories are for - to catch problems like this before they are released to the masses. This update has not gone in to hardy-updates or hardy-security yet.

---

### Post by Polygon on 2008-07-24
> **chrisccoulson said:**
> This update is currently in the hardy-proposed repository, which is a testing repository for Hardy updates. People using the testing repository should be prepared for some breakage from time to time. If you've got the update, then you have enabled this repository yourself.

This kind of thing is exactly what the '*-proposed' testing repositories are for - to catch problems like this before they are released to the masses. This update has not gone in to hardy-updates or hardy-security yet.

still. ONE person testing this kernel on their computers before putting it in hardy-proposed would of seen that it doesn't even boot..... it seems to effect everyone no matter their hardware, so either the person testing it didnt experience the bug or they just put updates in hardy-proposed without testing it themselfs...

---

### Post by avtolle on 2008-07-24
On at least one other thread, there are some posting that the new kernel works on their computers. So, I'd think that there had been testing on various boxes, but as the devs likely haven't access to all the possible combinations and permutations of chips, it was then put in proposed for additional testing. 

My thought is to not have the proposed repository enabled, unless the user wants to be involved in the testing process.

---

### Post by hav0x on 2008-07-24
Also got hit by this "bug".

AMD AthlonXP
SiS 735 chipset
NVIDIA Geforce FX


as usual just had to fallback on .19

---

### Post by skankster on 2008-07-24
> **Polygon said:**
> still. ONE person testing this kernel on their computers before putting it in hardy-proposed would of seen that it doesn't even boot..... it seems to effect everyone no matter their hardware, so either the person testing it didnt experience the bug or they just put updates in hardy-proposed without testing it themselfs...

I can boot with it (ASUS laptop), it just breaks my wifi.

---

### Post by chrisccoulson on 2008-07-24
> **Polygon said:**
> still. ONE person testing this kernel on their computers before putting it in hardy-proposed would of seen that it doesn't even boot..... it seems to effect everyone no matter their hardware, so either the person testing it didnt experience the bug or they just put updates in hardy-proposed without testing it themselfs...

Wrong!!!

I am running 2.6.24-20 without a hitch. So it *IS* hardware dependant, and it *isn't* affecting everybody. hardy-proposed is for testing purposes to catch bugs like this before they end up amongst the general user base, and today has demonstrated that this process works well. If you can't handle occasional breakage, you should not be running hardy-proposed.

---

### Post by avtolle on 2008-07-24
> **chrisccoulson said:**
> Wrong!!!

I am running 2.6.24-20 without a hitch. So it *IS* hardware dependant, and it *isn't* affecting everybody. hardy-proposed is for testing purposes to catch bugs like this before they end up amongst the general user base, and today has demonstrated that this process works well. If you can't handle occasional breakage, you should not be running hardy-proposed.
[https://bugs.launchpad.net/ubuntu/+bug/251344](https://bugs.launchpad.net/ubuntu/+bug/251344) indicates that the bug is, indeed, hardware dependent. Many affected are running older CPUs; it seems that those on 64 bit systems haven't had problems (from the limited sample there as well as on the forums).

---

### Post by TorqueyPete on 2008-07-24
I'll join this little gathering of folks with the same problem.
 Kernel -20 freezes on boot even in recovery mode. Reverting to -19 for now.

---

### Post by Aikon- on 2008-07-24
> **chrisccoulson said:**
> Wrong!!!

I am running 2.6.24-20 without a hitch. So it *IS* hardware dependant, and it *isn't* affecting everybody. hardy-proposed is for testing purposes to catch bugs like this before they end up amongst the general user base, and today has demonstrated that this process works well. If you can't handle occasional breakage, you should not be running hardy-proposed.

Wong!!!

No one is saying that they can't handle it.. they are saying that it doesn't work, and if anyone knows if there is a solution for it that would be great. Telling people you tried something (i.e. this new kernel) and that it didn't work is indeed part of the testing process, so lay off, since according to your own statements they are helping.

I also have this problem.

AthlonXP 2500+
Abit NF7-S with nVidia nForce2 Ultra

---

### Post by mistseeker on 2008-07-24
Same problem for me. My system is an Acer Aspire 1355 LC, AMD Athlon XP-M 2,6 , via KM400/KN400 integrated graphics and 1,2 gigs of Ram.

My faith in the open community remains, though. Power to the people!

---

### Post by honeybl on 2008-07-25
Apparently this is a problem with the kernel itself, and not dependent on any hardware configuration. I also upgraded the kernel today and cannot boot past the 'hlt' line. I'm rolling back to a previous kernel and it works just fine.

---

### Post by JoseReyes on 2008-07-25
> **honeybl said:**
> Apparently this is a problem with the kernel itself, and not dependent on any hardware configuration. I also upgraded the kernel today and cannot boot past the 'hlt' line. I'm rolling back to a previous kernel and it works just fine.

Works fine on one of my pc's a 
HP Pavilion a1619h Intel Pentium 4 3.20ghz
1024 Memory
NVIDIA GE Force 8500GT

But on my Intel dualcore 2 Intel 2ghz PC
2gig ram
NVIDIA GE Force 8500GT

I can't get any resolution over 640x480... then when I removed it, and went back to -19 kernel now I have to reload the windows manager everytime I boot the PC... Can't figure out how to fix the having to reloade window manager to get some of the desktop effects... also can't load the nvidia screenlet...

---

### Post by topgi on 2008-07-25
Same problem here: Athlon 2600 running at 2.4GHz, NVIDIA 6800GS, 3 year old motherboard ABIT NFS-7. I have the testing rep on.

---

### Post by chrisccoulson on 2008-07-25
> **Aikon- said:**
> Wong!!!

No one is saying that they can't handle it.. they are saying that it doesn't work, and if anyone knows if there is a solution for it that would be great. Telling people you tried something (i.e. this new kernel) and that it didn't work is indeed part of the testing process, so lay off, since according to your own statements they are helping.

I also have this problem.

AthlonXP 2500+
Abit NF7-S with nVidia nForce2 Ultra

You've taken my post out of context. I was responding specifically to Polygon:
> i highly doubt its related to any specific hardware as 5 people with completely different computers are getting the same thing, im sure its just some error or bug in the kernel that they overlooked.

course it makes me wonder why this wasnt tested before it went out.....
> still. ONE person testing this kernel on their computers before putting it in hardy-proposed would of seen that it doesn't even boot..... it seems to effect everyone no matter their hardware, so either the person testing it didnt experience the bug or they just put updates in hardy-proposed without testing it themselfs...
I got the impression that Polygon didn't understand that this is a proposed package, and that by running the proposed repository, Polygon is testing the package to catch this kind of breakage before it *is* actually released.

Of course, if I'm wrong, then I apologise

---

### Post by SeaJey on 2008-07-25
Same problem with Athlon XP 2500+ nvidia chipset/card
Did a stupid thing - removed all older kernels :(

How can I rollback to older kernel using only latest knoppix livedvd?

---

### Post by chrisccoulson on 2008-07-25
> **SeaJey said:**
> Same problem with Athlon XP 2500+ nvidia chipset/card
Did a stupid thing - removed all older kernels :(

How can I rollback to older kernel using only latest knoppix livedvd?

I'm not sure if the process would be the same as with an Ubuntu CD, but basically you need to boot the live CD, mount your install, chroot in to it and then install a kernel - something like:
```
sudo mkdir /media/target
sudo mount -t ext3 /dev/sdxx /media/target
sudo chroot /media/target
apt-get update
apt-get install linux-generic=2.6.24.19.21
exit
sudo reboot
```
Replace /dev/sdxx with the device node of the partition that your Ubuntu install resides on. If you're unsure, post the output of:
```
fdisk -l
```
from the live CD, and someone here may be able to help

Also bare in mind that if you have a separate /boot partition, you will also need to mount this from the live CD.

---

### Post by LarryEdwards on 2008-07-26
I just installed latest kernel, 2.6.26-ultimate, on my Toshiba laptop and on my wife's HP pavilion ze4500 using kernelcheck.  The upgrades went smoothly.  Both run 8.04 and were sort of ok running kernel 2.6.24-19. 
 
Now the HP has no sound.  The sound was fine with 2.6.24-19.  If I go back to 24-19 the sound is again fine.  But not with 26.  No sound at all.  I guess that somehow the driver didn't make it into the 26 kernel, right?  I don't know what the card and chipset are.  How do I find out that?  Suggestions?

My Toshiba will not boot with kernel 26, either normal or in protected mode.  I want to upgrade because I believe/hope that kernel 26 has a native driver for my Realtek wireless card.  Now I am without wireless and still running kernel 24.  Any help would be appreciated.
Thanks.

---

### Post by texhead on 2008-07-27
> **TorqueyPete said:**
> I'll join this little gathering of folks with the same problem.
 Kernel -20 freezes on boot even in recovery mode. Reverting to -19 for now.

Ditto :( back I go...

---

### Post by richardh9936 on 2008-08-01
Me too. AMD Sempron 2300 Nvidia Geforce.
I've lodged my hardware test with Launchpad.

---

### Post by richardh9936 on 2008-08-02
I've skimmed the bug report, and I can see our technical experts are working hard.  I'll be patient while they work it out.

---

