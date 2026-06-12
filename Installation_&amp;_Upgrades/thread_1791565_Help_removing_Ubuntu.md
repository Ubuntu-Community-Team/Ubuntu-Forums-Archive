---
title: "Help removing Ubuntu"
date: 2011-06-27
forum: Installation &amp; Upgrades
---

### Post by razer.aj on 2011-06-27
Hey guys, a few days ago I had installed Fedora over my Ubuntu. Then I suddenly felt like removing it so I booted into windows and managed to empty out the partition but I didn't extend my c drive to occupy the leftover space because I suddenly realized that I no longer had the Fedora boot loader when I did so. Luckily the boot loader remained but I felt like switching back to ubuntu. So to solve the problem I decided to reinstall Ubuntu to get grub as the boot loader and to occupy the space left after the removal of Fedora.

Now I don't want Ubuntu anymore. I want to remove Ubuntu along with grub but keep Windows. I heard that by doing so the system won't be able to boot since the default boot loader was replaced by grub. They say the problem can be solved by inserting the windows 7 install CD and then choosing the repair option but the problem is I don't have a Windows 7 install disc. Can some one give me a guide on how to completely remove Ubuntu and grub and regain the partition and get Windows to boot without having a copy of the install disc. Please..... In need of great help... Please please please*

---

### Post by jerrrys on 2011-06-27
just make your own recovery cd

[http://www.google.com/search?client=ubuntu&channel=fs&q=windows+7+recovery+cd&ie=utf-8&oe=utf-8](http://www.google.com/search?client=ubuntu&channel=fs&q=windows+7+recovery+cd&ie=utf-8&oe=utf-8)

---

### Post by YesWeCan on 2011-06-27
All you need to do is restore the standard MBR before you delete Ubuntu.

[moan]Why doesn't Canonical have a menu item on the live CD to do just this???[/moan]

Boot Ubuntu. Download Lilo and install the Lilo standard MBR:
[COLOR=DarkGreen]sudo apt-get install lilo
sudo lilo -M /dev/sda mbr[/COLOR]  (assuming your disk is named sda: check in System/Admin/Disk utility)
Then reboot into Windows and use Windows to erase Ubuntu.

---

