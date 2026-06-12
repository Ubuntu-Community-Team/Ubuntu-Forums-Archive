---
title: "Changing what OS is on my USB"
date: 2012-12-21
forum: Installation &amp; Upgrades
---

### Post by RadicaX on 2012-12-21
So I have a USB I used to change my computer's OS to Ubuntu 11.10. And have Loved it. Now I have a friend though who wants to make the switch from windows to Linux. They run a laptop though, so I was thinking it would be better if I changed the OS to a lighter one than Ubuntu for them. Like Xubuntu, or Lubuntu. But I do not really want to go out and just buy a new USB. And it would be nice if I could just rewrite the one I have Ubuntu on.

My question is, would this have any negative effects? Like Can I only do it a set amount of times with my USB? Another note, my computer is 7 years old at the least. And I have ran Ubuntu fine. On a 32 bit machine I mind you. Their Laptop is newer though, with Windows 7. (So not so new it has that windows 8 on it or anything.) And is 64 bit. Heck, I think They even have more ram than I do! Their laptop is a Acer of some odd sorts. What OS would you recommend? They plan on mostly doing things like facebook, and or ebay. So no need to worry about gaming as far as that goes.

Thanks in advance.

---

### Post by lykwydchykyn on 2012-12-21
Check out multisystem, it's a program that lets you put as many Linux live CDs as you want (or can fit) on a USB device.  I've used it for years, it works great (the website is in french, but you can translate it using the drop-down menu about halfway down on the right side).

[http://liveusb.info/dotclear/](http://liveusb.info/dotclear/)

---

### Post by haqking on 2012-12-21
> **lykwydchykyn said:**
> Check out multisystem, it's a program that lets you put as many Linux live CDs as you want (or can fit) on a USB device.  I've used it for years, it works great (the website is in french, but you can translate it using the drop-down menu about halfway down on the right side).

[http://liveusb.info/dotclear/](http://liveusb.info/dotclear/)
**edit: ignore me ;-)[]("http://tinyurl.com/bsjx6hz")**

---

### Post by haqking on 2012-12-21
> **lykwydchykyn said:**
> Check out multisystem, it's a program that lets you put as many Linux live CDs as you want (or can fit) on a USB device.  I've used it for years, it works great (the website is in french, but you can translate it using the drop-down menu about halfway down on the right side).

[http://liveusb.info/dotclear/](http://liveusb.info/dotclear/)

Dont you have to pay for that ?

This is free [http://www.pendrivelinux.com/yumi-multiboot-usb-creator/](http://www.pendrivelinux.com/yumi-multiboot-usb-creator/)

---

### Post by sudodus on 2012-12-21
> **RadicaX said:**
> So I have a USB I used to change my computer's OS to Ubuntu 11.10. And have Loved it. Now I have a friend though who wants to make the switch from windows to Linux. They run a laptop though, so I was thinking it would be better if I changed the OS to a lighter one than Ubuntu for them. Like Xubuntu, or Lubuntu. But I do not really want to go out and just buy a new USB. And it would be nice if I could just rewrite the one I have Ubuntu on.

[COLOR=Red]My question is, would this have any negative effects? Like Can I only do it a set amount of times with my USB? [/COLOR]Another note, my computer is 7 years old at the least. And I have ran Ubuntu fine. On a 32 bit machine I mind you. Their Laptop is newer though, with Windows 7. (So not so new it has that windows 8 on it or anything.) And is 64 bit. Heck, I think They even have more ram than I do! Their laptop is a Acer of some odd sorts. [COLOR=RoyalBlue]What OS would you recommend? [/COLOR]They plan on mostly doing things like facebook, and or ebay. So no need to worry about gaming as far as that goes.

Thanks in advance.
[COLOR=Red]Negative effects: Not really :-)

If you install and run a 'normal linux OS' onto a USB pendrive, it will wear, but it can stand many read/writes, and it is no problem to reuse it several times with new files, for example new live [KLX]Ubuntu systems.

[COLOR=RoyalBlue]What OS: Let them try several of those flavours of Ubuntu, either with one after another on the pendrive or as suggested by [/COLOR][/COLOR][COLOR=RoyalBlue]lykwydchykyn, with all of them using multisystem, if there is space enough on the pendrive.

An alternative is to install one system, and then install the other desktop environments

for example 'vanilla' Ubuntu and add

```
sudo apt-get install kubuntu-desktop
sudo apt-get install lubuntu-desktop
sudo apt-get install xubuntu-desktop

```You select the desktop environment at the login screen.
[/COLOR]

---

### Post by lykwydchykyn on 2012-12-21
> **haqking said:**
> Dont you have to pay for that ?

This is free [http://www.pendrivelinux.com/yumi-multiboot-usb-creator/](http://www.pendrivelinux.com/yumi-multiboot-usb-creator/)

No, multisystem is free.  They have several products to support the project, but the actual software is free. They even have a deb repository.

The site is laid out poorly, so you have to poke around to find install instructions, just look down the menus on the right.

---

### Post by haqking on 2012-12-21
> **lykwydchykyn said:**
> No, multisystem is free.  They have several products to support the project, but the actual software is free. They even have a deb repository.

The site is laid out poorly, so you have to poke around to find install instructions, just look down the menus on the right.

OK fair one, I took a cursory glance and saw prices that was all.

I use YUMI anyways which works the same way.

Cheers

---

### Post by ajgreeny on 2012-12-21
I am doing just a simple multiboot USB drive with 7 ISOs on it, all of which will boot without a problem by following the info at [http://ubuntuforums.org/showthread.php?t=1288604](http://ubuntuforums.org/showthread.php?t=1288604)

It is now a bit old, but as far as I'm aware will still work if you use the grub version from 12.10, instead of from the version I used, either 10.04 or 12.04, I can't remember which.

All the ISOs I use are ubuntu family, ie based on ubuntu with the same basic ISO structure, and I am not sure if other distros than those mentioned in the link will work with this.

I've attached a copy of my grub.cfg file from the grub folder of the USB so you can see what is needed.  Make sure you don't forget the final } of each distro's entry on a separate line, and note the final line of Bodhi 2.0 is ```
initrd (loop)/casper/initrd.gz
``` instead of ```
initrd (loop)/casper/initrd.lz
```

---

### Post by RadicaX on 2012-12-21
Thanks a lot. Everyone of you. That opened up the options quite a bit. And I like the idea of having multiple ISO to try out. So thank you. And glad to know it is not going to break it down in a couple times of doing it or something. XD

---

