---
title: "Ubuntu 10.10 and Sony Vaio VPCZ with NVIDIA Geforce GT330M"
date: 2010-11-10
forum: Installation &amp; Upgrades
---

### Post by joeheim on 2010-11-10
[COLOR=black][FONT=Verdana]Hi there,[/FONT][/COLOR]
 
[COLOR=black][FONT=Verdana]I would like to know if there is anyone who successfully installed Ubuntu 10.10 on a [/FONT][/COLOR]
[COLOR=black][FONT=Verdana]Sony Vaio VPCZ1 or similar.[/FONT][/COLOR]
[COLOR=black][FONT=Verdana]It has a NVIDIA GeForce GT 330M GPU with CUDA™ Technology (SPEED MODE) and Intel® HD Graphics (STAMINA MODE) (switchable)[/FONT][/COLOR]
[COLOR=black][FONT=Verdana]The Processor is an Intel Core i7-620M with 2.66 GHz[/FONT][/COLOR]
[COLOR=black][FONT=Verdana]and the Chipset from Intel HM57 Express chipset.[/FONT][/COLOR]
 
[COLOR=black][FONT=Verdana]All I got is a working VESA mode but otherwise I end up with a black screen or a prompt.[/FONT][/COLOR]
 
Thanks

---

### Post by tommcd on 2010-11-11
Which graphics card are you trying to use?
If you are using the nvidia, have you tried installing the nvidia driver from the Ubuntu repos?

---

### Post by joeheim on 2010-11-21
Hi,
 
finally I was successful !
 
I used the following article/websites:
 
[[COLOR=#3d2802]http://www.voip-x.co.uk/files/adam/[/COLOR]]("http://www.voip-x.co.uk/files/adam/") (Look at IMPORTANT_README File !!!!)
 
and the following instructions (forgot which Forum)
 
1) Download Newest Nvidia drivers
2) Open module blacklist as admin gksudo gedit /etc/modprobe.d/blacklist.conf Add these lines and save: blacklist vga16fb blacklist nouveau blacklist rivafb blacklist nvidiafb blacklist rivatv
3) Uninstall any previously installed Nvidia drivers: sudo apt-get --purge remove nvidia* sudo apt-get install binutils gcc
4) Reboot your computer
5) When an error message pops up saying that Ubuntu cannot load Nvidia drivers, choose Exit to terminal (Exit to console)
6) Login and cd to the directory where you saved your file
7)Install drivers sudo sh NVIDIA-Linux-x86_64-195.36.24-pkg2.run
Start GDM sudo service gdm start
 
that's it :P

---

