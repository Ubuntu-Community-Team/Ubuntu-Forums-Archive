---
title: "install, partition &amp; dual boot questions"
date: 2007-01-17
forum: Installation &amp; Upgrades
---

### Post by davidm0115 on 2007-01-17
I have xp on my 1st hard drive and was trying to install Ubuntu on my 2nd hard drive.  After the "install" the partitions didn't end up the size I chose in the partitioning setup and I have no idea what I am doing with the GRUB setup.  I ended up getting GRUB error 17 after I tried to reboot so Ubuntu would continue it's install. I had to repair xp to run fixmbr and now I can at least boot to xp.  I don't know where the install left off or if anything was installed at all!  I can use PartitionMagic to setup a root, swap and shared partitions if I need to.  If I can get the install done then I need to be able to do a dual boot.

Does anyone have any suggestions other than going back to crayons and coloring books.  I feel like an idiot.

---

### Post by rocknrolf77 on 2007-01-17
Don't know how to fix this but someone will come along who knows how. But at least here is the manual for grub : [http://www.gnu.org/software/grub/manual/html_node/](http://www.gnu.org/software/grub/manual/html_node/)

Maybe it has something to do with the order of the disks in bios?:-k

---

### Post by goodfella on 2007-01-17
When  you install ubuntu on a seperate drive follow this [post]("http://www.ubuntuforums.org/showthread.php?t=179902")

Ubuntu installs GRUB on the first bootable drive specified in your bios which explains why you had to use fixmbr to boot into windows.  Another thing to note is ubuntu does not require a reboot to install like windows does.  In windows you choose what partition to install windows on  and then the computer reboots and starts the installer.  For ubuntu it just installs.  

GRUB error 17 indicates that a partition specified to boot from does not exist.  One way that might help you boot into ubuntu if you get GRUB errors is to use the live cd and select the **Boot From First Hard Drive** option.  This will boot from the first bootable drive set in your bios so make sure your ubuntu drive is the first bootable hard drive in your bios.

---

### Post by jd65pl on 2007-01-17
Just boot with the live CD, start up gparted and delete your last ubuntu install then re-install using the provided installer selecting the options which apply to you. Once the installer has finished grub will install correctly.

Did you changed any partitions before the error occurred?

---

