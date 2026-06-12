---
title: "Install ubuntu to flash drive problem"
date: 2011-01-27
forum: Installation &amp; Upgrades
---

### Post by Sankou on 2011-01-27
What I'm trying to do is fully install ubuntu to a flash drive. I tried booting to a live cd and installing to the flash drive but it didn't work the way I wanted it to. It erased my windows mbr and replaced it. It would always boot to the grub and then I would have to choose my os. Windows 7 is on my hard drive by the way, I want to keep it untouched. What I would like is just to be able to boot to a full installation from the flash drive. I don't want the mbr erased again. That was kinda scary... the system was only able to boot when the flash drive was in. It couldn't even boot to windows without the flash drive. I've been searching everywhere and cant find a solution. Everything I found is just how to make a live usb. But I want to be able to make full use of the OS. Thanks in advance for any help!

---

### Post by sikander3786 on 2011-01-28
Welcome to the forums :-)

So, I hope you've already repaired your HDDs MBR for Windows and are now able to boot Windows without any problems (??).

If you want to make full use of your USB drive as a HDD, you can do a full install of Ubuntu to the USB drive. For safety, follow the steps below.

[http://ubuntuforums.org/showpost.php?p=9589064&postcount=7](http://ubuntuforums.org/showpost.php?p=9589064&postcount=7)
courtesy of forum member *C.S. Cameron*

If you haven't still fixed the MBR for Windows, you can do it from Windows install/repair disc. See here.

[http://www.sevenforums.com/tutorials/20864-mbr-restore-windows-7-master-boot-record.html](http://www.sevenforums.com/tutorials/20864-mbr-restore-windows-7-master-boot-record.html)

Once you've install Ubuntu to your USB drive, you can add Windows to the Grub menu so that even when the USB drive is plugged in, you'll have a choice to boot Windows and don't need to switch boot devices for that. Connect both your HDD and USB drive. Boot Ubuntu and from Applications > Accessories > Terminal:

```
sudo update-grub
```

This will add Windows to Grub menu and it won't mess up your Windows MBR. Just detect and add Windows ;-)

---

### Post by Sankou on 2011-01-28
I was able to fix the windows mbr, yes. But what I'm looking for is a way to boot to ubuntu just like I would if I installed with wubi. Through the windows os selector. Not the grub! If I do it through the grub, I can't boot to windows with out the flash drive in. So if I loose the flashdrive- which seems like something I'd do- I can't get on my computer anymore. I don't want that to happen.

---

### Post by Sankou on 2011-01-28
A lot of sites tell me I can install onto the flash drive with usb-creator and things like that. But they make live usb drives. I cant save or edit anything. Is there a way I can install to the flash drive like that, but be able to save things and add new packages?

If I remove my windows hard drive before the install, will it just treat the flash drive as it's own hard drive on boot? Like the way it would if I install it on my main hard drive??

It seems like I could do that and just select boot from flash drive in the cmos. Then it would boot to it independently. 

I don't want my main hard drive touched at all...

---

