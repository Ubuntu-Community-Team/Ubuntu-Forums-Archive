---
title: "xubuntu qemu embedded usb?"
date: 2007-01-22
forum: Installation &amp; Upgrades
---

### Post by revoltism on 2007-01-22
Hi i am trying to make an xubuntu qemu-embedded usb installation. I have almost got it working. I took the DSL-embedded install instruction and changed som of the input. I think it maybe has something with the image of the "harddrive" or "installed harddrive (the img named KNOPPIX on DSL)" that i flunked up some how. 

To describe the problem is too much to write so my only question is if someone els have tried and got it working?

Would love to have xubuntu embedded on my 4G USB so i could use it at work, witch use windows and have a no install policy.

---

### Post by revoltism on 2007-01-22
Maybe it was not so good of an idea to use the DSL-embedded insructions. I have decided to first embed a xubuntu img on the computer then copy/paste to the usb, when i coming home from work. 
 
I will use the command-line install as someone recomended in another post and...

```
sudo aptitude install x-windows-system-core xfce4
```

so i get as minimal as i can.

---

### Post by revoltism on 2007-01-22
Ok, guy's this is my first try to make a howto.. so bare with me..

I bought a cheap Transcend JetFlash V10 4 gig USB stick and decided to make it emulate linux. I needed this as I have Windows XP at work with a no install policy. 
First i tried an DSL-embedded install witch worked as a charm but I love Ubuntu so i decided to try Xubuntu. I could not find a howto so here it is.


#1#

First you need to download the latest 
[xubuntu-feisty-alternative-i386 herd2]("http://cdimage.ubuntu.com/xubuntu/releases/feisty/herd-2/")
[qemu-0.8.2-windows]("http://fabrice.bellard.free.fr/qemu/download.html")
[syslinux-3.31]("http://www.kernel.org/pub/linux/utils/boot/syslinux/").

#2#

I don't know if syslinux acctually is needed if you you only want to emulate as it is an alternative bootloader. Use only if you like boot from usb.
In the command promt (change X: to youre USB drive letter) and restart.
```
syslinux.exe X:
```


#3#

Format the USB to fat32 (right click on usb in explorer).
Extract and copy/paste the qemu folder to the USB flash drive and make a hda.img (virtual hdd).

In the command promt (win+r and cmd):
```
qemu-img.exe create -f qcow hda.img 3800M
```

Install Xubuntu to the virtual drive (hda.img)

Still in command promt:
```
qemu.exe -L \qemu -cdrom path-to-xubuntu-cd-img.iso -hda hda.img -m 256 -boot d
```

"-boot d" is only for booting the cdrom later you change it to "-boot c" whitch are to boot from the virtual hdd. I used a command-line system install to get it minimum (350 MB without X windows etc). This is all written [here]("https://help.ubuntu.com/community/Installation/LowMemorySystems?highlight=%28command-line%29%7C%28system%29"). I choosed Thunar, Dillo, Firefox and XFCE (ofcourse). I picked this cause i like blingbling and don't mind little lagg (if to much i go console). not rekommended for slower boxes. 


#4#

Make a xubuntu.bat file and put it in the root of youre USB.

In Notepad and rename to xubuntu.bat:
```
REM Start qemu on windows.
@ECHO OFF

START qemu\qemu.exe -L qemu\ -no-kqemu -localtime -hda qemu\hda.img -cdrom path-to-xubuntu-cd-img.iso -m 256 -boot c

CLS
EXIT
```

In the below Qemu link you can read what all the options means. If you get in to troubble delete the -cdrom with path and you might want to change -m 256 to 64 or 128 the "-m" indicates ram.


Sources i had help from:
[Qemu Official]("http://fabrice.bellard.free.fr/qemu/qemu-doc.html#SEC12")
[QemuOnWindows]("http://kidsquid.com/cgi-bin/moin.cgi/QemuOnWindows#head-4d3f2df4b7b962a7c2e4110dd7d4a2850bbaa0d8")

---

### Post by tenjin1 on 2007-01-24
Hi there

Sounds interesting! I've been trying to do a ubuntu dapper live on usb stick using persistance mode but it hasn't been working for me :(  ANyways I would love ubuntu to use qemu!

My question is:
You are using a 4gig USB..I only have a 1GB USB pendrive. How much will this install use? Will I be able to use 1gig?

---

### Post by revoltism on 2007-01-25
I have only a basic install now. xubuntu with dillo and firefox and it's about 880 megs. so it's possible for you but not recommended. 

bigger USB's are not that much expensive these days. I bought mine for about $65

---

### Post by embus on 2007-02-13
Take a look at USBware it's [**embedded usb software**]("http://www.jungo.com/usbware_embedded_usb_solution.html") and it helped me to solved some problems.

---

### Post by canotonic on 2007-03-14
I couldn't get this tutorial to work for me. Seems to be missing steps.

I ended up using and highly recommend the step by step tutorial found [[COLOR="Blue"]**here**[/COLOR]]("http://www.pendrivelinux.com/2007/03/13/run-ubuntu-from-windows-via-a-portable-usb-hard-drive/") which worked wonderfully. :KS

---

