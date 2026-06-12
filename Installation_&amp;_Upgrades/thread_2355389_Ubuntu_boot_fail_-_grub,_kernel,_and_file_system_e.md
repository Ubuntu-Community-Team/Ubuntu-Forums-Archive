---
title: "Ubuntu boot fail - grub, kernel, and file system errors"
date: 2017-03-12
forum: Installation &amp; Upgrades
---

### Post by deserati on 2017-03-12
I have Ubuntu 16.04 LTS desktop version (with GUI), fresh install in January, no RAID or special options were selected.  I installed Magento 2 on this machine and never did a backup.  I have quite a few database entries and customized files through the Magento installation that I really do not want to redo.  When I use a live CD, I can view all of the Ubuntu and Magento files on /dev/sba3.  However, when I try to enter the command mount /dev/sba3 /mnt so that I can reinstall kernel and grub through chown, it tells me that there is an unknown file system lvm2.
Here is a sequence of events, and the boot repair disk paste:
[http://paste.ubuntu.com/24163540/](http://paste.ubuntu.com/24163540/)

3/10/17 4pm removed power to running server, to physically move it in the server rack.  Did not do a proper shutdown.
3/10/17 6pm System was loading extremely slow, but was able to boot.  Left for the evening but noticed the website was not loading at all.
3/11/17 9am Arrived to find the system nonresponsive.  Powered down the server and turned it back on.  After the GRUB2 splash screen, I selected UBUNTU as usual, received a lot of white block characters on the screen.  If I typed on the keyboard, new white block characters would appear, as if there was some sort of graphics issue.  Restarted computer again, came to same screen after GRUB loaded UBUNTU.
3/11/17 10am Attempted Boot Repair Disk, selected purge kernels and reinstall last kernel from the advanced menu, as well as "repair file system."
3/11/17 11am Boot Repair Disk stuck on Purge kernels then reinstall last kernel mapper/Ubuntu--vg-root (ins).  This may require several minutes...
3/11/17 11pm Still running Purge kernels
3/12/17 8am Still running Purge kernels, exited out of program and shut down.
3/12/17 810am Attempted boot repair disk again but Purge kernels option is now grayed out and checked - I can't uncheck it. (I assume because it recognizes that there is no longer a kernel.)  Attempted this boot repair again, stuck at same screen.  Exited again.
3/12/17 830am downloaded Super Grub 2 Disk, it did not show any available operating systems, so I clicked the option "Enable RAID/LVM support".  Still no operating systems showed up on file and was unable to load UBUNTU.  I am not sure if this assigned some sort of LVM to my disk, as I never selected any LVM support options on the disk prior to this, but in the next event you will see the live cd references this LVM file system.
3/12/17 845am downloaded live cd and attempted (from forum instructions) to mount and run 'chown' on disk drive through the trial Ubuntu program.  Terminal responded that the file system was type "LVM" and was not able to be mounted.  Unusually, on the left side of the screen I can see both partitions are already mounted, and I can access files through the file manager there.
3/12/17 930am Attempted boot repair disk again, unsuccessful as it runs a continuous loop on the purge kernels then resinstall last kernel mapper/ dialogue.
3/12/17 10am Wrote forums.

Please let me know if there is anything I can do to get this operating system running on this drive again, so that I can keep my Magento/website in tact.

Thank you!

---

### Post by oldfred on 2017-03-12
Since you installed with LVM, did you also choose full drive encryption?

I do not know LVM nor encryption but have a few links.

       LVM - Logical Volume Management.
Advantages/Disadvantages LVM Post #9
[http://ubuntuforums.org/showthread.php?t=1586328&p=9917145#post9917145](http://ubuntuforums.org/showthread.php?t=1586328&p=9917145#post9917145)
[https://wiki.ubuntu.com/Lvm](https://wiki.ubuntu.com/Lvm)
[https://wiki.archlinux.org/index.php/LVM](https://wiki.archlinux.org/index.php/LVM)

You have to mount the LVM with the lvm2 driver. If encrypted you will also need that driver.
sudo apt-get install lvm2

 sudo pvdisplay
sudo lvdisplay 

mount
sudo vgscan --mknodes
sudo vgchange -ay
sudo e2fsck -f /dev/ubuntu-vg/root 

or:

sudo vgchange -ay /dev/mapper/ubuntu--vg-root
mount /dev/mapper/ubuntu--vg-root /mnt
mount /dev/sda1 /mnt/boot

---

