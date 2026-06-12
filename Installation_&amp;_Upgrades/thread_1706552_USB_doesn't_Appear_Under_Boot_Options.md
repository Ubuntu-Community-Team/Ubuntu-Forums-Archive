---
title: "USB doesn't Appear Under Boot Options"
date: 2011-03-14
forum: Installation &amp; Upgrades
---

### Post by johnveix on 2011-03-14
Hello all, first time poster! 

I've recently been trying to attempt to install Ubuntu on a partition on my macbook pro OS X 10.6.6. 

I have attempted to create a bootable USB stick (as I currently do not have any CD's/DVD's to use). I have followed the guide on the Ubuntu installation page twice, word for word, command for command. Everything goes flawlessly, all the files are visible on the drive when I checked, and I have never received any errors in the terminal. The problem arises when I attempt to boot from the USB, it simply does not appear under the options when I attempt to boot. I have also checked the Start up Disk under system preferences. 

I have attempted the installation on two different USB sticks, and the same problem on both, flawless to install to USB, but then it is somehow not booting.

I have checked with the USB company and directly from the website it says that the PNY attache is capable of this. It is the 4GB model. 

With that being said, it's getting late and I'm sure this is a very simple fix, but I would greatly appreciate if any of the experts would lend a minute or two to an eager Ubuntu noob. 

Cheers! :D

---

### Post by mcduck on 2011-03-14
As far as I know, macs require a GUID partition table on the drives to boot, while your USB drive probably uses the old MBR partitioning instead (As that's what most PC's still use).

Ubuntu supports both partitioning systems, so everything should work if you repartition the USB drive with the Disk Utility on OSX before you use the Startup Disk Creator on Ubuntu.

You might also be able to find more answers on the Apple users subforum: [http://ubuntuforums.org/forumdisplay.php?f=328]("http://ubuntuforums.org/forumdisplay.php?f=328")

---

### Post by johnveix on 2011-03-14
thanks for the quick reply! I've tried formatting the disk twice as GUID, but I'm not sure if it retains this when I write the installation .img to the USB in terminal. 

I've encountered a similar thread in the apple support sub-forum and have posted my information there. 

I will also leave this thread open in the hopes that between this thread and the one created by another user we can both figure out the answer to this problem.

Again thanks for the quick reply.

---

