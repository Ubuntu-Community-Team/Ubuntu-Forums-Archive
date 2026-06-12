---
title: "Ubuntu not installing on desktop pc"
date: 2014-08-27
forum: Installation &amp; Upgrades
---

### Post by bfagan824 on 2014-08-27
Hey guys, I am trying to get back into using Ubuntu like I used to a few years ago. As usual, I ran into a problem, once my liveusb was created, I shutdown my computer, but the computer ran into a kernel panic before I even reached the Ubuntu desktop interface. I searched to fix this problem and tried with a newly downloaded version of the same software but this time, an error occurred saying "[COLOR=#000000](initramfs) unable to find a medium containing a live file system".[/COLOR]After this, I researched the error and tried every solution I found online. I unplugged the HD, set the flash drive to priority, and checked the md5sum. (I have a gigabyte board if that makes a difference) I even partitioned the flash drive into a 4gb segment and do not have it plugged into the USB 3. I removed all USB devices besides the keyboard and still, the error occurred. I tried 3-4 different versions of Ubuntu tracing all the way back to 12.04, but the same error still occurred. Now, the frustrating part; I plugged the flash drive into my laptop with the same live usb install that just failed on my desktop and it worked without a problem. I then decided to install Ubuntu onto an external HD, but now the external HD is not recognized by even my laptop. The partitions I used are(in actual partition order):
"/boot"=500mb
"/"=125000mb
"/home"=120500mb
"swap area"=4000mb    
I sent the bootloader to the drive itself(installation failed) and then to the /boot partition which completed the installation but did not even show a UEFI menu on my laptop(the external hard drive has a capacity of 250.1gb, obviously I left out the small bits of free space automatically left over)
So, as you can probably tell, I am very frustrated with wasting my entire day after school on this issue and so I have come to ask the guys who can tell me that I probably missed one dumb check mark. I ask if you can help me with my desktop pc and Ubuntu problem(it has never made it to the desktop). Also, some help with what I did wrong on my external hard drive installation would be greatly appreciated, so that I can use it as a portable OS for both my laptop and desktop to share files and programs easily. Thanks for any help, you guys(and girls) are awesome!!!
(on a side note, my desktop does not even take me to a screen where i can manually type commands into a terminal; also, I believe that my desktop is currently in AHCI, although I'm not entirely sure because of the mobo's BIOS naming scheme)

---