### Post by MuddyAzian on 2010-12-21
Also, take a look at [http://forum.notebookreview.com/sony/473226-insyde-hacking-new-vaio-z-advanced-menu-bios.html](http://forum.notebookreview.com/sony/473226-insyde-hacking-new-vaio-z-advanced-menu-bios.html) which worked well for me (for Fedora 14)

---

### Post by lex0429 on 2010-12-27
Joeheim,

I have the VPCZ125GX and am trying to install 10.10 and after the install, which graphically wasn't great, all i get is a black screen. I cant open the OS at all to do what you suggested. Any ideas?

---

### Post by miser89 on 2010-12-27
I bought a new VPCZ last week and have solved most of the booting issues.  This guide [http://www.adhocism.net/2010/11/installing-ubuntu-10-10-on-sony-vaio-vpc-z13m9eb/](http://www.adhocism.net/2010/11/installing-ubuntu-10-10-on-sony-vaio-vpc-z13m9eb/) to using Adam's files (already been linked to) was very helpful.

It's not running perfectly though - full screen applications do not run when using the Intel graphics, and in Nvidia simply loading video is very buggy (often requiring me to restart X) after loading a game or AVI file.  Booting the laptop up is a bit of a pain - when that guide has been followed you need to select one kernel in GRUB at startup, then your computer will restart after a few seconds, then you select the later kernel, which is a bit of a hassle.

I hope someone out there is actively developing improvements on the solutions currently available; for me it's become an awkward experience using linux on here when I can't reliably watch video.

---

### Post by lenticular on 2010-12-27
Have you tried holding down the shift key when it boots?  This should get you to the grub menu and allow you to chose a kernel.

Good luck.

---

### Post by lenticular on 2010-12-27
I had work buy me a Vaio VPCZ133GX about a month ago as a successor to the Vaio TZ130 that I had used with Ubuntu for three years.  I've spent most of the holiday break trying to configure it to my liking.  Still a long way to go, but it is usable enough for me right now.

I started the OS install using the 10.10 desktop image, but found that this totally does not work with the graphics.  Following the advice from Frederic Questier's page ( [http://questier.com/2010/04/26/ubuntu-10-4-lucid-lynx-on-sony-vaio-vpcz11x9e/](http://questier.com/2010/04/26/ubuntu-10-4-lucid-lynx-on-sony-vaio-vpcz11x9e/) ) I used the 64-bit alternate image.  He seems to have been working with Lucid and not Maverick but there is still much interesting information.

Right now, I boot with the speed switch on, get into grub, and select this kernel ( initrd.img-2.6.28.10-vaioz ) which forces a reboot.  When it comes back up it is aware of the Nvidia graphics, and I then boot another kernel (usually 2.6.37-6-vaioz).  Both custom kernels come from Adams Files ( [http://www.voip-x.co.uk/files/adam/](http://www.voip-x.co.uk/files/adam/) ).  The IMPORTANT_README from that site gives basic directions.  I found the text a bit confusing, and it wasn't until I was several hours into it that I realized that I would have to essentially boot twice each time.  Ah well, at least the Vaio boots quickly. 

I wasn't up to speed on grub-2 and wanted to make it so that I didn't have to hold the space key down each time I rebooted.  good explanation of it here: [https://help.ubuntu.com/community/Grub2#Configuring%20GRUB%202](https://help.ubuntu.com/community/Grub2#Configuring%20GRUB%202).

I decided to use the SSD RAID as it came from Sony.  This seems to be ok with Maverick.  At one point, I tried Lucid, which didn't seem to understand the SSD RAID at all.

Never could get the driver downloaded from NVIDIA to work, but the one from the repos did the trick.

My main use for this PC is from a docking station at work, then taking it home with me in the evening.  Because of this I have not yet expended much effort on making it work in stamina (mode) so far.

Not working for me: suspend, brightness, and no sound.

I'm also having a heck of a time getting VMWare Player to work but that's not a Vaio issue.

Natty is due in April and I'm hoping that it will be an easier fit for the Vaio Z.

---

### Post by lenticular on 2010-12-27
A little progress...

Booting the 2.6.36-0-vaioz kernel I have analog sound.  From Preferences->Sound->Hardware I selected Internal Audio, then in the Output tab selected Internal Audio Analog Stereo and dialed up the output volume. 

Adam notes in the README that 2.6.36-0 incorporates all of his known fixes but warns that it is experimental and  bad things could happen.

Oh, I also booted the 64-bit Desktop alpha of Natty and was pleased to see that it had no problems working with the graphics hardware (although I didn't see if it was talking Nvidia or inttel).  Still, too rocky for me to do much with.

---

### Post by lex0429 on 2010-12-28
This sucks that there is no support for this laptop. While these work arounds might get the job done they are far from perfect and make it too inconvenient for me to use Ubuntu rather than just Windows. This is like going 8 years backward IMO. Anyhow I guess I will wait for the next release in April and hope they work things out.

---

### Post by barisergun on 2011-02-14
Hello Guys;

I have managed to install Ubuntu 10.10 Kernel 2.6.37 rc2 (for 10.10 maverick) both for 32-bit and 64-bit OS systems. Although I am at the stage of using only Intel HD graphics card and Dual switch is disabled. 

I have also used sony-laptop-series n.97 source codes with Adam's patch and by applying that the switch was enabled. Althoug I didint manage to fully configure the Nvidia card.

For being able to use Intel HD Graphics card with full resoluiton support dont use a Xorg.conf file as XServer manual states. That is to say delete Xorg.conf if it exists.

---

### Post by sd@ksu on 2011-04-06
Hi, I am a novice but I have installed and used UBUNTU on my other computer (dual boot with win xp).
Now, on my Sony VAIO VPCCW21FX with **NVIDIA GeForce 310M** , I am having difficulty viewing the display ! I could install Ubuntu if I connect to another display which is a sony SDM-M81 because I can see the display there !!! But not with my laptop display which is NVIDIA ! I read in this forum that people are taking about installing NVIDIA drivers and stuffs like that but there is too many information for a novice like me. Could anyone please answer my question so that I can see Ubuntu on my laptop screen. I have already installed Ubuntu 10.10 (64 bit) parallel with windows 7 64 bit on my machine. Windows 7 is fine. But with Ubuntu, I dont see the display on my laptop screen which is NVIDIA. Only if I connect an external display (SDM-M81 here) , I can see what's going on in ubuntu. Please help. Its really urgent. I have some softwares which run better if used in lunux !

---

### Post by tommcd on 2011-04-06
sd@ksu,
First try booting with the *nomodeset* option. To learn how to do that, see this: [http://www.ubuntugeek.com/how-to-fix-ubuntu-10-04-lts-lucid-blank-screen-at-startup.html](http://www.ubuntugeek.com/how-to-fix-ubuntu-10-04-lts-lucid-blank-screen-at-startup.html)
And welcome to the Ubuntu forums!

---

