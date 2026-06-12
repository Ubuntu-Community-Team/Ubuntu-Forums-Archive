---
title: "HDD Partition CRISIS!  and GRUB Error 17!"
date: 2006-03-31
forum: Installation &amp; Upgrades
---

### Post by rinch on 2006-03-31
Hi!

I've had a major partition crisis when my battery failed during an upgrade.  (this happened because the battery applet had crashed during the upgrade, and I didn' t get the 7min warning I have grown accustomed to! :o) )
This failure seemed to cause a failure of the partition table - and I was subsequently unable to boot into my linux partition - however, GRUB was still functioning, so I could boot into windows.

From windows I ran a utility called testdisk which reported errors in the partition table, which it fixed.  then when I rebooted, GRUB failed with error 17.  

tried to use the install disk with "[FONT="Courier New"]rescue[/FONT]"
failed due to a problem with stage 1
tried loading from a live CD... from which I am able to mount the partition and access the files.
tried correcting the /boot/grub/menu.lst  which didn' t work.
tried reinstalling grub (here grub fails to embed the stage1_5 file into the MBR)

I'm out of ideas - and I haven' t got any space on the HDD to reinstall linux without losing some rather valuable data.

still no success!

Any help welcome!

---

### Post by ispmarin on 2006-03-31
You can try to boot via the livecd, mount your old partition, do a chroot on the mounted partition, and do a grub-install. Maybe this will help.

---

### Post by rinch on 2006-03-31
chroot: cannot run command '/bin/bash': Exec format error

---

### Post by rinch on 2006-04-01
I have had some success by running the default Ubuntu installation.  At the section where you repartition the disk, I chose not to format the partition, but changed the mount point to "/" the root file system.

exit and save and then skip ahead to select the GRUB install.

after GRUB has successfully installed, ABORT the installation and reboot

this returned a functioning GRUB menu.

In my case, this was not enough to boot ubuntu, due to other problems - but at least now I can save my data and reinstall!

This process is covered in [HOWTO Restore GRUB (if your MBR is messed up)]("http://www.ubuntuforums.org/showthread.php?t=76652")

---

