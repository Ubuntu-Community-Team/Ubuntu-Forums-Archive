---
title: "Ubuntu 14.04.2 USB installation error “mounting /dev/loop0 (…) failed&quot;"
date: 2015-04-18
forum: Installation &amp; Upgrades
---

### Post by idiotenkonto on 2015-04-18
Hey,
Im pretty new here, sorry for any mistakes.

[COLOR=#111111][FONT=Ubuntu]Im trying to install Ubuntu on my PC for gaming, so I downloaded Ubuntu 14.04.2 and created a live stick with LiLi. When I try to boot with the stick and click on install Ubuntu, I always get the following error after a bit of loading:[/FONT][/COLOR]

Busybox 1.21.1 (Ubuntu 1:1.21.0-1ubuntu1) built-in shell (ash)

Enter "help" (...)

(initramfs) mount: mounting /dev/loop0 on //filesystem.squashfs failed: invalid argument
can not mount /dev/loop0 (...) on //filesystem.squashfs
[COLOR=#111111][FONT=Ubuntu]Specs:[/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu]AMD 6400k
8GB RAM
R7 270x[/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu]Hash and USB stick are okay, nothing defect. I even tried Ubuntu 12.02 (?), same error.

I hope somebody can help me, I want to start gaming on Ubuntu because it's unstable on windows. I tried askubuntu, but nobody responded.

[/FONT][/COLOR]

---

### Post by idiotenkonto on 2015-04-18
Nobody?

---

### Post by sudodus on 2015-04-18
[COLOR=#111111][FONT=Ubuntu]Is 'R7 270x[/FONT][/COLOR]' Radeon graphics or something else? The problem might be graphics or the wifi (if you have wifi).

Anyway, please describe your hardware with as many details as possible. It helps us help :-)

Please try with some boot options. You can start with **nomodeset**. See the following links.

[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

There might also be some general boot problem, that might be helped by Boot Repair. Start by creating a BootInfo summary and waiting for the response before trying to repair.

[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

Are you running in UEFI mode? In that case, have a look at the following link and links from that link

[https://help.ubuntu.com/community/Installation/FromUSBStick#UEFI](https://help.ubuntu.com/community/Installation/FromUSBStick#UEFI)

The following link contains some general tips (try several linux distros, flavours and versions live until you find something that works in your computer).

[Try Ubuntu (Kubuntu, Lubuntu, Xubuntu, ...) before installing it]("http://ubuntuforums.org/showthread.php?t=2230389")

---

### Post by idiotenkonto on 2015-04-19
> **sudodus said:**
> [COLOR=#111111][FONT=Ubuntu]Is 'R7 270x[/FONT][/COLOR]' Radeon graphics or something else? The problem might be graphics or the wifi (if you have wifi).

Anyway, please describe your hardware with as many details as possible. It helps us help :-)



Okay:
AMD 6400k 4x 4GHz
Biostar Hi-Fi A88W Mainboard
8Gb Ballistix RAM
Sapphire R7 270x 2GB (Yep, its the graphics card)

external:
Logitech mouse/keyboard (idk which one)
Netgear WiFi stick (n300 maybe?)
headset

[B]
edit:[/B] Maybe I should add that I have Windows 7 installed on my HDD and made a partition for Ubuntu

I will look trough all these links later on, I dont have access to the PC right now.

---

### Post by sudodus on 2015-04-19
We know more about your computer now :-)

I have very little experience of AMD/ATI/Radeon graphics, so [COLOR=#ff0000]I hope someone else will chip in and help[/COLOR] you with that.

There might also be problems with the wifi stick. You can boot when the Netgear WiFi stick is unplugged, and if it makes a difference, look more into the linux compatibility of that wifi device.

---

### Post by idiotenkonto on 2015-04-19
I already tried unplugging the WiFi stick, no difference. 

Who do you think could help me with the Graphics card? I really dont think that its the problem, considering that the error says "mount... invalid argument". Im a complete newbie at linux, just tell me if im wrong.

---

### Post by sudodus on 2015-04-19
I think you are right there :-) Obviously, I did not read your opening post carefully enough.

There may be something wrong with the installer. Try another tool to flash the iso file to the pendrive. There are several good tools. In windows you can try ***Win32 Disk Imager*** or ***Unetbootin*** according to the following links

[https://wiki.ubuntu.com/Win32DiskImager/iso2usb](https://wiki.ubuntu.com/Win32DiskImager/iso2usb)

[https://help.ubuntu.com/community/Installation/FromUSBStick#Unetbootin-1](https://help.ubuntu.com/community/Installation/FromUSBStick#Unetbootin-1)

and if you already have linux, read the whole help page

 [https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)

(I made ***mkusb*** and find it reliable, but as you can see, there are many tools, that give good results most of the time.)

---

### Post by sudodus on 2015-04-19
> **idiotenkonto said:**
> 
Who do you think could help me with the Graphics card?.

Let us wait and see. There are many people around, who may read this thread, and know enough about AMD graphics to help.

---

### Post by idiotenkonto on 2015-04-19
Tried Ubuntu 12.04.5 desktop i386 version. It went to the Ubuntu laoding screen with the dots and loaded forever. I dont know...

---

### Post by sudodus on 2015-04-19
With your relatively modern computer, I think you have better chances with Ubuntu 14.04.1 LTS, 14.04.2 LTS, 14.10 or the final testing version Ubuntu Vivid to become 15.04 on Thursday.

Did you try another tool to create the USB boot drive? See the links in post #7.

---

### Post by sudodus on 2015-04-19
Did you try with boot options? See the first link in post #3.

---

### Post by idiotenkonto on 2015-04-19
I tried Unetbootin, same error. But I didnt look at boot options. Going to try it later.

---

### Post by sudodus on 2015-04-19
Come back and ask, if you can't find out how to enter the boot options.

Good luck :-)

---

