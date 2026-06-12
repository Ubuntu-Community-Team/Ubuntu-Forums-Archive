---
title: "Problem booting with iso mounted as live CD"
date: 2011-07-19
forum: Installation &amp; Upgrades
---

### Post by r_anjit on 2011-07-19
I am running Ubuntu 11.04 with ISO mounted as the live CD .But when I try to install it permanently the installer presents itself with a message .

    The installer has detected that some partitions are mounted on /dev/sda ...........

on prompting with 'yes' to un-mount them the installation continues but halts with a message that the partitions cannot be un-mounted ........providing with a NO gives the same results.

Trying with a USB drive doesnt help either as there is only a changed message with /dev/sdb .

There is no problem hen burn the ISO to a disk.....Is it not possible to perform the installation in my case..Please help...as I try out many flavours of  linux and it is not possible to burn the CD everytime...waste of money and not environment friendly.


Thanks in Advance !!!

---

### Post by ajgreeny on 2011-07-19
So use a CD-RW or DVD-RW or DVD+RW, or at the very least, give them a try.

In spite of many people saying that -RW disks are risky and do not work, it is the way I installed all my versions of ubuntu from 5.04 to the latest.  My CD-RW disks must now be about 8 yrs old and still work perfectly.  I use USBs now when possible, as they are quicker, but my desktop will not boot from a USB, and my old laptop seems to have problems with some live USBs, but no problem with the same .iso burned to CD-RW.

PS:
I'm not sure what you mean by "the iso mounted as a live CD".  More info please, though I will also have a search myself for those terms.

---

### Post by psusi on 2011-07-19
Yes, this the "iso mounted as a live CD" does not make sense, unless you are talking about a virtual machine.

---

### Post by r_anjit on 2011-07-22
Actually I have made the changes to Grub so that it mounts the ISO in the when booting up and this is the problem because it fails to unmount in the installation stage.

---

