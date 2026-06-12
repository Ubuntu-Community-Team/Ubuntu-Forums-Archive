---
title: "dualboot ubuntu with ubuntu problem"
date: 2010-11-08
forum: Installation &amp; Upgrades
---

### Post by heian on 2010-11-08
Hi,

I'm trying to install ubuntu 10.04 twice on a computer with two harddrives. 

Both ubuntu's and swap installed on the first drive, and both home partitions on the second one. Here is how i tried it using g-parted first:


Sda1  = ext4    36Gb     (  /  for ubuntu-en )   prim. partition
Sda2  = ext4    36Gb     (  /  for ubuntu-nl )   prim. partition
Sda3  = swap             (      one swap for both OS  )


the second drive formatted as a extended partition, with three logical stations: 

Sdb1  =  ext4     30 Gb   (  home  for ubuntu-en  )
Sdb2  =  ext4     24 Gb   (  home  for ubuntu-nl )
Sdb3  =  NTSF     22 Gb   (  not sure what  ;-)  )

first  installed ubuntu-en
second installed ubuntu-nl

When i try to boot, only ubuntu-nl is available, it is not possible to
start ubuntu-en. Ubuntu-en just likes disappeared.

sudo os-prober   en  sudo update-grub  didn't change anything.

linux2-nl@linux-dualboot:~$ grep menuentry /boot/grub/grub.cfg
menuentry 'Ubuntu, met Linux 2.6.32-21-generic' --class ubuntu --class gnu-linux --class gnu --class os {
menuentry 'Ubuntu, met Linux 2.6.32-21-generic (herstelmodus)' --class ubuntu --class gnu-linux --class gnu --class os {
menuentry "Memory test (memtest86+)" {
menuentry "Memory test (memtest86+, serial console 115200)" {
menuentry "Ubuntu, with Linux 2.6.32-21-generic (on /dev/sda1)" {
menuentry "Ubuntu, with Linux 2.6.32-21-generic (recovery mode) (on /dev/sda1)" {

Just want one stable ubuntu, and one to play around with. And both their home partition stay safely on the second drive.

Is there someone out here who see what i do wrong?

many thanks in advance,

heian

---

### Post by Rubi1200 on 2010-11-10
I suggest you try using a custom GRUB menu. I have worked with 2 different Ubuntu versions on the same machine, but I suspect that since they both use the same kernel GRUB picks whichever was installed last (in this case the Dutch version).

Here is a great guide about how to create custom menu entries:
[http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)
Section 6 (adding entries using the 40_custom file is what you need to look at).

If it does not work, then post the results of the boot-script linked at the bottom of my post so we have more information to work with.

Thanks.

---

