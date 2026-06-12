---
title: "Bootmgr error on netbook where windows was completely overwritten?"
date: 2010-09-30
forum: Installation &amp; Upgrades
---

### Post by clv309 on 2010-09-30
Hi all,

I had a clean install of ubuntu going fine (as far as I could tell), then rebooted after the install.

I booted the computer but I keep getting the error message "Bootmrg is missing." I had the unbuntu install over the entire harddrive because I wanted this to be just for linux distros I want to play around with, so while this is a windows error, I don't know how it's appearing.

Is there any way to fix this short of buying an external CD reader (netbook, remember) and going through the usual steps to fix the MBR?

---

### Post by garvinrick4 on 2010-09-30
I do not believe you placed the boot manager grub2 into sda on install if it is missing.
You are on a netbook to replace the bootmanager you need Ubuntu install on a USB flash drive (live ubuntu usb). With a few simple commands you can put grub2 where it belongs.
 In page 8 of installation there is an advanced tab and must open it and select sda and will put grub in mbr of HDD. They are changing installation procedure for Maverick 10.10
  All users with a Netbook should really have a USB install or a USB external Optical drive with their operating systems on cd or dvd no matter what they are using for O.S. Must have some way of fixing a system!

---

### Post by garvinrick4 on 2010-09-30
By the way you can install desktop edition of Ubuntu and then add the netbook GUI.
When you install Netbook edition you get the desktop as selection at log-in. So can
use any USB with Ubuntu on it, not just Netbook.

---

### Post by clv309 on 2010-09-30
I did use a USB to install it. But now it won't read it at all, so I never get an option to enter grub commands. Something similar happened to be before on my actual laptop, but I was able to fix it then. Is there any way to get it to read the USB? It doesn't matter the boot order, it instantly goes to this screen which just says Ctrl Alt Delete to reboot.

How can I get it to go to a screen where I can type in grub commands? I'll have no idea what I'm doing, but I'd try it.

Basically, even if I get an external drive, I don't think I could get the netbook to boot to it anyways.

---

### Post by garvinrick4 on 2010-10-01
The same USB flash drive you used to install with? If Bios set to boot USB first or you can choose which to boot USB or HDD then should go to a window that says Try Ubuntu or install Ubuntu and you choose Try UBuntu. It is booting off of the Flash drive not the hard drive so has nothing to do with anything else. Just make sure it is set to boot off of USB first before HDD.

---

### Post by garvinrick4 on 2010-10-01
Do not forget to save changes in Bios after you set them.

---

### Post by clv309 on 2010-10-01
I've changed the boot order but it still won't read it, that's why this is confusing me so much. I never get a menu to do anything regarding ubuntu.

---

### Post by clv309 on 2010-10-01
I tried all the steps listed here: [https://help.ubuntu.com/community/Grub2#Command%20Line%20and%20Rescue%20Mode](https://help.ubuntu.com/community/Grub2#Command%20Line%20and%20Rescue%20Mode). 

But no such luck. Every combination returns unknown filesystem. I wanted to format the disk using GParted, but as I said before, I can't get anything to boot from USB. =\

---

### Post by clv309 on 2010-10-01
> **clv309 said:**
> I tried all the steps listed here: [https://help.ubuntu.com/community/Grub2#Command%20Line%20and%20Rescue%20Mode](https://help.ubuntu.com/community/Grub2#Command%20Line%20and%20Rescue%20Mode). 

But no such luck. Every combination returns unknown filesystem. I wanted to format the disk using GParted, but as I said before, I can't get anything to boot from USB. =\

Forgot to mention that with very specific steps, it puts me immediately into grub rescue, but the only commands I can use are ls and set, and nothing is working to mount anything.

---

