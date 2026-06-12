---
title: "Toshiba L50-A-16HNL: Black screen after selecting Install Ubuntu"
date: 2014-03-24
forum: Installation &amp; Upgrades
---

### Post by Justin_Cromberge on 2014-03-24
I'm running into this problem for a while and tried different solutions. I want to install Ubuntu 12.04 64bit LTS in dual boot alongside with Windows 8.1 Pro N. When I boot the USB or disc and select Install Ubuntu I get a black screen and nothing else happens.

With all four options I get the problem:
Try Ubuntu without installing
Install Ubuntu
Check disk for defects
Run usb stick from Windows

Solutions I tried:
Use a bootable DVD
Use a bootable USB(via different tools and different usb drives)
nomodeset solution

I got the Toshiba L50-A-16HNL (fresh installation of Windows, all drivers up-to-date)
Intel Core i7 4700MQ
Nvidia GeForce GT740M
Standard 5400 rpm disk
8GB ram

Oh, and Secure Boot is disabled.

Hopefully I'm not the only and is someone able to help me, thanks in advance.

---

### Post by ubfan1 on 2014-03-24
Try some more video tweaks for the Nvidia graphics:
For UEFI machines (with a black screen grub (grub-efi)  without any
function key options, like the older grub-pc, edit the grub menu and add
the below options on the "linux" line, then boot with F10 or ctrl-X.

Options for Video problems:

nomodeset
acpi=0
acpi_osi=linux
acpi_backlight=vendor
noalpic
i915.i915_enable_rc6=1
video=1280x1024-24@60
video=VGA-1:1280x1024-24@60

To allow Nvidia hybrid machines to boot.
nouveau.blacklist=1

---

### Post by mörgæs on 2014-03-25
Hi, welcome to the fora.

For new hardware you should use the newest of software. How does it work in a live boot of 13.10, perhaps with the option mentioned above?

---

### Post by Justin_Cromberge on 2014-03-25
First off thanks for the replies. I made an usb drive with 13.10, this made no difference. Then I tried nomodeset, nouveau.blacklist=0. This made no difference either, I need to add those options instead of -- right, in the line quiet splash --? Or have I been putting it in the wrong place?

---

### Post by ubfan1 on 2014-03-26
You can try the options one at a time and maybe in combinations by replacing the "quiet splash", which will allow more error messages to be seen too.

---

### Post by mörgæs on 2014-03-26
If everything else fails you could begin with a [minimal install]("https://help.ubuntu.com/community/Lubuntu/Documentation/MinimalInstall") (text-only) using wired internet access.

When that works you add the Ubuntu desktop with
```
sudo apt-get install ubuntu-desktop
```

---

### Post by fantab on 2014-03-26
On some machines you just need to increase the Display 'brightness', as, by default, the brightness is set to 0.

---

