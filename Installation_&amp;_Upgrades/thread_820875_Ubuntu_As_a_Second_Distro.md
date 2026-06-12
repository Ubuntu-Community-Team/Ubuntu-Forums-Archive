---
title: "Ubuntu As a Second Distro"
date: 2008-06-06
forum: Installation &amp; Upgrades
---

### Post by capatt on 2008-06-06
Hello
     I'm currently triple booting:

C:\XP and PCLinuxOS installed into unallocated area
D:\Vista

I've resized the Vista disk and have an unallocated area there I'd like to install Ubuntu 8.04 to.  I haven't seen anywhere exactly where in the installation process one can do this, and I've searched (probably not very effectively).

I currently boot PCLinuxOS from it's own root partition by chaining from the MBR, configured with EasyBCD.

I'd like to install Ubuntu's Grub to the same place so it detects PCLinuxOS and creates a menu with both.

Somewhat complicated for a n00b I realize, but works great with the triple boot so far.

Any suggestions?  Where in the Ubuntu install process can I make this configuration and install to the unallocated are on the D:\ drive?

Thanks!

---

### Post by housam on 2008-06-06
for ubuntu you need to create 2 new partitions out of that unallocated space : one for the root (/ ) ext3 format and one for the swap ( 1 GB is Ok ).
for maintaining more than 2 systems on your machine , read [[COLOR="Red"]_this guide_[/COLOR]]("http://ubuntuforums.org/showthread.php?t=724817") it may help.

---

### Post by logos34 on 2008-06-06
> **capatt said:**
> Hello
     I'm currently triple booting:

C:\XP and PCLinuxOS installed into unallocated area
D:\Vista

I've resized the Vista disk and have an unallocated area there I'd like to install Ubuntu 8.04 to.  I haven't seen anywhere exactly where in the installation process one can do this, and I've searched (probably not very effectively).

Choose the 'manual' partition option in the ubuntu installer.  Then set ubuntu '/' (ext3) to the empty space.  You can use the existing pclinuxos /swap. You could probably also select 'Guided -- use largest continuous free space' option and it would correctly choose the unallocated space.
> 
I currently boot PCLinuxOS from it's own root partition by chaining from the MBR, configured with EasyBCD.

I'd like to install Ubuntu's Grub to the same place so it detects PCLinuxOS and creates a menu with both.

Ubuntu will detect the presence of the other OSs and add them to it's own own fstab and menu.lst.  But if I understand you correctly and you want to continue using EasyBCD to chainload the linux, do the same thing you did for pclinuxos and [install grub to the bootsector of the linux (in this case, ubuntu) root partition]("http://neosmart.net/wiki/display/EBCD/Ubuntu"), not the mbr.  Then add ubuntu to EasyBCD.

---

