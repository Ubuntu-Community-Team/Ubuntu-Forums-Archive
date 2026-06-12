---
title: "Installed, though grub stage1.5Read Error"
date: 2007-03-05
forum: Installation &amp; Upgrades
---

### Post by Iorionix on 2007-03-05
I installed Ubuntu 6.10 today, though I get an error after rebooting. Grub will display, "GRUB Loading stage1.5Read Error. I wiped the drive on installing, and let the installer specify the partition settings for the 160gb hd. 

Tried to reinstall grub using the following commands I found in a tutorial on the forums to reinstall grub.

sudo grub

find /boot/grub/stage1
(hd0,0)
root (hd0,0)
setup(hd0,0)
quit

and still get the stage1.5Read error.

Any help is appreciated.

---

### Post by yabbadabbadont on 2007-03-05
setup(hd0,0)

Should be

setup (hd0)

If you want grub to be your main bootloader.  (you do if Ubuntu is the only thing on your drive)

---

### Post by Iorionix on 2007-03-05
tried reinstall of grub with setup (hd0) instead. Same error as before. 

(ubuntu is the only os on the hard drive)

---

### Post by yabbadabbadont on 2007-03-05
Is the only harddrive in the box SATA?  Also, what is the error number that Grub reports?

---

### Post by Iorionix on 2007-03-06
The drive is an IDE drive, their was a SATA drive in the box before. Though that drive is no longer in the box.

I don't see a error number printed on the screen, it just starts to load. Then...

stage1.5Read Error

---

### Post by CountSessine on 2007-11-29
This is exactly what I'm seeing right now, with Feisty server. I install the OS on the hardrive, I reboot it for the first time, and I get "GRUB Loading stage1.5Read Error". I've had feisty on this machine before - nothing had changed. I rebooted a few days ago  and it gave me that error message. I thought my HD was corrupt so I reintalled the OS, but I still get that error message.

I'm really stuck here. There's just basically nothing that can be done. I don't have any logs to read through and I've tried everything I can think of. Can anyone think of a way to diagnose this? Is there anything I can turn on in GRUB? Any kind of debugging output? 

The system in question:

AMD Athlon XP 2500+
Asus A7V8X-MW SE v1.03 (KM400/A chipset)
1GB RAM
Samsung Series P 250GB PATA hard drive

It's never been within 100 feet of a SATA drive

---

### Post by CountSessine on 2007-12-01
> **CountSessine said:**
> This is exactly what I'm seeing right now, with Feisty server. I install the OS on the hardrive, I reboot it for the first time, and I get "GRUB Loading stage1.5Read Error". I've had feisty on this machine before - nothing had changed. I rebooted a few days ago  and it gave me that error message. I thought my HD was corrupt so I reintalled the OS, but I still get that error message.

I'm really stuck here. There's just basically nothing that can be done. I don't have any logs to read through and I've tried everything I can think of. Can anyone think of a way to diagnose this? Is there anything I can turn on in GRUB? Any kind of debugging output? 

The system in question:

AMD Athlon XP 2500+
Asus A7V8X-MW SE v1.03 (KM400/A chipset)
1GB RAM
Samsung Series P 250GB PATA hard drive

It's never been within 100 feet of a SATA drive

So, this gets ever more interesting. I've found that there's a setting in my CMOS that turns off IDE DMA - "IDE DMA transfer access" that seems to get disabled for some reason. When I enable it then I can successfully boot ubuntu, but when I reboot the machine, the setting (and only that setting - everything else in the CMOS is OK) gets disabled and I get the "GRUB Loading stage1.5Read Error" message and a halted boot. 

1. Why would a CMOS setting make any difference if the OS doesn't look at those settings, and
2. Why does that setting keep getting disabled? Does Ubuntu play around with it? Is there a way to check the settings outside of the CMOS set up utility? I'd like to print out the values during the boot process to see if anything is toying around with it...

---

