---
title: "BIOS cannot find bootable OS on hard disk after installation"
date: 2006-12-26
forum: Installation &amp; Upgrades
---

### Post by Linux4Life on 2006-12-26
Hello,
    I have been running LINUX in various flavors for several years and have absolutely stumped myself, hopefully someone here in the forums can help.  Here is the problem:

During the installation of 6.06 (or 5.10) on a new system, the BIOS is unable to boot off the hard disk when the installer reboots the system.   The system is an Intel D975XBX mobo with a 3.46 Ghz Extreme Edition CPU, 1024 MBs of RAM (512 x 512 dual mode), a DVD burner and both a SATA and ATA/133 hard drive, both of which exhibit the same problem.  The BIOS will error upon reboot that it cannot find a bootable medium and provide the age old option to retry.

I have loaded Windows (retch) to confirm the hardware works, and it does perform as expected, booting off the hard disk as needed.   The only way into LINUX right now, is to boot off the DVD/CD and choose to boot off the first hard drive, which works sporadically.  

I have run the memory test on the CD ad nauseum, passing all the time.

Has anyone run into a similar issue?  From other web based posts it appears the motherboard should work with the distribution, and in fact everything works great with the exception of booting from the hard drive.

Thanks for your help in advance!

---

### Post by scrooge_74 on 2006-12-26
power off the system, even unplug it for a moment so it will loose all energy then try again.  I had a stubborn computer (just die a few days ago) that will sometimes loose the drives and not see them in the bios, and I had to do just that to make her see them again

---

### Post by adaptr on 2006-12-26
The very first thing you need to determine is what disk ID Grub gives to your Ubuntu system partition - it won't be the one in grub.conf, that's for sure.
Then you'll have to edit grub.conf to use the right disk, and re-install grub to the right MBR.

Chances are that the SATA disk is chosen as your boot disk, so that'll be disk 0 at boot up, but when Grub loads, it will probably see it as disk 1 or 2.

Grub does not see what the BIOS sees.

---

### Post by Linux4Life on 2006-12-26
I have been around the block on powering off, unplugging... drop kicking etc...

I will check the GRUB settings once I get my power supply replaced.  It died this evening.. blew a capacitor... that MAY have been the root of the problem all along.

I'll post a reply once I get back up and running.  What poor timing for a PS to fail.   Thanks for the replies!

---

