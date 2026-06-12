---
title: "cannot boot from either a dowloaded iso or a usb boot image"
date: 2012-12-05
forum: Installation &amp; Upgrades
---

### Post by rickdaly on 2012-12-05
Hi all
I am a newbie to ubuntu linux and basically downloaded an iso to usb (ubuntu-12.10-desktop-i386.iso) and to CD, neither of which worked. I changed the boot sequence in bios as instructed but it didnt boot on startup?? It just waited a few seconds and then went to hard drive and booted up normal Vista. Having looked closer at the usb drive and the folders I found a VM Box which I opened and it gave a message "this kernel requires the following fearures not available on this CPU : pae
Unable to boot - please use a kernel appropriate for your cpu"
Can someone tell me whats missing? Or how I can find a linux version which is appropriate. My CPU is an Intel Core DUO E6750 @ 2.66 GHz
Appreciate any help. And please remember I am a newbie so would appreicate simple instructions ;)

---

### Post by darkod on 2012-12-05
You need to burn the cd from image file, not simply burn the .iso to a cd. If you open the cd and see the .iso file in there, it's wrong.

For usb it's the same. You can't simply copy the iso in there. You need to create the usb so that it's bootable.

Burning the cd from the iso would be easier, but if you want to try creating the bootable usb from the iso you will have to use something like Unetbootin or Universal USB Installer. That will make the stick bootable and at the same time extract the iso onto it.

---

### Post by rickdaly on 2012-12-05
Thanks darko, appreciate your help :)
but am not that much of a newbie ;) I created the bootable usb using Universal USB Installer - it now has renamed the usb so I guess that proof? And u are right, the CD just has the .iso image on it. But I followed the instructions on how to do it. So what is supposed to be on CD? Do u know a site which is "idiot-proof"? I just want to have a bootable medium (CD/USB) from which I can run Ubuntu Linux for my Vista PC?

---

### Post by darkod on 2012-12-05
In windows you can download and install the free Imgburn. When you open it select the Write Image file to disc option, select the iso and that's it.

The usb should work if it was created correctly and if your computer supports booting from usb. If you want to try again booting from it, go into BIOS and take a look at the boot devices. Sometimes to boot usb sticks you need to select the option USB-HDD. The device needs to be before the HDD otherwise it will try booting from the hdd.

---

### Post by verzx on 2012-12-05
USB is probably the fastest way to do it and it's good to test if you like it before installation using the Live option you have. This program is really straight forward all you need to do is follow the steps and then start it. It also gives you the option to download the correct distribution if you do not have the ISO file.

Try using this:

[http://www.linuxliveusb.com/](http://www.linuxliveusb.com/)

Here is a picture of the interface:

[http://www.linuxliveusb.com/images/stories/screenshots/2.jpg](http://www.linuxliveusb.com/images/stories/screenshots/2.jpg)

---

### Post by rickdaly on 2012-12-05
Thanks guys! 
I did what darkod said about new iso burn and used a DVD instead of a CD (although they said it was ok to) It worked fine now...except its changed mz kezboard from German to english ;) Anyway am writing this from my first ever usage of Linux...
I will try the USB option again later, will get mzself used to this first. 
And as gurus of Linux, what wold u suggest to a Newbie to read to become Linux savvy_ Is there a bible which has a link_
Once again, thank u both for your speed help :)

---

### Post by oldfred on 2012-12-05
You can pick and choose what you might want to know more about:

       A master thread on learning/books/terminal/bash/Linux etc
Linux Command Line Learning Resources
[https://help.ubuntu.com/community/CommandLineResources](https://help.ubuntu.com/community/CommandLineResources)
[http://ubuntuforums.org/showthread.php?t=1909108](http://ubuntuforums.org/showthread.php?t=1909108)

   Thread on books:
[http://ubuntuforums.org/showthread.php?t=1874294](http://ubuntuforums.org/showthread.php?t=1874294)

   Ubuntu Documentation:
Official Ubuntu Documentation
[https://help.ubuntu.com/](https://help.ubuntu.com/)
[https://help.ubuntu.com/community](https://help.ubuntu.com/community)
[http://ubuntu-manual.org/](http://ubuntu-manual.org/)
[http://www.ubuntupocketguide.com/index_main.html](http://www.ubuntupocketguide.com/index_main.html)

---

