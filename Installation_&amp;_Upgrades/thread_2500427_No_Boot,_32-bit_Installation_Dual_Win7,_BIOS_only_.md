---
title: "No Boot, 32-bit Installation Dual Win7, BIOS only No UEFI"
date: 2024-09-01
forum: Installation &amp; Upgrades
---

### Post by sorozon on 2024-09-01
I've searched other posts and nothing fixes my problem.
I'm installing on a Win7 32-bit old ThinkPad. I picked up the last 32-bit install, gen 16. USB boot. The installer runs, and the OS files are in the appropriate hard drive petition, but I can't boot into Ubuntu.

The bios is no longer supported by Lenovo, and the menu has no boot from Ubuntu option. I can't access grub.

I've tried many of these steps: [https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

When I run the install code for the boot-repair, there is a message about a file missing. This seems like a dead end.

Do I need an even earlier version of Ubuntu? Maybe one that works without UEFI? Is that why the boot repair won't work, because the system is too old? Otherwise, if everything should be working, why don't the boot-repair steps listed above seem to work?

---

### Post by ubfan1 on 2024-09-01
What model ThinkPad? Just because Win 7 is 32bit installed in legacy mode doesn't mean the machine is not 64 bit capable and UEFI (maybe pre-secure boot.  An old W520 Thinkpad ran for 
years with the oringinal hdd as legacy (Win7 to Win 8 to Win 10) but with a second sdd in a disk caddy (replace the DVD) which booted 64 bit UEFI and ran Ubuntu 22.04.  I eventually did change the internal disk to gpt, but had to reinstall Windows -- the Ubuntu partitions survived intact.

---

### Post by ajgreeny on 2024-09-01
32 bit installation? Is the computer a 32 bit machine or can it run 64-bit OSs?

What version are you trying to install as the last 32 bit systems of any of the 'buntus was in 2018, all now EOL unless you have registered for Ubuntu-pro which can give up to 10 years support

---

### Post by ubfan1 on 2024-09-01
Lenovo still has downloads for many old laptops that they originally delivered with 32 bit win 7 (like the w520).  The gotcha is that Lenovo decided that they would only consider 32 bit users when making firmware changes.  Not that Ubuntu cares, but Windows devices got squeezed when Lenovo decided to give the (mostly non existent (you seem to be one)) 32 bit users more memory, and raised the TOLUD (Top of Lower Usable DRAM). A 64 bit Win install may not have enough device space for a large video card. Check the release notes before applying the firmware patches if you intend to be running Win 64.  I had stopped patches at 1.42 for the W520, later patches up to 1.46 seemed to have the TOLUD problem.  Workarounds are possible, but more effort than I wanted.

---

### Post by sorozon on 2024-09-02
I'm trying to install 16.04.6 which I think is the last 32-bit install. The 20.xx install even the 18 was crashing in the installer, which is why I switched. I do in fact have 32-bit windows 7 installed. 

Lenovo definitely does not support firmware drivers for this model anymore. It's the X200 tablet. I don't need Windows anymore, but I want to dual install because I don't want to brick the device if I can't get Ubuntu working. Maybe I should just go ahead and wipe Windows since that would at least bypass the boot issue.

Still, in the BIOS menu there's no sign of booting from Ubuntu in spite of the OS files present in the disk partition after install. Can't get to grub for the life of me and the boot repair process leads to some sort of message about file not found in the terminal.

Here are the system specs:
Intel Core2 Dduo 19600 @ 2.13GHz
2 gig ram
32-bit

At least, the pen and tablet input from wacom actually work when running Ubuntu from the boot disk (USB) which is sort of cool.

Most advice I read suggests messing with UEFI settings or using grub, finally boot repair. None of which works. The install completed, but I can only access Ubuntu by booting from USB.

I feel like there's something specific I need to do, maybe install an earlier version of Ubuntu that would word with legacy boot specifically. Or boot to Ubuntu from the install disk and set legacy boot in there or something.

For 20.x install, there were suggestions to update the bios firmware, but again, I can't find the driver online and Lenovo doesn't support.

I could be okay with losing Windows, but I don't want to reinstall a 64-bit windows or anything like that.

---

### Post by sorozon on 2024-09-02
I want to use Ubuntu mostly to play around with it, but I also want to use the word processor. That's literally it. I don't need a humming machine, just want the install to actually hold. I'm fine using unsupported versions.

---

### Post by yancek on 2024-09-02
There is no point in post a link to the boot repair download site.  The purpose is to run the software with the Create BootInfo Summary option and post a link here to the output so members have access to the information to help you.  If you try running it and have problems, post any messages you get so we know what is happening.

If you have a Legacy systems booting from the MBR, you can only have code for one OS there so if you have windows code then it won't boot Ubuntu whereas the reverse will work.  There are convoluted methods of booting Linux from older Legacy installs of windows.

