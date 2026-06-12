---
title: "problem trying to boot from usb"
date: 2018-01-29
forum: Installation &amp; Upgrades
---

### Post by ivanlrojales on 2018-01-29
Hi everyone, I have installed ubuntu 17.10 in my laptop and now I would like to unistall it and reinstall windows 10. I have downloaded the windows 10 iso and I have done 3 bootable usb's but any of them is recognized at booting. Could you help me and tell me how to do this bootable usb? I dont know which filesystem is required to be able to boot from grub. Thank you!! I use the uefi bios option*.

---

### Post by westie457 on 2018-01-29
Hi ivanlrojales, what did you use to create the bootable usb sticks?

Are you pressing a key to get to the one-time boot menu to select the usb to boot from?

---

### Post by ivanlrojales on 2018-01-29
I open the windows iso with the disk image writer and I install it in my usb. When I reboot the laptop I enter the bios and change the boot order. But it doesnt appear.

---

### Post by yancek on 2018-01-29
I haven't use disk image writer but, I would be surprised if it could be use to create a 'windows' bootable usb.  
Have you tried a windows forum on how to create a bootable usb?  Do you have a windows computer available, it would seem that would be easier.  I created a bootable windows 7 & 10 bootable usb with instructions from the link below, not a simple process like using rufus or unetbootin.

[http://onetransistor.blogspot.ch/2014/09/make-bootable-windows-usb-from-ubuntu.html](http://onetransistor.blogspot.ch/2014/09/make-bootable-windows-usb-from-ubuntu.html)

You could skip the part about Grub and just create an entry from the Ubuntu Grub to boot.

---

### Post by westie457 on 2018-01-29
Having tried a few experiments and had them all fail I agree with yancek. The link s/he provided is a workable solution. It is quite possible I have tried this in the past and it works.

There is another option available here [http://www.webupd8.org/2017/06/tool-to-create-bootable-windows-usb.html](http://www.webupd8.org/2017/06/tool-to-create-bootable-windows-usb.html) 
I have not tried this yet so cannot confirm whether it works or not.

---

### Post by C.S.Cameron on 2018-01-29
Microsoft has a tool for making a USB Windows installer:

[https://www.microsoft.com/en-us/download/windows-usb-dvd-download-tool](https://www.microsoft.com/en-us/download/windows-usb-dvd-download-tool)

---

