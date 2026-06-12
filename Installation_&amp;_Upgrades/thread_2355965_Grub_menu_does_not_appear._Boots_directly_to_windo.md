---
title: "Grub menu does not appear. Boots directly to windows"
date: 2017-03-18
forum: Installation &amp; Upgrades
---

### Post by mr-mister on 2017-03-18
Hi, i'm starting my transition from windows to linux. My problem is with the grub menu that does not appear, it boots directly to windows (i can boot ubutu from bios). I've tried reinstalling it manually (error after installing from root: grub-install: error: /usr/lib/grub/i386-pc/modinfo.sh doesn't exist. Please specify -target or --directory) and with boot-repair, witch gave me this url: [http://paste2.org/pNBpUZVB](http://paste2.org/pNBpUZVB) . The thing is that i first tried with linux mint(exactly the same problem), then ubuntu and now i don't know if i just messed up with the partitions, so i'd appreciate any help.

---

### Post by kansasnoob on 2017-03-18
I recently had the same problem:

[https://ubuntuforums.org/showthread.php?t=2355285](https://ubuntuforums.org/showthread.php?t=2355285)

First of all figure out which key you need to press during boot to display the UEFI/BIOS boot options. The two I've most recently encountered are F10 and F11. It varies from one PC/motherboard manufacturer to another.

What I found is it's much easier to manipulate the boot order and/or disable/enable boot options using EasyUEFI from the Windows side:

[http://www.easyuefi.com/index-us.html](http://www.easyuefi.com/index-us.html)

Just be sure to create a backup of the UEFI boot partition before playing with things! I did that using Gparted from an Ubuntu live DVD and copying the entire partition to a flash drive.

Something I'd warn of using EasyUEFI - after selecting a boot entry to move or disable/enable take your time as when you hover your mouse over the vertical column of options it takes a moment for the pop-ups to appear showing you what it's going to do, and there is no additional warning! I personally recommend never removing an entry entirely! I'd only use it to move a boot entry up or down on the list and enabling or disabling boot entries.

Before finding EasyUEFI I just used efibootmgr:

[http://manpages.ubuntu.com/manpages/zesty/man8/efibootmgr.8.html](http://manpages.ubuntu.com/manpages/zesty/man8/efibootmgr.8.html)

---

### Post by mr-mister on 2017-03-18
it worked! very elegant and simple solution. Thanks a million!

---

