---
title: "Problem upgrading from 10.04 LTS to 12.04 LTS - get grub prompt"
date: 2013-02-04
forum: Installation &amp; Upgrades
---

### Post by GiancarloRed on 2013-02-04
I am a Linux newbie who has tried to update from Ubuntu 10.04 LTS (which I´ve used for 3 years) to 12.04 LTS on my Dell desktop using update manager, thought all was working well, even though my HD partition desktop is small (just 20gb) and commentary stated short disk space. I am now faced with the sole grub prompt, GNU Grub version 1.98-1ubuntu13 and the comment ¨Minimal BASH-like editing...¨. What do I do from here?  Could anyone please advise? It´s my main computer I am worried I won´t be able to access my data (that I have not backed up fully). Can I try to go back to 10.04 or boot from USB?

---

### Post by schragge on 2013-02-04
Try this.
```

grub> search.file /boot/grub/grub.cfg root
grub> set prefix=($root)/boot/grub
grub> insmod normal
grub> normal

```

---

### Post by GiancarloRed on 2013-02-07
Thanks for the advice, have tried what you suggested but get an error message(s)

error: no module specified
error: no suitable mode found
error: unknown command ´terminal´
syntax error
incorrect command
grub>

Have I done something wrong?

What else could I try?

All help really appreciated, open to try solutions.

---

### Post by GiancarloRed on 2013-02-07
Should I try to boot via usb with 12.04?  Will I be able to access my data - that is my primary concern?

---

### Post by PowerBarry43 on 2013-02-07
Hi

You could boot from a livecd and chroot in but i find it's easier to download a supergrub boot disk

[http://www.supergrubdisk.org/category/download/supergrub2diskdownload/](http://www.supergrubdisk.org/category/download/supergrub2diskdownload/)

you just download the iso about 7mb (first mirror seems broken but the second one works) burn it to a cd and boot from it, choose "detect any os" and it's probably the top one if you have a single boot system.

You have now booted into your new install
from here we can open up a terminal (CTRL+ALT+T) and run

```
sudo grub-install /dev/sda
sudo update-grub
```

You should now be able to reboot and get into your system.

Hope this helps!

Barry

---

### Post by GiancarloRed on 2013-02-11
Thanks for advice, have booted into my PC using live USB and initially noted most of my data was there (via OS drive), for whatever reason it now shows much less stuff. I would like to backup my data say to USB but now cannot see most of it, though I presume the folders and data are still there. How do I check this? I installed boot repair via sudo (following advice here [https://help.ubuntu.com/community/Boot-Repair#A2nd_option_:_install_Boot-Repair_in_Ubuntu](https://help.ubuntu.com/community/Boot-Repair#A2nd_option_:_install_Boot-Repair_in_Ubuntu)) but it asks me to backup data before doing the repair, but how do I do that? There is no system admin in the Live USB mode. At the moment I can only boot via USB-HDD as the prior option to boot from HDD (and boot menu) has disappeared. Sorry for the extended question but am just stuck again. I know I can proceed to install 12.04 alongside other OSes (10.04, and Vista) and in theory retain respective files and data (and have 200 Gb free space on the HD) but am thinking I back up first. I still want the option to boot into 10.04 assuming it is possible. Happy to remove Vista unless not advisable. Should I just go ahead and repair the boot as you say via supergrub? Any advice appreciated.

---

### Post by oldfred on 2013-02-12
Boot-Repair should fix grub issues if that is all the issues you have. Or Supergrub should let you boot into your install. 

But best to backup /home including the hidden files first. You should be just able to copy & paste from Nautilus on live version. If not from terminal use superuser. Do not modify anything in this mode as you can do anything as superuser.
gksudo nautilus

Or post link to BootInfo report from Boot-Repair.

---

