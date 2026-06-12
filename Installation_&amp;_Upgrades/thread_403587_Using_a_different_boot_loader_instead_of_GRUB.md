---
title: "Using a different boot loader instead of GRUB"
date: 2007-04-07
forum: Installation &amp; Upgrades
---

### Post by cm1924 on 2007-04-07
I am using a boot loader to boot Win2000, XP and OpenSuse. The boot loader (BOOT-US) is installed on a floppy disc. OpenSuse is installed on a logical drive with lilo installed on the first sector of the logical drive not the MBR. The swap file is also on a logical drive. I want to install Ubuntu 6.06 on another logical drive and again install lilo on the first sector of this drive.

When I click the install Ubuntu icon it gives me a GUI interface with only six steps for the installation and none of them allow me to select where I want the OS loader installed. If I select text install then there appears to be an option allowing me to select where the boot loader is installed.

Question 1:
As I need to select where the Ubuntu boot loader is stored, is there a away for me to use the GUI installation or must I use the text based one?

Question 2:
Can both linux installations use the same swap file? I can't see why not but I want to be sure.

Thanks for any help you give.

John

---

### Post by mmmichael on 2007-04-07
#2: yes, they can use the same swap file.

---

