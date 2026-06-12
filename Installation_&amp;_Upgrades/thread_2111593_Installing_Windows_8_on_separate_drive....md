---
title: "Installing Windows 8 on separate drive..."
date: 2013-02-02
forum: Installation &amp; Upgrades
---

### Post by ragtag on 2013-02-02
I was running Ubuntu 12.04 and Win7 on the same box, but on seperate disks, and stupidly decided to upgrade my Win7 to Win8. I disconnected my Ubuntu drive (as I don't trust Windows not to mess up GRUB), and everything installed fine. I then reconnected the drives, and had to change the boot sequence in BIOS so that my Ubuntu drive would be first. After a grub update, Windows was showing up as Windows 8 in GRUB, but when I choose it, the blue window logo comes up for a few moments, followed by an error message for a fraction of a second which says error 0x00000050, and then the computer reboots.

I think that the source of the problem is that Windows hibernates when you do shutdown, and when you boot it from GRUB, it fails to "de-hibernate" for some reason. When I tried mounting the Windows partition in Ubuntu, it insisted I do it as read-only, as the disk was hibernated. 

I've tried boot-repair and update-grub, but neither worked. I also think they attack a different problem than what I'm having.

Has anyone found a solution to this problem?

---

### Post by ragtag on 2013-02-02
Just a little update. Doing the exact same process with Windows 7 works just fine. If I can't figure this out, I may just stick with Windows 7. I only use it for gaming and the odd DRM infested video streaming site. I use Ubuntu for everything else. :)

---

### Post by Mark Phelps on 2013-02-02
First thing you should do is confirm that Win8 will boot from its own drive.  That will rule out Windows-specific boot problems.

IF that works, the problem is likely that Win8 uses a different boot loader than Win7, and (personally) I don't know if GRUB, or if the os_prober can handle that properly.

Sorry, but you'll have to wait for someone with more expertise in booting Win8 from GRUB to come along...

---

### Post by presence1960 on 2013-02-02
> **Mark Phelps said:**
> First thing you should do is confirm that Win8 will boot from its own drive.  That will rule out Windows-specific boot problems.

IF that works, the problem is likely that Win8 uses a different boot loader than Win7, and (personally) I don't know if GRUB, or if the os_prober can handle that properly.

Sorry, but you'll have to wait for someone with more expertise in booting Win8 from GRUB to come along...

I have Windows 8 on one disk and my linux installations (including Ubuntu) on a separate disk. GRUB 2 loads Windows 8 just fine. 

+1 on what Mark says to do. Disconnect the ubuntu disk or make the disk with windows on it the first disk to boot in the hard disk boot order in BIOS. Report back the results of booting this way.

---

### Post by ragtag on 2013-02-07
Choosing the Windows drive in the BIOS, booted Windows 8 just fine, so hit F12 on each boot, and choose which drive to use from the BIOS boot menu...but I wouldn't mind figuring out how to do this with GRUB.

My first theory was that it had to do with Win8 Fast Start, which hibernates part of  the system, and can cause problems if you try to mount the Windows drive in Linux. Unfortunately disabling it fast boot didn't help.

Then I realized I have GRUB 1.99, installed. I guess this could be a problem, and upgrading to GRUB 2, might solve the problem. I'll be trying this out when I get a chance. :)

---

