---
title: "Ubuntu freeze at startup - lubuntu 13.10"
date: 2013-11-19
forum: Installation &amp; Upgrades
---

### Post by istvan3 on 2013-11-19
I have a dual boot with Windows 8.1. I am using GRUB menu. 
Since about a week, my Lubuntu freeze at startup (NumLock key don't react).
I thought, maybe has to do with Windows itself, so I logged in in Windows, and back to Lubuntu.
But still, freezing happened every second time.

Now, today, I tried to start Lubuntu 3 times. Don't work. NumLock  key don't react.

What I did recently:
- I upgraded motherboard Firmware  
- Grub Menu was broken so I had to repair it, with boot-repair.

I also did the latest Ubuntu updates, but did not help.
I did not have this kind of problems with Lubuntu 13.04


Now I can get to the "recovery mode" menu.


Can you help me? Which step I have to do?


"recovery mode" now also don't work. It freeze at "init ramdisk"...

---

### Post by istvan3 on 2013-11-19
Fixed.

I booted from Ubuntu 13.10 Live CD. I could see all partitions with all data, even Windows partition.

I again, installed "boot-repair" and started it. Now, Ubuntu is not freezing at startup.

---

### Post by istvan3 on 2013-11-21
2 times startup worked, then 2 times same problem again. 
I changed in BIOS the "secure boot" to "disabled". Not it works.. maybe this was the problem.. Let' see..

---

### Post by istvan3 on 2013-11-22
I had the problems again. I changed some BIOS settings not it works, again. I did not use Windows in between. 
What I changed in BIOS:

[TABLE="class: grid, width: 600"]
[TR]
[TD][/TD]
[TD]BEFORE[/TD]
[TD]NOW[/TD]
[/TR]
[TR]
[TD]UEFI Hard Disk Drivve BBS Properties[/TD]
[TD][/TD]
[TD][/TD]
[/TR]
[TR]
[TD]Boot option #1[/TD]
[TD]ubuntu[/TD]
[TD]ubuntu[/TD]
[/TR]
[TR]
[TD]Boot option #2[/TD]
[TD]ubuntu[/TD]
[TD]Windows Boot Loader[/TD]
[/TR]
[TR]
[TD]Boot option #3[/TD]
[TD]Windows Boot Loader[/TD]
[TD]Disabled[/TD]
[/TR]
[TR]
[TD][/TD]
[TD][/TD]
[TD][/TD]
[/TR]
[TR]
[TD]Boot from USB device[/TD]
[TD]Enabled[/TD]
[TD]Disabled[/TD]
[/TR]
[TR]
[TD][/TD]
[TD][/TD]
[TD][/TD]
[/TR]
[TR]
[TD]Secure Boot Control:[/TD]
[TD]Enabled[/TD]
[TD]Disabled[/TD]
[/TR]
[TR]
[TD]Secure Boot Mode:[/TD]
[TD]Custom[/TD]
[TD]Custom[/TD]
[/TR]
[TR]
[TD][/TD]
[TD][/TD]
[TD][/TD]
[/TR]
[TR]
[TD]Serial Port Configuration[/TD]
[TD][/TD]
[TD][/TD]
[/TR]
[TR]
[TD]Serial Port 1[/TD]
[TD]Enabled[/TD]
[TD]Disabled[/TD]
[/TR]
[TR]
[TD]Serial Port 2[/TD]
[TD]Enabled[/TD]
[TD]Disabled[/TD]
[/TR]
[/TABLE]

---

