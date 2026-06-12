---
title: "Each method I try to make a kodibuntu usb (using ubuntu) results in a diffrnt err msg"
date: 2015-07-20
forum: Installation &amp; Upgrades
---

### Post by shaansweb on 2015-07-20
Hello,


I am trying to make a kodibuntu live usb so I can install it on my old computer. I am trying to use ubuntu to make the usb. However, every method I try has a different error message. I have downloaded the 32 bit ver from [here]("http://mirrors.kodi.tv/releases/kodibuntu/") and have confirmed the hash is correct.


**Using startup disk creator**


When I use the built-in startup disk creator in ubuntu, I get the following error:


"Failed to load COM32 file vesamenu.c32"


and then I get a prompt that says "boot:" but I don't know any commands. I tried to solve this using [this]("http://www.ajopaul.com/2014/10/21/linux-usb-boot-disk-error-failed-to-load-com32-file-menu-c32/") tutorial to no avial.


**Using UNetBootin**


When I use unetbootin to create the disk, I get a menu that has "UNetBootin" as a header and options like install, try without installing, etc. However, selecting any of these options causes by PC to reboot and leads me back to the same menu.


**Using the command: "sudo dd bs=4M if=kodibuntu-14.0rc-helix_i386.iso of=/dev/sdb1"**


But I get the error: isolinux.bin missing or corrupt




Any tips on how to solve this would be greatly appreciated

---

### Post by Vladlenin5000 on 2015-07-20
[http://kodi.wiki/view/HOW-TO:Install_KodiBuntu_from_a_USB_drive](http://kodi.wiki/view/HOW-TO:Install_KodiBuntu_from_a_USB_drive)

---

### Post by shaansweb on 2015-07-20
I've seen this. For ubuntu, this just says to use the built in startup disk creator tool. As I said, I get the following error with this message: "[COLOR=#000000]"Failed to load COM32 file vesamenu.c32"

Any clue on why this could be?[/COLOR]

---

### Post by PaulW2U on 2015-07-20
> **shaansweb said:**
> I've seen this. For ubuntu, this just says to use the built in startup disk creator tool. As I said, I get the following error with this message: ""Failed to load COM32 file vesamenu.c32"

That looks like a bug which still seems to be affecting some releases of Ubuntu but the error is slightly different to what I've seen before.

[https://bugs.launchpad.net/ubuntu/+source/usb-creator/+bug/1325801/comments/103](https://bugs.launchpad.net/ubuntu/+source/usb-creator/+bug/1325801/comments/103)

Does "type live and press enter" work for you?

---

### Post by shaansweb on 2015-07-20
nope. It just reboots and takes me back to the same screen. I also tried all three methods again with a different flash drive and got the same results, so I know the flash drive is not at fault

---

### Post by shaansweb on 2015-07-23
If anybody else finds this page looking for a solution, I just went with openelec instead. I realized that the iso I has was a release candidate, so it's probably a bug that hasn't been worked out yet. I have a 32 bit machine and there aren't any 32 bit releases (as of writing)

---

### Post by sudodus on 2015-07-23
I suggest that you try another tool to make your USB boot drive, for example mkusb

[https://help.ubuntu.com/community/mkusb](https://help.ubuntu.com/community/mkusb)

You find several alternatives at the following link

[Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)

***Edit:*** The above instructions apply if you have a 'full iso file' to install from. I tested and ***mkusb*** can install **kodibuntu-14.0rc~helix_i386.iso** to a working USB boot drive.

If you have Ubuntu, you can also install Kodi into that system via a PPA, according to the instructions at the Kodi web page.

```
sudo apt-get install software-properties-common
sudo add-apt-repository ppa:team-xbmc/ppa
sudo apt-get update
sudo apt-get install kodi
```

---

