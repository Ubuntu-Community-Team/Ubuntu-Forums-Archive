---
title: "Installing ubuntu without cd or usb"
date: 2017-09-10
forum: Installation &amp; Upgrades
---

### Post by kameni1 on 2017-09-10
Hello, I am trying to install ubuntu 16.10 on my old laptop and i was wondering if there was a way to fully install ubuntu (not dual boot) without a usb or cd

---

### Post by Autodave on 2017-09-10
First off, 16.10 is no longer supported. You should either go with 17.04 or 16.04.

   Every 2 years, a long term service release is made. These LTSs have a service life of 5 years: security and software updates are available for 5 years after the release.  The last LTS was 16.04. 16 stands for the year of the release, 04 stands for the month (April). The next LTS will be 18.04. Releases in the interim will be 6 month releases and only supported until the next release.

I stick with only the LTSs and even then I usually wait a month after their release before installing them. Further, I do not upgrade to them but completely install the new release after copying all files that I need to save to an external HD.

Now to answer your question: no way that I know of. May I ask why you cannot use a USB or DVD?

---

### Post by kameni1 on 2017-09-10
Because the dvd drive rarely works and i have no idea why and i think that the laptop doesn't even support bootable usb drives

---

### Post by deadflowr on 2017-09-10
> **kameni1 said:**
> Hello, I am trying to install ubuntu 16.10 on my old laptop and i was wondering if there was a way to fully install ubuntu (not dual boot) without a usb or cd

Sure.
set up to boot from an iso file from GRUB:
[https://help.ubuntu.com/community/Grub2/ISOBoot]("https://help.ubuntu.com/community/Grub2/ISOBoot")

Ideally, of course, you would set aside a tiny partition (2gb will work) and place the iso image in there.
And then point the grub settings to see that partition.
You would do this so that you do not install to the installer, or else you would overwrite the iso location and eventually the install will fail, because well, the installer would be gone to finish the job.

Post install you can either reset the partition to use (maybe set as swap) or leave it as is for future reinstalls.

Now,
can this be done without grub? (Like directly from a hard drive partition)
I do not know.

---

### Post by kameni1 on 2017-09-23
Thank you for your help but i figured it out. In the end I just used wubi to dual boot it. Unfortunately, ubuntu didn't react how I thought it would. It turns out that windows 7 runs better than ubuntu on my laptop...Dont know why.

---

### Post by mörgæs on 2017-09-23
Here is something you should know about [Wubi]("https://ubuntuforums.org/showthread.php?t=2229766").

Is your DVD drive completely dead or is there some life in it?

---

### Post by Impavidus on 2017-09-23
You may be able to remove the hard drive and connect it to a computer with working bootable dvd/usb. Then use that computer to install Ubuntu on that hard drive and then put it back into the other computer.

Don't install any proprietary drivers before putting the hard drive back. This seems an older computer, so you probably have to install in bios mode and make sure grub is installed to the right drive.

---

### Post by oldfred on 2017-09-23
If computer is so old that it does not boot with USB then it also has little RAM and very old video card/chip.
Ubuntu would be way to large and run very slow on that system.

You need to try Lubuntu, or one of the other lightweight flavors
 Lightweight flavors
Lubuntu, xubuntu, Ubuntu mate, Budgie 
[https://wiki.ubuntu.com/UbuntuFlavors](https://wiki.ubuntu.com/UbuntuFlavors)


 [https://help.ubuntu.com/community/Installation/LowMemorySystems](https://help.ubuntu.com/community/Installation/LowMemorySystems)

---

### Post by efflandt on 2017-09-24
How old is this computer. Any computer from around 2006 or newer should be able to boot from USB and can probably use a 64-bit OS. The most recent computer I had that did could not boot from USB and was 32-bit only was a very low end Compaq laptop from 2005 (Sempron CPU which at that time was 32-bit crippled version of Athlon64). But my HP desktop from 2004 could boot from USB [and was an early Athlon64 3200+ (2.0 GHz)]. A Toshiba laptop I have from 2006 has an Intel CPU that can boot from USB and do 64-bit. If it came with Win7 it should certainly be able to boot from USB, with BIOS setting and may in some cases also require pressing a hot key during boot to select boot device (especially Dell computers) if USB or optical drive (CD/DVD) was not the last thing booted.

---

### Post by r_widell on 2017-09-27
One other thing to try.
Since it's so old that it won't boot from USB, it almost certainly has a floppy.
Look around for a floppy image of Smart Boot Monitor (SBM).
This should enable you to boot from a USB CD/DVD drive, if you can borrow one of those for awhile.

ron

---

### Post by mörgæs on 2017-09-28
If it runs Windows 7 it's probably new enough for USB booting. I would not expect 7 to run on hardware from the floppy era.

---

