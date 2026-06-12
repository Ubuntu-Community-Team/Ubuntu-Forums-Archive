---
title: "Ubuntu install stops at GRUB"
date: 2006-12-29
forum: Installation &amp; Upgrades
---

### Post by dversouri on 2006-12-29
Hello, looking for a little help here. 

I have 5 identical brand new systems that I am building for a client. I have used this exact same iso, physical cd, and identical hardware in a good 20+ systems in the past. 

on this batch of 5, 2 machines loaded flawlessly. on the other 3, the install gets to the window titled 'Installing GRUB boot loader' the cd spins down, and the system sits at 0% forever. the system is not frozen, i can toggle numlock etc. 

the ram on all systems has been 24 hour memtested on each individual board with no issues, cpu temp is fine, hard drives have been checked for errors, bios is identical version on all systems. i have tried reburning this iso at the slowest speed and testing the cd for errors afterwords.

i can take a drive from one of the completed systems and plug it into one of the other three, and it boots all the way into ubuntu with no issues. i attempted to ghost (2003, and 8.0) one of the completed drives to a new blank one, installed it in the new machine, and it stops at a black screen that just says GRUB_ on it.

the drives are hitachi deskstar 250gb sata's. the motherboard is an ASUS a8n-vm. each system has 1gb of ram, and a 3800 processor.

im under a deadline and running out of ideas, any help would be greatly appreciated!

edit: a little info i forgot

the client provided me with this iso, i believe it is version 5.10 of ubuntu

---

### Post by meng on 2006-12-29
Is this using the Alternate CD or Live CD? Try the former if the latter is giving problems.

---

### Post by dversouri on 2006-12-29
niether, this is a client provided custom configured installation. it has worked on many batches of this identical hardware config in the past.

i would guess it is already the alternate cd, with a second cd of the clients specific apps/drivers etc. however it doesnt get to the point where it asks to reboot, then asks for the second cd on 3 of these systems. it is stopping in the initial install, after the drive is formatted and the install files are copied. it stops at 'installing the grub package...' at 0%

---

### Post by meng on 2006-12-29
Then I wonder whether you could use some sort of recovery tool (like a regular Ubuntu LiveCD) to grub-install manually, after you get to the hanging point.
[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

---

### Post by dversouri on 2006-12-29
Live cd fails at  

----------------------------------

Busybox v1.1.3 (Debian 1:1.1.3-2ubuntu3) Built in shell (ash)
enter 'help' for a list of built in commands.

/bin/sh: cant access tty; job control turned off
(initramfs) _

----------------------------------


also attempted to use the 'super grub disk' repair listed on that link, that one failed as well.
thank you for the suggestions however. any other ideas?

---

### Post by meng on 2006-12-29
No I'm scratching my head trying to work out what's wrong (aside from hardware failure, which seems unlikely to have occurred 3 times out of 5 in identical systems). Sorry, good luck though!!!

---

