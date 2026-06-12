---
title: "How to Save Editting at GRUB 1.97 beta4 Boot"
date: 2010-01-13
forum: Installation &amp; Upgrades
---

### Post by huangyingw on 2010-01-13
hello
     I want to realize such purpose:
     Install Ubuntu 9.10 on a removalble USB disk, and then, just simply carry this usb disk to everywhre. So, I could use a same OS, no matter at home or office.
     After installation of Ubuntu 9.10 on my targeted USB disk from my laptop, I unplug and plug this USB disk to my PC. After choosing boot from USB,I could successfully load the GRUB menu.
     But when I choose "Ubuntu, linux....", my PC could not successfully boot to Ubuntu. I guess it might be something wrong with this section ```
set root=(hd0,1)
```. So, I press 'e' at my target option, and entered the edit mode of GRUB.
     But, I don't know how to save my editting.
     And what's more, I am not sure whether this would works, after updating my grub.
     Could someone share his successful experience at this point?

---

### Post by kansasnoob on 2010-01-13
Several options:

[http://www.pendrivelinux.com/](http://www.pendrivelinux.com/)

Personally I don't care to use grub2 on external drives, I always revert to legacy grub because grub2's ability to probe all OS's bugs me:

[http://ubuntuforums.org/showthread.php?t=1298932](http://ubuntuforums.org/showthread.php?t=1298932)

Alternatively you can tweak grub2:

> # Building a Totally Customized Menu: Ok, admit you are a control freak and you want to see only what you build yourself - customized titles, no "memtest86+" and no extra kernels. Here is how you do it:

    * Run sudo update-grub to get the current available kernels.
    * Copy the desired "menuentry" listings from /boot/grub/grub.cfg to /etc/grub.d/40_custom The entry begins with the line starting with "menuentry" and ends with a line containing "}".
    * Add any other "menuentry" items you wish to see on the boot menu.
    * Edit the titles of the "menuentry" line if desired (between the quotation symbols). Do not change the lines following the "menuentry" line. Each entry should start with a "menuentry" line and end with a "}" on the last line.
    * Remove the executable bit from /etc/grub.d/10_linux, /etc/grub.d/20_memtest86+ and /etc/grub.d/30_os-prober
      Removing the executable bit from any file in /etc/grub.d will exclude the file from being included in grub updates.
      Code:

      sudo chmod -x /etc/grub.d/10_linux /etc/grub.d/20_memtest86+ /etc/grub.d/30_os-prober

    * Run "sudo update-grub"
    * The updated /boot/grub/grub.cfg file should now contain only sections for "00_header", "05_debian_theme" and "40_custom".
    * The grub.cfg file will not be updated with the addition of a new kernel. To add a new kernel, make "10_linux" executable, run "sudo update-grub" to refresh the available kernels, and repeat these instructions.


[http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)

---

### Post by brickhead248 on 2010-01-13
what i would do is:

boot ubuntu off a live CD

run the command** sudo fdisk -l** in the terminal to determine the name of your USB drive (should be something like sdc1)

browse the USB disk and find the file menu.lst (if i recall correctly, it should be under **[USB device directory]/boot/grub**)
[B]
back up the menu.lst file[/B]

change the entry for the ubuntu boot option from **root (hd0,0) **to **root (sdc1,0) **[assuming that is the name of your USB disk]

good luck!

---

### Post by brickhead248 on 2010-01-13
> **brickhead248 said:**
> what i would do is:

boot ubuntu off a live CD

run the command** sudo fdisk -l** in the terminal to determine the name of your USB drive (should be something like sdc1)

browse the USB disk and find the file menu.lst (if i recall correctly, it should be under **[USB device directory]/boot/grub**)
[B]
back up the menu.lst file[/B]

change the entry for the ubuntu boot option from **root (hd0,0) **to **root (sdc1,0) **[assuming that is the name of your USB disk]

good luck!
disreagard what i just said, i dont think it would work as grub has a different naming system to unix. SORRY

---

### Post by huangyingw on 2010-01-14
> **kansasnoob said:**
> Several options:

[http://www.pendrivelinux.com/](http://www.pendrivelinux.com/)

Personally I don't care to use grub2 on external drives, I always revert to legacy grub because grub2's ability to probe all OS's bugs me:

[http://ubuntuforums.org/showthread.php?t=1298932](http://ubuntuforums.org/showthread.php?t=1298932)

Alternatively you can tweak grub2:



[http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)
Thank you for providing so much about GRUB2 and the detail about pendirvelinux.
I would prefer to try pendrivelinux first, to see what excitements it would provide to me..

---

### Post by huangyingw on 2010-01-14
> **brickhead248 said:**
> disreagard what i just said, i dont think it would work as grub has a different naming system to unix. SORRY
thank still, this might not works for GRUB2.

---

### Post by huangyingw on 2010-01-14
> **kansasnoob said:**
> Several options:

[http://www.pendrivelinux.com/](http://www.pendrivelinux.com/)

Personally I don't care to use grub2 on external drives, I always revert to legacy grub because grub2's ability to probe all OS's bugs me:

[http://ubuntuforums.org/showthread.php?t=1298932](http://ubuntuforums.org/showthread.php?t=1298932)

Alternatively you can tweak grub2:



[http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)
Hi, jus to make sure I totally understand what is described in pendrive.com. I found that the pendrive's information are all about how to make a usb-boot live CD, but no information on how to install running, and maintain a linux OS in a usb disk.

---

