---
title: "Dual-boot on 2 HDD. Ubuntu 12.04.3 wont boot at all"
date: 2013-09-26
forum: Installation &amp; Upgrades
---

### Post by Nicolas_Rousseau on 2013-09-26
Hi,

I am new to Ubuntu and unfortunably I am unable to install it... I done everything said on the Ubuntu Install section, using a flash drive and a DVD, nothing worked. I always get stock at the same point: Ubuntu purple page with the orange dots flashing then the maze (see attachment)

I am running on an Asus motherboard and Nvedia gt240 graphic card, drivers are fine. 

I am trying to install Ubuntu on my second Harddrive so i will be set up that way:

500gig complete HDD for windows 7 home premium 64bit
500gig complete HDD for Ubuntu 12.04.3 64bit

I also tryed to disconect my windows HDD before trying to boot Ubuntu: same issue.

Can someone please help me?

PS: keep in mind that i am new to Ubuntu and I am not a native English speaker so please give all the details you can.

Thanks a lot,

Link i used to try installing:

Download Ubuntu:
[http://www.ubuntu.com/download/desktop](http://www.ubuntu.com/download/desktop)

Create a Bootable USB drive:
[http://www.ubuntu.com/download/desktop/create-a-usb-stick-on-windows](http://www.ubuntu.com/download/desktop/create-a-usb-stick-on-windows)

Install Ubuntu:
[http://www.ubuntu.com/download/desktop/install-desktop-long-term-support](http://www.ubuntu.com/download/desktop/install-desktop-long-term-support)

I used InfraRecorder to burn my DVD.

---

### Post by carl4926 on 2013-09-26
So Ubuntu is installed
It just isn't booting to the desktop?
Or is it not installed and you can't even get to the installer or live desktop?

Have you tried booting with nomodest?

---

### Post by Bucky Ball on 2013-09-26
Try this: 

When you get to the purple page hit F6. Do you get some options? If so, choose 'nomodset' and continue.

If you can get to the page that give you the option to 'Try Ubuntu' 'Install Ubuntu' etc., then hit F6, choose 'nomodset', continue. Did that work? Your problem, I'm assuming from what you've given above, it related to graphics card/drivers.

If you have Ubuntu installed but are booting to this, let us know. 

(This supports what carl4926 mentions re 'nomodset' above but doesn't explain how to do. ;))

---

### Post by Nicolas_Rousseau on 2013-09-26
Ubuntu doesnt give me any option at all. If I boot from the USB i get some options but still in my BIOS setting not in Ubuntu. I have no idea what is nomodset. I will check it. I just reformat my PC every drivers are the latest. According to Nvedia web page my graphic card is up to date.

---

### Post by Nicolas_Rousseau on 2013-09-26
Find the nomodeset thing: same issue but this time with more green in the maze :P

---

### Post by ubfan1 on 2013-09-26
Here some more options to try, some might have to be typed in if they are not on the F6 list:
nomodeset
acpi=0
acpi_osi=linux
acpi_backlight=vendor
video=1280x1024-24@60

---

### Post by Nicolas_Rousseau on 2013-09-26
@[**[COLOR=#DD4814][B]carl4926**[/COLOR][/B]]("http://ubuntuforums.org/member.php?u=809261")
Ubuntu is not install. I try to do it. I am only seeing the page where you can choose to instal or run in usb drive. No installation launcher or anything like that.

@[**[COLOR=#000000]ubfan1[/COLOR]**]("http://ubuntuforums.org/member.php?u=1256996")
I'm going to test it. I will come back for the result.

@ ALL 
Thanks for your help, still some work to do but its the beginning of something.

---

### Post by Nicolas_Rousseau on 2013-09-27
We have something! I have been able to launch Unbuntu from my usb drive! I cant figure out where I put the command ubfan1 gave me. I cant launch the installation because after i clic on the icon, the window that open doesnt let me clic or enter anything. Any idea?

---

### Post by Nicolas_Rousseau on 2013-11-05
I manage to install it right! Nomodeset was the answer. I switch my boot order to use gnome as a "boot manager". I folllow direction to instal ubuntu on my SDb. Now running faster and better then windows ;) 

Thanks for your help.

---