Is your computer capable of running a 64bit OS?  Do you see any reference to UEFI in the BIOS of the computer?

---

### Post by oldfred on 2024-09-02
Google says this about your model, is it correct?
Intel Core 2 Duo P8600 2 x 2.4 GHz (Intel Core 2 Duo)

If so then it is 64 bit, but only old BIOS mode support.
Also then how much RAM?

My 2006 laptop with older Core2 Duo would not boot Ubuntu. It only has 1.5GB of RAM and if using more than one larger app, would use swap. Old slow HDD made for 2 sec pause/gray screen when going to swap. Found external SSD with Kubuntu was then very functional and occasional swap was also so fast I barely noticed. But still tried to only load one larger app at a time.

I was able to install server & lightweight gui. But then tried Kubuntu which I was suprised worked. 
Kubuntu is more a mid-weight flavor.

[https://ubuntu.com/download/flavours](https://ubuntu.com/download/flavours)
Light weight flavors:
Lubuntu, Xubuntu, Ubuntu MATE, Budgie
Flavors of Ubuntu only come with three years of supported life (five years applies to Ubuntu Desktop, Ubuntu Server but not flavors)

---

### Post by him610 on 2024-09-04
FWIW, Debian has recent 32bit downloadable distributions, [https://www.debian.org/distrib/]("https://www.debian.org/distrib/") 

There is talk that this may be the last 32bit Debian release. 
I think I had rather have a recent Debian release than a six year old Ubuntu release.

---

### Post by sorozon on 2024-09-30
Thanks all, will try some of this.

---

### Post by guiverc on 2024-09-30
Ubuntu 16.04 LTS wasn't the last 32-bit available; I have older devices that ran pentium M that were used in *Quality Assurance* testing of *disco* or what became Lubuntu 19.04; though no *official* ISOs were released; but if one of the 19.04 32-bit ISOs was used for install, upgrades were available for the life of Ubuntu 19.04.

However, the last *supported* release of Ubuntu that provided support for *i386* or 32-bit x86 was Ubuntu 18.04 LTS; as later 18.10/19.04 weren't LTS and thus ended life well before 18.04.  The last *i386* ISOs were released in [August 2020]([https://fridge.ubuntu.com/2020/08/14/ubuntu-18-04-5-lts-released/](https://fridge.ubuntu.com/2020/08/14/ubuntu-18-04-5-lts-released/)) *at least for flavors.*

There were *fewer* ISOs available for *i386* or x86 32-bit after Ubuntu 17.04; but fewer install ISOs doesn't relate to support; *i386* ISOs were still available even with [18.04.6]("https://fridge.ubuntu.com/2021/09/17/ubuntu-18-04-6-lts-released/") which was released in September 2021.

32-bit windows was sold on computers because it was $5 cheaper than the 64-bit version; and most buyers of devices understood $5 far more than 32bit versus 64bit, especially since both ran the same programs & the machine came with the same amount of disk/RAM etc..

The only LAST ISO at 16.04 was it was the last release that include 32-bit POWER PC (*ppc*) ISOs for *flavors*, but they won' to run on an intel core2duo CPU.

If your machine was 32-bit intel (a 2002 or 2003 pentium M for example) I'd suggest running Debian, as only 32-bit ARM is still supported by Ubuntu; but Intel Core2Duo CPUs were *amd64* or 64-bit capable.

Devices I use in *Quality Assurance* testing of Lubuntu include
- hp dc7900 (c2d-e8400, 4gb, intel 4 series integrated i915)
- hp dc7700 (c2d-e6230, 7gb, amd/ati rv610/radeon hd2400 pro/xt)
- dell [optiplex] 755 (c2d-e6850, 5gb, amd/ati radeon rv516/x1300/x1550)
- dell [optiplex] 755 (c2d-e8300, 8gb, amd/ati radeon rv610/radeon hd2400 pro/xt)

which are all c2d, and they run all releases up to the *unreleased* 24.10.

Some lenovo's I have are
- lenovo thinkpad sl510 (c2d-t6570, 2gb, i915)
- lenovo thinkpad x201 (i5-m520, 4gb, i915)
- lenovo g560 (i5m-480, 4gb, i915)

and again they run all releases (*up to 24.10*).

---

### Post by sorozon on 2024-11-17
Thanks all. I finally backed up my files from Windows and installed the 32 bit (deprecated) Ubuntu without doing a disk partition. It does seem the problem was that my version of windows didn't support dual boot. Wiping Windows allowed the 32-bit installation to work fine and I'm good to go!

Still not sure why the most recent Ubuntu crashed on installation, but with the last 32 bit version on full install everything worked great.

---

