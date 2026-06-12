---
title: "After 17.10 installation, no bootable devices"
date: 2017-10-27
forum: Installation &amp; Upgrades
---

### Post by rexpop on 2017-10-27
Thanks in advance for any help you guys can provide.


  I have a Toshiba L50-B-243. I installed Ubuntu 17.10 choosing to  erase the entire disk and previous partitions (Windows 10 & KDE  Neon). After install I got the dreaded "No bootable device - please restart"  message. Using the Live USB I ran boot-repair, but it told me there was  an error when repairing. Here is the log: [URL="http://paste.ubuntu.com/25825329/"]http://paste.ubuntu.com/25825329/
[/URL]

  I've tried re-installing from the Live USB to no avail. I've checked  the BIOS menu and SecureBoot is definitely inactive, and in the config  menu UEFI is selected. I've double-checked that the Live USB is  definitely using EFI.

More details of some of the suggested solutions I've tried can be found here: [https://askubuntu.com/questions/969662/unable-to-boot-after-17-10-installation-no-bootable-device-on-toshiba-l50-b](https://askubuntu.com/questions/969662/unable-to-boot-after-17-10-installation-no-bootable-device-on-toshiba-l50-b)

I have had absolutely no luck after three days of trying so any help you can provide is truly, truly appreciated. My laptop is currently useless :-(

Thank you again for any support you can give,

Avi

---

### Post by mörgæs on 2017-10-29
Hi, welcome to the fora. 

Does it boot a 64 bit Lubuntu ISO?

---

### Post by rexpop on 2017-10-29
Hi, I haven't tried with Lubuntu - although I just read on another forum I should try the Lubuntu alternate ISO (without GUI) - I've tried everything else so far, so I'll download the ISO now. I'll update you on the results.

Thanks for taking the time to read and reply, I appreciate the help.

EDIT: So, no, the Lubuntu USB also didn't work :-( 

BUUUUTTT: following advice found at linux.com, I was able to use the only Live USB that my laptop thinks is bootable, from its grub menu enter the command line, and use:

grub> set root=(hd1,2)
grub> linux /vmlinuz root=/dev/sda2
grub> initrd /initrd.img
grub> boot

to load my OS on my hardrive so I'm currently using Ubuntu 17.10, logged into my hdd, everything is good except for one thing: I can't make it stick. I have to use the same method every time I want to boot up my system. Do you have any suggestions for how I can make grub do this automatically when my computer turns on so I don't have to keep directing it? If it helps, I ran boot-info to get this [http://paste.ubuntu.com/25848854/](http://paste.ubuntu.com/25848854/)

Thanks again for your help - it is really appreciated!

---

### Post by mörgæs on 2017-10-30
You don't have to thank me. You found the solution yourself, at least a temporary one.

For the GRUB question I'll pass it to someone knowing more than me.

---

