---
title: "CRC error causes and  solutions"
date: 2007-01-27
forum: Installation &amp; Upgrades
---

### Post by Peturrr on 2007-01-27
I think I finally solved my CRC error kernel panic stuff.! I learned a few things I want to share.

**CRC errors are almost always hardware related**
Bad memory, bad cdrom or a bad harddisk.

- Three scenarios: 

1. If you **always have CRC errors,** when booting from **liveCD and** **harddisk** version. Your memory is probably damaged. Try running memtest86 that is on the livecd for **a whole night**. If it shows errors, get new memory. If you have some spare memory, just change it and try to boot and see if the error disappears.

2. If you **only have CRC errors** when using the** LiveCD,** it is probably the CD that is damaged or not correctly burned. Try 2 other CD's: One burned on the lowest speed, and one burned on another pc/burner. Also make sure that the downloaded ISO is not damaged by checking the md5sum. (you can search for that on the forums)

3. If you **only have CRC errors** when using your **harddisk** ubuntu, it is probably a harddisk error. Could be a filesystem problem, could be a real hardware problem. 

Personally I experienced scenario number 3. I have a raid 1 filesystem and I just found out that the kernel error only appears when booting from harddisk nr. 1, and no errors when booting harddisk nr. 2 (the mirror). Hopefully I will discover that that harddisk is indeed defective.

---

### Post by poe503 on 2007-05-29
If the above remedies do not work, try decreasing your CPU clock frequency and/or core voltage (assuming your motherboard BIOS allows you to do so).  

This worked for me as my CPU was overclocked.  The overclocking worked OK with Windows but caused "crc error" on boot up with Ubuntu.

If you only get "crc error" when the computer is warm (such as rebooting after Ubuntu installs itself), try removing and cleaning the CPU fan/heatsink assembly and apply new thermal grease at the CPU/heatsink interface.

---

### Post by Kr!ztov on 2007-07-14
Well mine must be an anomoly then. I get the CRC error - System Halted thing, but it has only started happening after I updated Ubuntu. The previous kernel version thing works fine. Anybody know how I can reinstall upgrades to attempt a fix?

---

### Post by bean77 on 2007-09-05
How long is Memtest supposed to take?

---

### Post by bean77 on 2007-09-05
Oops...[nevermind]("http://shsc.info/Memtest86")...

---

### Post by Pumalite on 2007-09-05
Hours

---

### Post by cpomp on 2007-09-17
I believe its scenario 3 for me.
I've had this problem before. It's not memory because I ran memtest overnight and nothing.
I've reinstalled the OS at least 10 different times in my laptop. The way it happens is that I'm able to run for days, sometimes maybe a few weeks and then the laptop starts to suddenly crash and I have problems botting up. Sometimes succeeds, sometimes it fails until I just can't boot up anymore . It happened for XP and now for Ubuntu.

My question is it time to get a new hardrive or should I try something else first, like a testing utility for the hard drive? Do you know of any?

Thanks.

---

### Post by Pumalite on 2007-09-17
Your hard drive seems to be dying.

---

### Post by Falx on 2007-09-24
I've also been having that 'crc error' after installing Kubuntu 7.04 (64-bit) on my newly purchased SATA HDD.

Every time I would run the installation, be it via LiveDVD or otherwise, I would get that error after my first boot (into HDD).

As Peturrr had mentioned, I suspected a hardware issue. To make my story short, I knew it wasn't my RAM nor was it the new HDD. Turns out that my overclocked CPU was the culprit.

I went to the BIOS and set everything back to its factory default state. Now, after re-installing Kubuntu, I've managed to boot into Linux without a hitch. Everything seems to be fine and dandy and am currently updating the system.

In my case, it was an overclocked CPU that caused that error.

---

### Post by Pumalite on 2007-09-24
Crc=cpu

---