### Post by rickm1945 on 2014-08-27
I installed Ubuntu 14.04 LTS on my Toshiba 160 GB External drive. It runs flawless on my Asus.  I had to do some changes in UEFI but nothing major. Check out my Post:
[http://ubuntuforums.org/showthread.php?t=2222450](http://ubuntuforums.org/showthread.php?t=2222450)

Hope this helps you.

---

### Post by bfagan824 on 2014-08-27
> **rickm1945 said:**
> I installed Ubuntu 14.04 LTS on my Toshiba 160 GB External drive. It runs flawless on my Asus.  I had to do some changes in UEFI but nothing major. Check out my Post:
[http://ubuntuforums.org/showthread.php?t=2222450](http://ubuntuforums.org/showthread.php?t=2222450)

Hope this helps you.
Hey, thanks for the help, but my situation is slightly different. The liveusb works perfectly fine on my laptop and goes through with the install. However, on my desktop it goes to the error "medium not found" every time I try to use any Ubuntu OS version, even after using the same exact one on my laptop. So far the things I've found online haven't helped at all so I have no idea what is causing it, although the flash drive and iso are ruled out as issues. Besides that, I'm not sure where I went wrong with my installation on the external hard drive because it does not even go to the GRUB menu on my laptop. I suspect I must have assigned the bootloader to the wrong area but I'm still not sure. Thanks for any help you guys, because until these issues are solved my Ubuntu experience will be delayed sadly ;(

---

### Post by mastablasta on 2014-08-28
Desktop:
what OS does desktop currently have? how is the BIOS configured. or is it UEFI maybe? if UEFI Secureboot on or off?

Laptop: leave the external HDD inside, boot form live USB and use boto repair tool to generate boot info and post the link to that here. it's the only way we can see what you did and how you set it up.

also read this: [http://ubuntuforums.org/showthread.php?t=1422475](http://ubuntuforums.org/showthread.php?t=1422475)

because basically from all your writing all I got was desktop is not booting and laptop is not booting from install to external disk. the info you provided just isn't enough. ok you did provide the error you get but nothing about the "environment" in which the error was created..

---

### Post by bfagan824 on 2014-08-29
> **mastablasta said:**
> Desktop:
what OS does desktop currently have? how is the BIOS configured. or is it UEFI maybe? if UEFI Secureboot on or off?

Laptop: leave the external HDD inside, boot form live USB and use boto repair tool to generate boot info and post the link to that here. it's the only way we can see what you did and how you set it up.

also read this: [http://ubuntuforums.org/showthread.php?t=1422475](http://ubuntuforums.org/showthread.php?t=1422475)

because basically from all your writing all I got was desktop is not booting and laptop is not booting from install to external disk. the info you provided just isn't enough. ok you did provide the error you get but nothing about the "environment" in which the error was created..
Hi mastablasta, thanks for your suggestions. I figured out the laptop and external hard drive problem with a little bit of tweaking, so that case is solved; Ubuntu runs flawlessly on my laptop now. My desktop now recognizes the external hard drive as a booting device and show the GRUB menu. This gives me the option to boot to Ubuntu or to boot to Ubuntu with advanced options(just older versions and safe modes). However, none of these work. The computer either loads until it hits a purple screen with nothing on it, just a blank purple screen, or it goes through a coding process which results in a new error. It says that it: gave up waiting for a root device and that "dev/disk/by-uuid/...random characters... does not exist. Dropping to a shell. It finally finishes with {initramfs}
I'm not sure what could be causing it at this point, but, as far as I know, I do not have UEFI Secureboot turned on as I made this computer at home.

---

### Post by bfagan824 on 2014-08-29
Here's a picture of the BIOS settings[ATTACH=CONFIG]255926[/ATTACH]

---

### Post by mastablasta on 2014-08-29
assuming all is assembled correctly on desktop... :P

does notebook have BIOS and the desktop UEFI? if so then: [https://help.ubuntu.com/community/Installation/UEFI-and-BIOS](https://help.ubuntu.com/community/Installation/UEFI-and-BIOS)

---

### Post by bfagan824 on 2014-08-29
> **mastablasta said:**
> assuming all is assembled correctly on desktop... :P

does notebook have BIOS and the desktop UEFI? if so then: [https://help.ubuntu.com/community/Installation/UEFI-and-BIOS](https://help.ubuntu.com/community/Installation/UEFI-and-BIOS)

Yes, that describes my situation. My laptop has a very basic BIOS and the desktop has a complex UEFI. From the instructions though, I'm not sure where my starting point should be. Am I supposed to do all of the steps on my laptop with BIOS or my desktop with UEFI. If I have to use the desktop, then it will not work as the desktop doesn't even make it to the Gnome environment or password stage. If I am meant to use my laptop, could you please elaborate on the instructions down for me. I'm not exactly sure what they mean by "Boot into UEFI mode from the install drive", and going down the list, I don't fully understand some of the terminology/references. How would I boot into UEFI mode on the laptop is my biggest question at this point :) By the way, thanks for all of your help thus far!

---

### Post by bfagan824 on 2014-08-29
Scratch that, I just read through it again and caught its meaning. The part that I get lost at and do not understand clearly is from letter J onward. Step J and each following step has me at a loss, so some explanation of those would be very helpful

---

### Post by bfagan824 on 2014-08-29
Ok well never mind to that too, I understand it now :). At step M and all of the following steps, however, I am truly stumped. Is the author implying that the drive should boot into a grub menu, have you select "Ubuntu", and then open up a terminal and type the command, or should the computer boot directly into a terminal. What does he/she mean by the drive booting into UEFI mode? Also, I assume that this step would still be done on the laptop, correct? Could you tell me at which step I need to transfer over to my desktop, I don't want to mess up my laptop's settings when I should be messing up my desktop's settings :)

---

### Post by mastablasta on 2014-08-29
no it should boot ok else you need to repeat steps K,L,M

yeah you chose one of the most complicated way to use this OS... I am not sure it is worth the hassle. at least I wouldn't do it. what is the rationale behind this kind of setup? to move external disk from one to the other?!? what not just keep it attached to let's say desktop and access the disk over net? I mean you might take a few steps back and think about it form a different perspective. perhaps there is an easier way that will fit your needs.

---

### Post by bfagan824 on 2014-09-04
> **mastablasta said:**
> no it should boot ok else you need to repeat steps K,L,M

yeah you chose one of the most complicated way to use this OS... I am not sure it is worth the hassle. at least I wouldn't do it. what is the rationale behind this kind of setup? to move external disk from one to the other?!? what not just keep it attached to let's say desktop and access the disk over net? I mean you might take a few steps back and think about it form a different perspective. perhaps there is an easier way that will fit your needs.
Sorry, I didn't notice the "2" at the bottom for the second page of comments so I didn't see your response until now. Anyways, I wanted this setup so that I could use it at home on the desktop, and then when I'm on vacation or out of town, still access the same exact files and ecosystem as I have at home. Even if I were to only install it on the desktop, the desktop does not respond to Flash drives. It always show the "missing medium..." error. With the external hard drive it at least gets to a purple screen, but then sticks there. I would ultimately prefer to install this way for a mobile OS, but if there is a way to install just on my desktop, I could settle. However, the desktop doesn't recognize the live os on the flash drive so I'm not sure how I would get this done.

---

### Post by mastablasta on 2014-09-05
so you want a portable so to carry around on flash disk...but at the same time If I understand correctly this os is not actually installed on any computer?!

otherwise you could install on desktop then use syncing to sync the files to another device before leaving the home.

---

### Post by bfagan824 on 2014-09-05
> **mastablasta said:**
> so you want a portable so to carry around on flash disk...but at the same time If I understand correctly this os is not actually installed on any computer?!

otherwise you could install on desktop then use syncing to sync the files to another device before leaving the home.
Yes, I would prefer a portable os on my external hard drive that I could use for my laptop on the go, hook up to my desktop at home, and hook up to a friend or someone else's computer when necessary. At this point, I have installed Ubuntu onto the external hard drive and it works fine on my laptop. However, plugging the external hd into my desktop freezes it on a purple screen(or sends it to the missing medium error, or the one described before). The desktop always says the error "missing medium" for the os with a liveusb so I wouldn't even be able to install Ubuntu on my desktop directly. Therefore, your linked instructions seem like they would be the only way to get things to work, I just don't completely understand them.

---

