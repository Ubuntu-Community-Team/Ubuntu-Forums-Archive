---
title: "Linux Partitioning with Ubuntu, CentOS and openSUSE"
date: 2015-08-09
forum: Installation &amp; Upgrades
---

### Post by mrcanadianmenace on 2015-08-09
Hi all,

I'm a newb with Linux and have been trying to follow the edX Linux Foundation course to learn the basics but have been having difficulties trying to install all of the used distros.  The distros used are Ubuntu, OpenSUSE and CentOS.  I have been trying to partition these systems on to one hard drive but have been unsuccessful so far and would very much appreciate a detailed walkthrough for how to setup these three distributions onto one hard drive or being redirected to where I can find a guide to do so.  Thanks a bunch! :)

---

### Post by yancek on 2015-08-09
If you don't have experience with multi-boot, the simplest thing to do is to create a single partition of 15-25GB for the operating system and then create a swap partition.  Repeat the process for each system except you do not need to create multiple swap partitions.  You can then use the remaining space for shared data. 

Have you checked to see that your hardware met the minimum requirements for each distro?  What have you tried and what problems have you had?    There are numerous tutorials on installing all three systems.  The link below is a detailed tutorial on installing Ubuntu and if you scroll down the page, you will see a step by step for dual booting.  

 [http://www.dedoimedo.com/computers/ubuntu-14-04-install-guide.html](http://www.dedoimedo.com/computers/ubuntu-14-04-install-guide.html)

It will be simpler if when you install the third system, you install the Grub bootloader to the MBR.  If you are using UEFI, that's a different story but you haven't posted much info so just guessing as to what you have.?

---

### Post by howefield on 2015-08-10
> **mrcanadianmenace said:**
> Hi all,

I'm a newb with Linux and have been trying to follow the edX Linux Foundation course to learn the basics but have been having difficulties trying to install all of the used distros.  The distros used are Ubuntu, OpenSUSE and CentOS.  I have been trying to partition these systems on to one hard drive but have been unsuccessful so far and would very much appreciate a detailed walkthrough for how to setup these three distributions onto one hard drive or being redirected to where I can find a guide to do so.  Thanks a bunch! :)

Nothing wrong with installing all three, but isn't the idea to select one distribution and take the course / examination on that one ?

---

### Post by SeijiSensei on 2015-08-10
Here's a general overview of what I would do:

1) Boot from an installation disk, then use gparted or fdisk to create a small primary partition, say 1 GB on new machines, that will be mounted as /boot in all three systems.

2) Create an extended partition spanning the rest of the disk.

3) Divide the extended partition into at least five new partitions, one for swap, one for each OS, and one for /home that will be common to all three.  The size for swap depends in part on whether you intend to use hibernation.  In general, I'd make swap at least as large as physical memory on machines with 2 GB of memory or less.  Beyond that the need for swap decreases considerably on machines that don't require hibernation.

4) Run the installers and point the root of each installation to one of the three OS partitions.  Use the common /boot and /home for each.

5) If you're just learning, and don't expect to have much real content on these machines, then having a common /home may be overkill.  In that case, let each OS create its own /home in its own partition.

---

### Post by mrcanadianmenace on 2015-08-11
Thanks for all of the replies!  I'll leave another reply when I have more information on the hardware going into this computer.  Thank you again so much for the helpful advice though!

---

