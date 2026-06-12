---
title: "Dual booting on Ryzen setup"
date: 2018-09-29
forum: Installation &amp; Upgrades
---

### Post by crossoni on 2018-09-29
I was about to follow this guide: [https://itsfoss.com/install-ubuntu-1404-dual-boot-mode-windows-8-81-uefi/](https://itsfoss.com/install-ubuntu-1404-dual-boot-mode-windows-8-81-uefi/) to dual boot Windows 10 and Ubuntu, but then I found other stuff that was important for installing with this setup. First I found out that I should download ubuntu EFI only disc, then I found out that I have to change [COLOR=#333333][FONT=Ubuntu]Compatibility Support Module settings in BIOS to use UEFI when booting and after that I found out that Ryzen 5 1600 crashes on Ubuntu because of a rare bug. Can I use my current setup for dual booting and if so, is there something else that I should be aware of?

My setup:
Ryzen 5 1600
ROG Strix B350-F Gaming
GTX 1060 6GB
[/FONT][/COLOR]Corsair Vengeance DDR4 16 GB 3200Mhz[COLOR=#333333][FONT=Ubuntu]
[/FONT][/COLOR]

---

### Post by yancek on 2018-09-29
The link below goes to the official Ubuntu documentation on dual booting with windows 10 so I would suggest you use that as a guide.

[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

---

### Post by oldfred on 2018-09-29
Make sure you have newest UEFI from motherboard vendor.
You may need boot parameters. And possibly add newer kernel.
What video card? If nVidia you will need nomodeset.

       Asus B350M-A needs newer kernel that 18.04 default
[https://ubuntuforums.org/showthread.php?t=2391892](https://ubuntuforums.org/showthread.php?t=2391892)
[https://ubuntuforums.org/showthread.php?t=2390660&p=13799816#post13799816](https://ubuntuforums.org/showthread.php?t=2390660&p=13799816#post13799816)
MSI Tomahawk B350 with Ryzen R5 1600 New UEFI required
[https://ubuntuforums.org/showthread.php?t=2390475](https://ubuntuforums.org/showthread.php?t=2390475)
ASUS PRIME B350M-E major issues
[https://www.phoronix.com/scan.php?page=news_item&px=AMD-Raven-Ridge-Mobo-Linux](https://www.phoronix.com/scan.php?page=news_item&px=AMD-Raven-Ridge-Mobo-Linux)
ryzen acpi=off only 1 cpu, needs nomodeset & then nVidia driver instead
[https://askubuntu.com/questions/951630/fix-ubuntu-16-04-issue-with-gigabyte-ga-ab350-motherboard-and-amd-ryzen-cpu](https://askubuntu.com/questions/951630/fix-ubuntu-16-04-issue-with-gigabyte-ga-ab350-motherboard-and-amd-ryzen-cpu)
Asus Prime X399-A  with AMD Ryzen 1950X  Ubuntu 16.04.3
[https://ubuntuforums.org/showthread.php?t=2380798](https://ubuntuforums.org/showthread.php?t=2380798) 
    
General UEFI install instructions in link in my signature.

---

### Post by crossoni on 2018-09-30
> **yancek said:**
> The link below goes to the official Ubuntu documentation on dual booting with windows 10 so I would suggest you use that as a guide.

[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)
I followed this guide, but I can't get it working. I am trying to test ubuntu before installing it, but I can't even launch it. If I try booting it from USB 2.0 port, I get error "Unable to find a medium containing a live file system" and if I try booting it from dvd, it just loads a black screen. I tested to boot it using USB on another computer which does not have UEFI and it worked like a charm. What can I do? I have disabled secure boot and fast startup and made CSM only use UEFI.

---

### Post by yancek on 2018-09-30
Did you try the suggestions made above by oldfred?

---

### Post by crossoni on 2018-09-30
Aren't I supposed to do most of them after I have installed Ubuntu? For example, don't I have to be inside Ubuntu to change kernels? Also I tried to change command line parameters in Grup to acpi=nomodeset, but I can't use character "=" since I have Nordic keyboard. I went through all of my buttons and none of them were =.

---

### Post by Dennis N on 2018-09-30
If as you say "Ryzen 5 1600 crashes on Ubuntu because of a rare bug" why not try installing another Linux distro? You may just need latest kernel - suggestions: 1) try Fedora which is using kernel 4.18, or 2)
easiest distro I know of to install and switch kernels and have installed multiple kernels is Manjaro which has GUI kernel manager to select and install from a list. It can also supply 4.18 kernel. I use both on other machines.

---

### Post by crossoni on 2018-09-30
> **Dennis N said:**
> If as you say "Ryzen 5 1600 crashes on Ubuntu because of a rare bug" why not try installing another Linux distro? You may just need latest kernel - suggestions: 1) try Fedora which is using kernel 4.18, or 2)
easiest distro I know of to install and switch kernels and have installed multiple kernels is Manjaro which has GUI kernel manager to select and install from a list. It can also supply 4.18 kernel. I use both on other machines.
Alright I'll try those and see if I can get them working. Thanks for the help!

---

### Post by oldfred on 2018-09-30
While always better to use a LTS version, and best not to use a version not yet released, but Ubuntu 18.10 now has the newer kernel 4.18. I have it installed, just to see what has changed.

I might make two / (root) partitions, so you could go back to 18.04 when its next update in Feb which will be a newer kernel. But then keep data separate with either /home or data in separate partition(s).

---

