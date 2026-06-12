---
title: "Can't seem to install ubuntu - monitor sleeping"
date: 2010-11-29
forum: Installation &amp; Upgrades
---

### Post by damon118 on 2010-11-29
Trying to install ubuntu 10.0 and an older 9.something on a desktop of mine. Tried a couple of different things with no luck.

Seems that after getting to "checking battery" part of the installation the monitor just goes to sleep and won't wake. I have tried using the motherboards on board graphics card with the same results. Also tried the nomodeset option, but still the same results.

Desktop was running XP with no problems at all, formatted the drive so I could install ubuntu. So currently no OS on the desktop nor do I have a windows cd anymore to reinstall. 

Install went just fine on my laptop which has a nvidia 9800m gs, so not sure what other options I have.

any ideas?

---

### Post by damon118 on 2010-11-29
bump - No ideas? Or am I just screwed?

---

### Post by AbeJarano on 2010-11-29
Is the CD drive OK?  The CD/DVD (MD5)?  If so simplify the hardware: one drive, one stick memory, no cards if possible.  Set the BIOS to defaults.  If Knoppix boots your hardware should be OK.

---

### Post by damon118 on 2010-11-29
> **AbeJarano said:**
> Is the CD drive OK?  The CD/DVD (MD5)?  If so simplify the hardware: one drive, one stick memory, no cards if possible.  Set the BIOS to defaults.  If Knoppix boots your hardware should be OK.

cd-rom is fine, nothing wrong with it. I get to the screen to choose between installing and running live cd. After I choose to install or run ubuntu live the screen just sleeps and won't wake up.

Running off of the on board video, only has 1 stick of memory, only has 1 hard drive. Only has this problem when trying to install or run ubuntu. 

I don't think it is a hardware problem, Even though both cd's work fine on my laptop I think this is a Ubuntu problem, maybe because of the older video hardware of the desktop or something. 

I see a lot of people having the same problem, but they have another OS to boot up to so they can find work around to the problem.

---

### Post by AbeJarano on 2010-12-02
It's Ubuntu waiting for a device that doesn't respond.  Do the usual; simplify your system hardware.

---

### Post by oldfred on 2010-12-02
I had to do this with my Nvidia 9600GT:
boot from the cd, press F6 and then select the nomodeset option.
I edited my grub.cfg as I use grub to boot ISO, in syslinux.cfg or text.cfg
then
On first boot after install, press e on getting the GRUB bootloader. 
Hold shift from BIOS boot to get menu if only one system installed.
Using arrow keys navigate to and delete quiet and splash and type the word nomodeset in their place
Press Ctrl and X to boot (low graphics mode)

After I installed Nvidia driver (default from pop up) then it has worked without issue.
gksudo nvidia-settings
Or it should be in System>administration>Hardware drivers.
Possible additional things to run once nvidia working:
gksudo nvidia-settings
sudo nvidia-xconfig

---

