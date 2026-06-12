---
title: "Ideal setup for SSD &amp; HDD?"
date: 2017-06-18
forum: Installation &amp; Upgrades
---

### Post by r8t3d on 2017-06-18
Hello! I am currently running on Windows and I've been having quite some trouble getting Ubuntu installed alongside Windows 10 with my SSD & HDD combo.
Firstly, I couldn't do anything on my installation of Ubuntu and I found how that I had to put in the "nomodeset" parameter to make it work. Then, I had to disable safeboot and hibernation on my computer. Once I did that, I tried to go through with my Ubuntu installation and it went fine (I thought) until I couldn't boot back into it after installing. I checked and it even installed grub. I reformatted and reset my storage setup to see if I can give this another go. 
[IMG]https://i.gyazo.com/5e10760740f1b3aa83cf4d49b9eca88e.png[/IMG]
Does anyone have advice on how I should go about installing and everything with this current setup? I've got such a headache from just trying to figure out the nomodeset thing, now I'm completely lost as to why it didn't boot into Grub. 

Any help would be greatly appreciated, thank you.

---

### Post by TheFu on 2017-06-18
You don't appear to have any free space for Ubuntu to install.  Between 15G and 100G would be good. I suppose you have a UEFI system, so you'll reuse the existing EFI partition, probably want a 700MB /boot partition, then want 25G for /, with 4G for a swap partition and the remaining storage for /home.  Hopefully, your disks are GPT, not MBR formatted, so you don't have to screw around with extended and logical partitioning.  

If you want clear instructions, please run the **boot-info** script and post the URL it creates. [https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)  The data it provides will provide a clearer idea about the setup of the computer.

---

### Post by oldfred on 2017-06-19
I am not seeing an ESP - efi system partition (FAT32 format), so then it looks like an old system with BIOS/MBR configuration.
Then you have the 4 primary partition limit with MBR.

 My laptop already has 4 primary partitions: how can I install Ubuntu?
[http://askubuntu.com/questions/149821/my-laptop-already-has-4-primary-partitions-how-can-i-install-ubuntu](http://askubuntu.com/questions/149821/my-laptop-already-has-4-primary-partitions-how-can-i-install-ubuntu)
Good advice on how to handle all four primary partitions used. - srs5694
[http://ubuntuforums.org/showthread.php?t=1686440](http://ubuntuforums.org/showthread.php?t=1686440)
Be sure to create recovery DVD(s) first. And a Windows repair CD. 

Do you want Ubuntu on SSD or HDD?

What brand/model system? What video card. 
Often nVidia is the one that needs nomodeset to boot installer and first boot after install, or until you install proprietary driver.

---

### Post by efflandt on 2017-06-19
Note that it is best to first shrink a Windows partition using Window's own Disk Management to free up unallocated space to install Ubuntu.

Also you may want to put grub in the MBR of the opposite drive than you currently have set in BIOS to be the boot drive now for Windows. I don't know about Win8 or newer, but occasionally a long Win7 update (service pack or NET framework?) will fail if not booting from its own MBR. So you can set your BIOS to normally boot the drive with grub, and switch back to the one that boots Windows from its MBR if a Win update fails.

---

