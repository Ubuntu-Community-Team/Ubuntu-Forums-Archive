---
title: "Grub only loads when booting from SD card"
date: 2011-01-21
forum: Installation &amp; Upgrades
---

### Post by Brendor on 2011-01-21
Hello, Ive installed Ubuntu 10.10 from a SD card (yes my laptop supports booting from SD) and it works fine except the grub does not load. Although I know there are many threads about this Im not sure which one to use because my problem is quite strange. 
Im not pretending I understand how grub works but I find it strange:
When I boot from Hard Drive, it boots into Windows without loading grub (I installed ubuntu to an empty partition along the windows on the same drive), however, when I force booting from the SD card, I get the grub window with all the options as expected - ubuntu, mem check, windows 7. Now Im not sure if its grub loading from this SD card (containing ubuntu) or the card somehow runs the grub that is on the hard drive.

My guess is that the partition containg windows (sda0) is flagged as boot and thus the system doesnt even look after grub when booting, however, when theres the SD card it somehow forces booting the ubuntu partition (sda6).

Any idea what I should do? I can boot into Ubuntu, I can access grub etc. I just cant make it load without having the SD card in my PC

---

### Post by drs305 on 2011-01-21
You need to install Grub to the hard drive MBR. You can do this from the LiveCD or once you have booted into Ubuntu. Assuming your Ubuntu hard drive is sda:

If you are in your normal Ubuntu install:
```
sudo grub-install /dev/sda
sudo update-grub

```
If you have booted the LiveCd:
```
sudo mount /dev/sda1
sudo grub-install --root-directory=/mnt /dev/sda
# After you have rebooted into Ubuntu:
sudo update-grub

```

Other than the mounting command, do not use the partition number in the install commands.

---

### Post by oldfred on 2011-01-21
Each bootable device has an MBR under MBR/msdos partitioning. So you have the windows boot loader in the MBR of sda and windows will only boot windows. Grub does not use the boot flag. 

It then sounds like you have installed grub to the MBR of the SD card. The MBR is tiny and all it does is identify where to jump to continue booting. 

If you want to see what is where with SD card installed. You can run from your Ubuntu or liveCD.

Boot Info Script courtesy of forum member meierfra
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste results.txt, then highlight entire file and click on # in edit panel(code tags) to make it easier to read.
Or You can generate the tags first by pressing the # icon in the post's menu and then paste the contents between the generated [ code] paste here [ /code] tags.

---

### Post by Brendor on 2011-01-21
Thanks drs305, that one worked, its funny though because I tried the sudo grub-install before but I didnt update it afterwards. Also thanks to oldfred, I didnt need to use that but at least you gave me the idea what to do if the first solution didnt work. :)
Flagging this as solved.

---

