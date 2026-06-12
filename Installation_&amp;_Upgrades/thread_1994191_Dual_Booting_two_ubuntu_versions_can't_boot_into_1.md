---
title: "Dual Booting two ubuntu versions: can't boot into 12.04"
date: 2012-06-02
forum: Installation &amp; Upgrades
---

### Post by squireofshire on 2012-06-02
Hi folks,

I was running Ubuntu 11.10 and installed 12.04 on a blank partition of my HD.

I installed 12.04 successfully but when I restarted my computer it loaded into 11.10, not 12.04, and I can't figure out any way to make it boot into 12.04.

I looked at my hard drive with disk utility and my 12.04 partition has the "bootable" checkbox unchecked,  so I tried clicking on it to check it, but that just causes a spinning busy symbol over the partition that never ends.

I would like to be able to boot into both versions of Ubuntu, but I'd even settle with only being able to boot into 12.04 for now. I just can't figure out how.

Any help would be appreciated!

Thanks!

P.S. Both are 64 bit versions of ubuntu

---

### Post by darkod on 2012-06-02
Boot your 11.10, open terminal and post the output of:
sudo fdisk -l
df -h

---

### Post by coffeecat on 2012-06-02
Three points:

1 - Don't bother with trying to set the boot flag on your 12.04 partition - which is what you're doing with the bootable tickbox. Linux doesn't need the boot flag - it makes no difference whatsoever. Only Windows requires the boot flag.

2 - The problem is with your grub menu and how grub (the Ubuntu bootloader) is installed. My guess is that you told the installer to install grub to the 12.04 partition rather than to the mbr of sda, which would mean that you are still using the 11.10 version of grub and, at the moment, the menu is not configured to know about your new 12.04 installation. Try this. Boot into 11.10 and open a terminal. Now run this command:

```
sudo update-grub
```

Reboot, and do you see a grub menu with 12.04 as one of the choices? You can use that to boot into 12.04.

3 - If by chance running update-grub in 11.10 does not help, we need to see an overview of your system so that you can re-install 12.04's version of grub. In Ubuntu 11.10 go to this site:

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

Download and run the boot info script - the instructions are on that page - and post the contents of the RESULTS.txt file between [noparse]```
 and 
```[/noparse] tags to preserve formatting and for clarity. The simplest way of doing this is to highlight the output and then click on the [img]http://ubuntuforums.org/images/editor/code.gif[/img] button in the message toolbar.

There is one error in those instructions. Once you have unpacked it from the tar.gz file, the name of the script is bootinfoscript, not boot_info_script.sh. So, if you have moved the script file to your desktop, the command should be:

```
 sudo bash ~/Desktop/bootinfoscript
```

---

### Post by squireofshire on 2012-06-02
Thanks!

While I was waiting for a response I managed to "fix" my problem by using boot repair's advanced options to change "OS to boot by default" to 12.04.

But after reading this, I tried (from 12.04) "sudo update-grub" and I can boot into both 12.04 and 11.10, which is even better. :) Thanks for the help!

---

