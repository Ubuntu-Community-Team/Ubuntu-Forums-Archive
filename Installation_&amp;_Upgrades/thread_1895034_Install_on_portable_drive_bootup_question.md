---
title: "Install on portable drive bootup question"
date: 2011-12-13
forum: Installation &amp; Upgrades
---

### Post by Dragonbite on 2011-12-13
I have an external hard drive and a Dell laptop running Windows 7 (Home).  I was going to install (via LiveUSB) onto the external hard drive but I need to know something first.

I want it so that when the external drive is plugged in, either the BIOS says to boot to it first, or I manually tell it to boot from it each time.

If the external drive is NOT plugged in, I want Windows to boot as if the external drive has never existed and give no indication that anything has happened to it.

I was going to try and unplugged the laptop's hard drive so the system would not even know it exists and cannot do anything to the hard drive. Unfortunately it isn't under the panel I thought it was and am afraid it is deeper down than I am curently comfortable with cracking. (only because it's a new machine).

How can I make sure the MBR and the Windows boot internal hard drive does not get messed up by installing Ubuntu on the external hard drive?

I understand about the alternatives (VM, dual boot, etc.) but that is not what I am asking about at this time.

---

### Post by fantab on 2011-12-13
> **Dragonbite said:**
> I have an external hard drive and a Dell laptop running Windows 7 (Home).

I want it so that when the external drive is plugged in, either the BIOS says to boot to it first, or I manually tell it to boot from it each time.

If the external drive is NOT plugged in, I want Windows to boot as if the external drive has never existed and give no indication that anything has happened to it.

How can I make sure the MBR and the Windows boot internal hard drive does not get messed up by installing Ubuntu on the external hard drive?

Well, 

[LIST=1]
[*]You will have to **install GRUB on your EXHDD** (/dev/sdb, assuming). This will not then mess with your Windows Boot-Loader on /dev/sda.
[*]You Must **set the BIOS to boot USB Devices First**. This will ensure that when EXHDD is plugged as USB at boot it will Boot First. And when it is not plugged in the Internal HDD with Windows will boot.
[/LIST]
See this [**webpage**]("http://members.iinet.net.au/%7Eherman546/p24.html") for more info.

---

### Post by Dragonbite on 2011-12-14
Ok, that did it well enough.  I was just nervous with not wanting to mess up Windows.  As I work with Windows, I realize that with my years of using Linux, I am unfamiliar with how to set things up in Windows.

Now all I need to do is figure out how to set Grub to automatically boot to Ubuntu without popping up that menu and wait for any time.

See, the system is set to boot to the hard disk FIRST, so that not only is no time wasted looking for other devices, but if I (or somebody nefarious) leave a CD in the disk drive it doesn't automatically boot up into it, or a USB when plugged in.

If I consciously want to boot up to another device, I hit F12 and select the device then.

But at least I was able to boot into Windows by not touching anything during bootup, and I was able to boot into the external drive using F12 and selecting it (then the menu came up).

So thanks for the info!  I thought it would work like that, but seeing somebody else saying it too was a comfort.

---

