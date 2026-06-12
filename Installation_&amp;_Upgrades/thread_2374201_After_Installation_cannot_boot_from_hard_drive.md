---
title: "After Installation cannot boot from hard drive"
date: 2017-10-13
forum: Installation &amp; Upgrades
---

### Post by n88yanks on 2017-10-13
I have successfully installed Ubuntu 16.4 on my laptop, but after installation the machine will not boot from the hard drive - boots fine from USB, but not from teh HD.  I followed the instructions in this thread, [https://ubuntuforums.org/showthread.php?p=11919563](https://ubuntuforums.org/showthread.php?p=11919563) but the problem still exists.  Any help would be appreciated!  Thank you!

Jim+

*jim@jim-Aspire-ES1-512:~$ sudo fdisk -l*
*[sudo] password for jim: *
*Disk /dev/sda: 465.8 GiB, 500107862016 bytes, 976773168 sectors*
*Units: sectors of 1 * 512 = 512 bytes*
*Sector size (logical/physical): 512 bytes / 4096 bytes*
*I/O size (minimum/optimal): 4096 bytes / 4096 bytes*
*Disklabel type: gpt*
*Disk identifier: BF514EBA-D7F3-40E6-8435-207069CE091B*

*Device         Start       End   Sectors   Size Type*
*/dev/sda1       2048   1050623   1048576   512M EFI System*
*/dev/sda2    1050624 968624127 967573504 461.4G Linux filesystem*
*/dev/sda3  968624128 976771071   8146944   3.9G Linux swap*


*Disk /dev/sdb: 7.6 GiB, 8103395328 bytes, 15826944 sectors*
*Units: sectors of 1 * 512 = 512 bytes*
*Sector size (logical/physical): 512 bytes / 512 bytes*
*I/O size (minimum/optimal): 512 bytes / 512 bytes*
*Disklabel type: dos*
*Disk identifier: 0x0bff4ba5*

*Device     Boot Start      End  Sectors  Size Id Type*
*/dev/sdb1  *     2048 15826943 15824896  7.6G  c W95 FAT32 (LBA)*


*Disk /dev/sdc: 3.9 GiB, 4169138176 bytes, 8142848 sectors*
*Units: sectors of 1 * 512 = 512 bytes*
*Sector size (logical/physical): 512 bytes / 512 bytes*
*I/O size (minimum/optimal): 512 bytes / 512 bytes*
*Disklabel type: dos*
*Disk identifier: 0x89125686*

*Device     Boot Start     End Sectors  Size Id Type*
*/dev/sdc1         464 8142847 8142384  3.9G  6 FAT16*

---

### Post by RobGoss on 2017-10-13
Hello and welcome to the forums, 
I'm assuming this is a single boot installation correct?

Did you install Ubuntu in UEFI or BIOS mode?

You might have to access the BIOS to see how your machine is setup

Most machines BIOS can be accessed using the F2 key

This page might be helpful
[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)


Please provide the spec for your machine in order to assist you further

---

### Post by n88yanks on 2017-10-13
Yes thank you - it is a single boot installation.  Ubuntu was installed in UEFI mode.  What kind of specs would be helpful?  It is an Acer laptop - it came installed with Win 8 - I upgraded to Win 10 but then wiped the HD to install Ubuntu.   Thank you.  Jim+

---

### Post by RobGoss on 2017-10-13
Acer has Superior password that needs to be set in order to be able to install and boot Ubuntu, Here's one post that may help get things rolling [https://askubuntu.com/questions/771455/dual-boot-ubuntu-with-windows-on-acer-aspire/771749#771749](https://askubuntu.com/questions/771455/dual-boot-ubuntu-with-windows-on-acer-aspire/771749#771749)

Scroll down to the second post I believe it should have information on how to achieve this issue

---

### Post by RobGoss on 2017-10-13
Acer has Superior password that needs to be set in order to be able to install Ubuntu, Here is one post that may help get things rolling [https://askubuntu.com/questions/771455/dual-boot-ubuntu-with-windows-on-acer-aspire/771749#771749](https://askubuntu.com/questions/771455/dual-boot-ubuntu-with-windows-on-acer-aspire/771749#771749)

Scroll down to the second post I believe, it should have information on how to ovrr come this issue

---

### Post by n88yanks on 2017-10-13
Thanks for the help.  I've been playing around with this with some success.  There didn't seem to be an option to rename the [FONT=Consolas][COLOR=#111111]shimx64.efi file and when I tried to add another I received the message "File is exist" (yes - that is verbatim), however the new option did not show up in the boot options.  So [/COLOR][/FONT]I ran boot repair and I still get the error on boot that it can't boot from the HD, but then I am given the choice to select the HD and now its boots.  I am moving in the right direction.  I've posted the details on the ubuntu pastebin site.  [http://paste.ubuntu.com/25733814](http://paste.ubuntu.com/25733814).  Thanks again for the assistance.  Jim+

---

### Post by oldfred on 2017-10-13
Do you have latest UEFI from Acer?
Some older threads mention downgrade, but then newer threads say newest Acer UEFI works.

 Acer Trust Settings - details, some now report that then secure boot has to be on to set trust:
[https://ubuntuforums.org/showthread.php?t=2358003](https://ubuntuforums.org/showthread.php?t=2358003)
[https://ubuntuforums.org/showthread.php?t=2291335&p=13341757#post13341757](https://ubuntuforums.org/showthread.php?t=2291335&p=13341757#post13341757)
[https://ubuntuforums.org/showthread.php?t=2342323](https://ubuntuforums.org/showthread.php?t=2342323)
[http://ubuntuforums.org/showthread.php?t=2297947&p=13369742#post13369742](http://ubuntuforums.org/showthread.php?t=2297947&p=13369742#post13369742)
Acer Cloudbook shows screen for selecting trust
[http://bernaerts.dyndns.org/linux/74-ubuntu/340-ubuntu-install-acer-aspire-cloudbook-431](http://bernaerts.dyndns.org/linux/74-ubuntu/340-ubuntu-install-acer-aspire-cloudbook-431)
[http://community.acer.com/t5/Predator-Laptops/Dual-Boot-Ubuntu-Win10-Step-by-step-guide/m-p/430392#U430392](http://community.acer.com/t5/Predator-Laptops/Dual-Boot-Ubuntu-Win10-Step-by-step-guide/m-p/430392#U430392)
 InsydeH20 setup utility
Acer Very latest UEFI/BIOS works, downgrade not required:
[http://ubuntuforums.org/showthread.php?t=2298380&p=13419141#post13419141](http://ubuntuforums.org/showthread.php?t=2298380&p=13419141#post13419141)

---

