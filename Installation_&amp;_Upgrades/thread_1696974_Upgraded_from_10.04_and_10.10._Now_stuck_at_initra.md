---
title: "Upgraded from 10.04 and 10.10. Now stuck at initramfs"
date: 2011-02-28
forum: Installation &amp; Upgrades
---

### Post by dwllui on 2011-02-28
I have recently upgraded from 10.04 to 10.10 (dual boot with Windows 7). After the upgrade, Grub was gone. Tried to boot using live CD to repair Grub but keep prompting "initramfs:unable to load medium containing live file system" before i can load into Ubuntu. I was able to confirm that the live CD has no problems (tried it on another PC and it works fine) Finally, used Windows 7 CD to repair and managed to boot into Windows. Tried to totally remove the Ubuntu partition using Windows disk management but was not successful. I deleted the partitions during this process and the unallocated space could not be allocated using Windows disk management. Used Easeus partition master and was able to format and allocate a drive to the unallocated space (unfortunately, i don't think this is totally cleaning up the Ubuntu partition). Did anyone manage to solve this problem before? I just want to do a clean 10.10 installation on the Ubuntu partition again. But I can't clean it properly in Windows nor I could boot into the liveCD (not even using a bootable GParted disk). How can I get this running again?

---

### Post by Kernelslave on 2011-02-28
Don't panic, everybody wipes their pc sometimes.

Most likely this happened because you were installing windows first and partitioned all the space for it w/o leaving any space for lin (ub installer has probs resizing the NTFS)
 Burn new Ubuntu cd (just in case), and follow everything on [https://help.ubuntu.com/community/DualBoot/Windows](https://help.ubuntu.com/community/DualBoot/Windows)
You might have to try Wubi ;p

Most of all, dont rush read everything and follow instruction >>> dual boot should be easy ;)

---

### Post by dwllui on 2011-02-28
Hi there. Thanks for your advice. I will try to to use "GParted from UNetbootin-PartedMagic" or "QtParted from the System Rescue CD" and try to clean up the previous Ubuntu partition and do a clean installation. Will keep you posted whether I can resolve the problem. Thanks again

---

### Post by dwllui on 2011-03-01
Tried the System Rescue CD 2.0.1 - cannot even reach the command prompt to run QtParted. Please look at attached image

Tried UNetbootin-PartedMagic - unable to boot to USB although I have that option in the BIOS. Tried the Parted Magic boot CD and similarly, no success. Please find attached image for more details

Finally, I have tried to reproduce the error when booting into the Ubuntu 10.10 live cd. "initramfs unable to find medium containing live file system". Are there any more ideas that may work (apart from removing the hard disk from my desktop and reformatting the entire drive which contains both the windows and ubuntu partitions and then reinstalling everything again?). I can still boot into windows 7 and everything is fine in there. Therefore, I do hope there's a solution to this problem

---

### Post by dwllui on 2011-03-01
attached initramfs when booting ubuntu live cd

---

### Post by dwllui on 2011-03-01
Found another possible solution here [http://ubuntuforums.org/showthread.php?t=1682433&highlight=initramfs]("http://ubuntuforums.org/showthread.php?t=1682433&highlight=initramfs") which is to hold down the SHIFT key and try to boot into the system. Not sure whether this will work since I have used disk management in Windows 7 to reformat the hard drive after using Easeus Partition Manager to reclaim the partition for Windows 7 (but as indicated previously, every time i delete the volume again in Windows 7 disk management, I could not create a drive directly and going to Easeus again shows me that I still have stuffs in there. So i believe that my previous 10.04 to 10.10 upgrade is still there). 

Another possibility, as indicated by KernelSlave is to install Wubi. If i were to migrate the Wubi installation into the partition which contains my previous 10.04 to 10.10 upgrade (that is not working now), would this work using the migration directions provided in [http://ubuntuforums.org/showthread.php?t=1519354]("http://ubuntuforums.org/showthread.php?t=1519354") Anyone who has experience with this, your feedback is greatly appreciated.

---

### Post by dwllui on 2011-03-03
Another unsuccessful attempt holding down the SHIFT key during boot. Cannot boot into previous versions of Ubuntu.

Even tried including boot options before trying to start Ubuntu without installation using the livecd (all_generic_ide floppy=off irqpoll) but still got kicked out to busybox with initramfs: unable to find medium containing live file system.

Has anyone here managed to solve this problem? Although i can reclaim the partition using Easeus partition master (home edition) in Windows, but i am not able to extend my drives and no matter how many times i attempt to reformat the partition, it still appears that the partition previously installed with Ubuntu is not wiped out. Any advise is greatly appreciated before I take the only solution I can possibly try, which is to reformat the entire hard disk, repartition it again (assuming i could) and do a clean installation of windows and Ubuntu.

---

### Post by deconstrained on 2011-03-04
If the shift key trick doesn't work then use a live disk and chroot. Then you'll have a chance to double-check your configuration and run update-initramfs and grub-update in order to repair your Linux image so that it boots properly.

---

