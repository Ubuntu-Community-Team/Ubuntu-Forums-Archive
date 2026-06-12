---
title: "Unable to start or install"
date: 2006-10-30
forum: Installation &amp; Upgrades
---

### Post by smiley505 on 2006-10-30
I just put together my first 'build-your-own' computer.  And I was hoping to abandon Windows on the deserted island it deserves to be left...but I can't until I get Ubuntu running.

I burned my own CD of Dapper Drake (several actually, with multiple programs at the LOWEST speed).  It loads just fine to the install menu.  I choose 'Start or Install Ubuntu'.  In the background a screen that says:

<code>
Uncompressing Linux... Ok, booting the kernel.
[17179571.484000] PCI: Faild to allocate mem resource #6:20000@50000000 for 0000:01:00.0
</code>

That is replaced after about half a second by the regular Ubuntu loading screen (my University uses Ubuntu, so I'm used to the graphic).  It gets to 'Mounting root file system' and sits for about 20 seconds.  Then that loading screen goes away and brings me back the the above-described screen...where it sits (and will overnight and longer).  

I've tried all the different boot options detailed in other threads, as well as not using any USB anything.  I haven't seen anything about this particular situation...so I was hoping I could get some help on what to do from here.

If it helps...here's my setup:

Core 2 Duo E6400
Intel DP965LT Motherboard
G. Skill 1GB 240-pin DD2RAM [DDR2 800]
Western Digital SE16 320GB 7200RPM SATA 3.0Gb/s
e-GeForce 7300GT video card

Any help would be GREATLY appreciated.

KDW

---

### Post by catlett on 2006-10-31
Has your system booted anything yet? Can you boot an Ubuntu live cd or any linux live cd?
Is your hard drive formatted yet? Are you using the live cd install or the alternate install cd ? You may have better luck with the alternate install cd because it doesn't need to start an x session just to install the operating system, it just runs a text based installer. This may not change anything but it may be the issue is Ubuntu creating the live session and by not having to create it with the alternate install cd, it may work.
I am not certain if the alternate install cd will make a difference but it may be worth a shot.

---

### Post by smiley505 on 2006-10-31
Well...I got past that screen with the alternate CD.  And now, we're at the problem that was probably at fault to begin with.  During the install, it can not find the CD-ROM.  And, I have no floppy with a driver.  It's an OEM Sony DVD/CD combo drive (Sony model DWQ120AB2), which conveniently doesn't have a driver on the Sony website.  Any ideas?

On a separate note, how is it possible that the CD- ROM can not be found if the installer was booted FROM the CD to begin with?

---

### Post by pierce. on 2006-10-31
I have had this same problem with very similar hardware. It's a problem with ICH8 support in dapper and edgy. I've tried installing from USB stick (to no avail), and from USB cdrom drive (also didn't work). At this point I am just waiting it out for at least one distro to support my hardware.

---

### Post by smiley505 on 2006-11-02
Is this really what we're left to?  I don't want to have to resort back to MS.  Ubuntu doesn't work.  Debian doesn't work.  Mandrake doesn't work.  All because they can't mount a cd-rom (apparantly).  

Anybody???

KDW

---

### Post by flashpoint on 2006-12-05
I have very similar hardware and I too am experiencing the same problem:

Core 2 Duo E6400
Intel DP965LT Motherboard
2GB DDR2 667
Western Digital 500GB SATA 
ATI Radeon X800GT video card

The live disk is getting the PCI problem also and the root filesystem does not mount (ramdisk).  It stops at a (initramfs) prompt.  That is with the 64 bit version of Edgy. The 32 bit also has a similar problem. There is no where to go from that point.

I have just downloaded the 64 bit alternate ISO so that is next on my list to try.

Surely this isn't a problem with every Linux Distro??? If anyone has had any success with this type of hardware, I would really like to know what magic they used to make it happen.

---

### Post by tomwhipple on 2006-12-17
I have the same ptoblem with the DP965LT mainboard. I managed to get a system installed via network boot, but it was a HUGE hassle. I still don't have a working CD/DVD drive, even after upgrading to 2.6.19.1 and trying various modules and kernel options. 

I think Intel really dropped the ball with this board. They have a lot of pull with some of the distros and I am very disappointed that it doesn't work yet.

---

### Post by bradps on 2007-01-11
Hi,

I have a DP965LT motherboard as well and have experienced the same problems I see in this forum regarding the CD/DVD RW visibility after booting. It is a chipset problem. A workaround that I found works somewhat is a 2 step process as follows:

1. In the bios (I flashed mine to 1612 latest rev with MQ96510J.86A.1612.EB.EXE).
    SET or verify the ATA/IDE Configuration to LEGACY as opposed to NATIVE.

2. On bootup of the install CD (fedora core 6 in my case) at the boot prompt, 

type "linux text all-generic-ide" without the quotes of course.

Then proceed to do a typical text install.

Note that what was seen prior as /dev/sda, /dev/sda1, /dev/sda2 ... will now show up as /dev/hda /dev/hda1 and so on. Kind of un-nerving yes. You should be able to see and mount the install media in your dvd/cdrom drive. Try using "dmesg |grep hd" to find it. Again without the quotes. I think mine showed up as /dev/hdi for example. Good Luck!

Cheers - Brad

---

### Post by bcouturi on 2007-01-18
Hi,

What's the kernel version on the Fedora Core 6 installer?

I have bought a DP965LT and a Core 2 Duo E6400, and tried the trick you mentioned with the Edgy Eft alternate installer, but it looks like the kernel (2.6.17-10-generic) does not recognise the DVD drive:

lspci says:
 IDE interface: Marvell Re=Technology Group Ltd. Unknown device 6101 (rev b1)

Cheers
Ben

---

### Post by bradps on 2007-01-23
> **bcouturi said:**
> Hi,

What's the kernel version on the Fedora Core 6 installer? Installer was 2.6.18-1.2869.fc6 and I'm running 2.6.19-1.2895.fc6 currently.

Dual booting WinXP and Fc6 with grub and passing the all-generic-ide param in grub. WinXP is on a SATA drive hda and Fc6 is on a second SATA drive hdc. Using e6600 conroe cpu on the DP965LT Intel mobo.

Maybe a newer kernel will help. I know that 2.6.18 got more support for the Marvel and SATA stuff but still not quite all the way there yet.

Good Luck - Brad

I have bought a DP965LT and a Core 2 Duo E6400, and tried the trick you mentioned with the Edgy Eft alternate installer, but it looks like the kernel (2.6.17-10-generic) does not recognise the DVD drive:

lspci says:
 IDE interface: Marvell Re=Technology Group Ltd. Unknown device 6101 (rev b1)

Cheers
Ben

This is a few more characters ... okay?

---

### Post by bradps on 2007-01-23
Ben,

This was essential before I could see my cd/dvd drive even with the all-generic-ide parameter passed to the installer (dvd in my case)  at boot time.

[B]1. In the bios (I flashed mine to 1612 latest rev with MQ96510J.86A.1612.EB.EXE).
SET or verify the ATA/IDE Configuration to LEGACY as opposed to NATIVE.
[/B]
It was in my first post. The bios setting had to be at LEGACY instead of NATIVE in order to mount the dvd/cd after it booted. I could not see or mount it without making the bios change on the DP965LT mobo.

Once I got past that point I was able to install Fc6. Please note that I checked and the kernel version on my install dvd was 2.6.18-1.2798.fc6 and not as I earlier reported.

Regards - Brad

---

