---
title: "What to backup?"
date: 2010-11-15
forum: Installation &amp; Upgrades
---

### Post by jus71n742 on 2010-11-15
I am going to experiment with my laptop in doing a dual HDD system.  Windows  on one and Ubuntu on the other.  If I want to do an upgrade while I am at it.  9.10 - 10.04/10.10 what all is essential to back up?  just the home directory?  
Am I correct in saying that it will also keep all my settings in place once I upgrade and restore?  I essentially need to know this for when I do it on my Desktop with a similar setup but more scripts and such.

---

### Post by s3MA00RRNY on 2010-11-15
At minimum I would backup:

Home
/etc/apt/sources*
Firewall settings (location varies)
A markings list (load Synaptic. Go to File... > Save Markings)

Be sure to check save full state.

---

### Post by Mark Phelps on 2010-11-16
To be SAFE, you would also want to disconnect the Windows drive while doing the upgrade.  This will prevent problems like changing the MBR on the Windows drive, or installing GRUB to a partition on that drive.

---

### Post by jus71n742 on 2010-11-19
Well I have it up and dual booted.  Windows restored correctly and everything is as I left it.  Now the Ubuntu side I need to get my backup restored.  I followed this
[http://ubuntuforums.org/showthread.php?t=35087&highlight=backups](http://ubuntuforums.org/showthread.php?t=35087&highlight=backups)

And when I restored and rebooted I still am missing some of the files.  If I reinstall the programs with settings (Tbird, Chrome, etc etc) will they find the files or be a big ole maybe?

I only backed up /home.
and I am now up to 10.04 instead of 9.10 if that has anything to do with it.

---

