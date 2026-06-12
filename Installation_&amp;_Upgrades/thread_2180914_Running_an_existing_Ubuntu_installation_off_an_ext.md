---
title: "Running an existing Ubuntu installation off an external harddrive"
date: 2013-10-15
forum: Installation &amp; Upgrades
---

### Post by hin2 on 2013-10-15
I have recently bought a new laptop which comes with Windows 8. I would like to keep Windows 8 as the main operating system on the internal harddrive of this new laptop. I also have an old laptop which runs Ubuntu and I would like to stick its HDD into an external HDD case and boot off that on the new laptop when I want to.

I have had a look at some resources, but most of them are about starting fresh. How do I go about setting up the new laptop to be able to boot from the external HDD (with Ubuntu on it) when I plug it in?

Thanks in advance!

---

### Post by TheFu on 2013-10-15
Almost all new laptops with Win8 will have UEFI, so the booting process is a little different.
There is a good UEFI how-to for Ubuntu. Google will find it. I'd start there. Then I'd try Boot-Repair. If that didn't work, time to dig into grub-install and possibly change the boot drive in the BIOS.

Sorry there isn't a 3-step how-to.  Windows8 has made it much more complicated.

---

### Post by ubfan1 on 2013-10-15
It might be possible to switch to  compatibility mode to boot the external (old) disk, with USB moved to the top of the boot order of course.  Switch back to UEFI mode for booting Windows.  Less work, but less convenient if it even works.

---

### Post by hin2 on 2013-10-15
Thanks for the suggestions. I might start of with ubfan's suggestion, but would that mean that system processes will be using the external HDD? Is there anyway that I can tell it to use the internal HDD for the caching-type processes?

---

### Post by oldfred on 2013-10-15
Ubuntu has read and booted with BIOS from gpt partition drives for many versions. I have used gpt with BIOS boot since 10.10 and had Windows XP on a MBR drive. XP does not read gpt drives but Ubuntu read all drives without issue.
Of course Windows 8 has its always on hibernation or fast boot, so you want to turn that off and not use the c: drive for anything other than Windows 8. Create other data partitions.

You should be able to boot external drive with BIOS/CSM mode, but will have to go into UEFI or maybe one time boot key on reboot to choose a BIOS boot. You cannot easily dual boot one system with BIOS and another with UEFI, but you can dual boot.

---

### Post by hin2 on 2013-10-17
Thanks for you time. The technology has changed a lot since the last time I looked into this kind of stuff and didn't realise all the problems that this is causing with me trying to use some older tech on new computers.

So here's what I grasped from reading around a bit more: It is difficult or impossible to setup dual booting with an UEFI OS and a BIOS and that Ubuntu and Windows don't play nicely together with Intel SRT. Which leads me to my next question: ExpressCache and Intel SRT are two different things, right? My new laptop has 24GB ExpressCache. Are there are settings that I would need so that Ubuntu makes use of the SSD? I don't want to install Ubuntu on the SSD.

Here's the new laptop that I've got: [URL="http://www.samsung.com/uk/consumer/pc-peripherals/notebook-computers/ultra-portable/NP540U3C-A03UK"][http://www.samsung.com/uk/consumer/pc-peripherals/notebook-computers/ultra-portable/NP540U3C-A03UK](http://www.samsung.com/uk/consumer/pc-peripherals/notebook-computers/ultra-portable/NP540U3C-A03UK)
I[/URL]s there any thing else that I should be aware of?

Sorry for the rather open question. Just need to make sure I don't mess things up.

---

### Post by oldfred on 2013-10-17
It looks like ExpressCache is SanDisk's competitor to Intel SRT cache. Not sure if anyone else has installed on a system configured with that. Not idea how it is configured, but unless SanDisk has a driver for Ubuntu I do not think you can use it. 
Anyway its purpose is to speed booting of Windows, so you could not use it in Ubuntu when it has Windows data cached ready for next Windows boot.

Because Intel SRT uses RAID that causes issues on the installer or gparted seeing drives. Does gparted see your drives from the install ok, or is it also an issue with ExpressCache?

You should just install Ubuntu in UEFI mode in new partition(s) on your hard drive to make it easy to dual boot. Once you start down the path of new system with UEFI, it is time to change all drives to gpt partitioning and convert to UEFI booting.
To boot BIOS drive, you have to go into UEFI, turn off UEFI and/or turn on CSM/BIOS/Legacy mode. And then to boot UEFI you have to change settings again. Some systems will boot in either UEFI or BIOS when secure boot is off, not sure if then it will offer to boot in correct mode without changing settings or not. 

UEFI and BIOS are not really compatible, so once booting starts in one mode you cannot switch, so grub will not let you change boot modes to boot anther system.

---

### Post by hin2 on 2013-10-18
Thanks oldfred.

Yeah, after reading around a bit more it was as you expected; there's a dedicated partition on the SSD for windows only. In the end, I think I'll just resort to installing Ubuntu onto the HDD the boring way without all the flashy technology. I suppose they weren't necessary, but would have been nice to have.

Once again, thanks for your help. Much appreciated.

---

