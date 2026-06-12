---
title: "X Server problem"
date: 2006-04-17
forum: Installation &amp; Upgrades
---

### Post by matt_21484 on 2006-04-17
Hello everyone, I am new to these forums and to Ubuntu as well.  I finally bought a new hard drive and set up a dual boot but when the install is completed i get this error: Failed to start the X server (your graphical user interface) and then it asks if i want to see the log. if i click yes, this is what i get (attach: x server output).  i click ok and then it comes to this (attach:detailed x server) click ok, and (attch: next error) and then it goes to the command prompt.  

As I said I am very new to ubutu and have very limited use w/ the command prompt but i am computer savy and think i can pick this up.  my computer is home built the specs are: 
Intel Pentium D820 w/ Intel 945 mobo
1GB Ram
Radeon X800GT 
seagate 7200.7 80GB hard drive (linux)
Maxtor 100GB HDD (windows)

I've done some basic searching and have heard of ati causing similar problems.  I hope this can be resolved.  Thanks for your input](*,)

---

### Post by jakez on 2006-04-17
On the attached pictures i cannot read the problem, i.a.w. when you scoll down yo poosible will see what causes the problem; but maybe that will not cease the problem for a new linux user;
But you could try to reconfigure the harware with the following command:
sudo dpkg-reconfigure xserver-xorg

I hope this will be helpfull to you
Greetz

---

### Post by Sutekh on 2006-04-17
Run```
sudo dpkg-reconfigure xserver-xorg
```
You will be asked a long string of questions about your input devices; mouse/keyboard and monitor

If you are unsure what to answer, just use the default/suggested

The important question is what video driver to use for the X Windows Server.  You should choose the **vesa** driver

Once you are finished configuring it, run
```
sudo /etc/init.d/gdm restart
```

If you get into Ubuntu, then you are halfway there.  Those "vesa" drivers are just the quick fix.  You should look into installing the ATI drivers.

You can try either this HOWTO

[Ubuntu Document Storage Facility - Install ATI Driver](http://doc.gwos.org/index.php/Install_ATI_driver)

or look into installing EasyUbuntu (for GUI install of ATI drivers and loads of other stuff)

[Ubuntu Forums - Easy Ubuntu v2.2](http://ubuntuforums.org/showthread.php?t=64629)

---

### Post by hellfried on 2006-04-18
[QUOTE=Sutekh] 

If you get into Ubuntu, then you are halfway there.  Those "vesa" drivers are just the quick fix.  You should look into installing the ATI drivers.
 
 [/QUOTE]

personally this so called 'quick fix' have served me well so far. things actually looks quite ok as far as video quality is concerned. is it neccessary to get this ati driver and what are the problems if i stick to 'vesa'?

---

### Post by Sutekh on 2006-04-18
I don't think you will encounter many problems.  I can't really speak from experience, having used an NVIDIA card, which was pretty well supported from the installation.  I have since upgraded the drivers to those in the Ubuntu repositories.

If I'm not too much mistaken, the vesa driver does not provide 3D acceleration for your graphics card.  Installing the official proprietry ATI drivers (or the fglrx drivers I think) will give you full graphics acceleration.

The vesa drivers are a really easy and usually successful way to solve graphics problems, hence 'quick fix'.  I think that if possible though, you are better off using a driver that matches your card better.  I could be way wrong on this though.

---

### Post by hellfried on 2006-04-18
[QUOTE=Sutekh]I don't think you will encounter many problems.  I can't really speak from experience, having used an NVIDIA card, which was pretty well supported from the installation.  I have since upgraded the drivers to those in the Ubuntu repositories.

If I'm not too much mistaken, the vesa driver does not provide 3D acceleration for your graphics card.  Installing the official proprietry ATI drivers (or the fglrx drivers I think) will give you full graphics acceleration.

The vesa drivers are a really easy and usually successful way to solve graphics problems, hence 'quick fix'.  I think that if possible though, you are better off using a driver that matches your card better.  I could be way wrong on this though.[/QUOTE]

 well i followed the instructions in the other posts on this thread but i still got x server failures. looks like i will be sticking to vesa for a while.
my graphics card is a ati radeon x550.

---

### Post by Sutekh on 2006-04-18
Maybe these links can help.  

[Ubuntu Wiki - Binary Driver HOWTO](https://wiki.ubuntu.com/BinaryDriverHowto)

[Unofficial ATI Linux Driver Wiki](http://wiki.cchtml.com/index.php/Ubuntu_Installation_Guide)

[Ubuntu Forums - ATI Radeon X550](http://ubuntuforums.org/showthread.php?t=99725)

Edit: They seem to be similar to the other I posted, so maybe not.

---

### Post by matt_21484 on 2006-04-18
> **Sutekh]Run```
sudo dpkg-reconfigure xserver-xorg
```
You will be asked a long string of questions about your input devices said:**
> Ubuntu Document Storage Facility - Install ATI Driver[/url]

or look into installing EasyUbuntu (for GUI install of ATI drivers and loads of other stuff)

[Ubuntu Forums - Easy Ubuntu v2.2](http://ubuntuforums.org/showthread.php?t=64629)

I tried to run through the x server setup and I am not sure where to select the vesa drivers, or if i am getting that far in the process.  I get to the 24-bit color selection in the setup and i get a "warning" down at the bottom of my screen.

"xserver-xorg postinst warning: overwriting possibly-customised configuration file; backup in /etc/x11/xorg.conf.200604181003"  then it leaves me at the command prompt.  I typed in yes and i got nothing but a long string of "y" that never neded so i had to reboot.  I went through the process again, and same result.

---

### Post by ofer_w on 2006-04-18
I have the same problem - the xserver is not working

I wrote in the command line
$sudo dpkg-reconfigure xserver-xorg 

and this is what I recive

sudo: unable to lookup mysystem via gethostbyname()
postdrop: warning: unable to look up public/pickup : No such file or directory
Package 'xserver-xorg' is not installed and no info is available.
Use dpgk (...)
and dpkg ....
/user/sbin/dpkg-reconfigure: xserver-xorg is not installed

---
what should I do?

thanks

---

### Post by hellfried on 2006-04-18
[QUOTE=Sutekh]Maybe these links can help.  

[Ubuntu Wiki - Binary Driver HOWTO](https://wiki.ubuntu.com/BinaryDriverHowto)

[Unofficial ATI Linux Driver Wiki](http://wiki.cchtml.com/index.php/Ubuntu_Installation_Guide)

[Ubuntu Forums - ATI Radeon X550](http://ubuntuforums.org/showthread.php?t=99725)

Edit: They seem to be similar to the other I posted, so maybe not.[/QUOTE]

ok right off the bat i have a question: following the first link, i am now looking at the 'binarydriverhowto/ati'. it says that i should install the kernel drivers. i am running on this new fancy dual core pentium chip. so what should i put as my cpu architecture #?

---

### Post by Sutekh on 2006-04-18
> **matt_21484]I tried to run through the x server setup and I am not sure where to select the vesa drivers, or if i am getting that far in the process.  I get to the 24-bit color selection in the setup and i get a "warning" down at the bottom of my screen.

"xserver-xorg postinst warning: overwriting possibly-customised configuration file said:**
> 
I think the step you need is before the colour setup.  It should ask you a question like>  For the X Window System graphical user interface to operate correctly, it is necessary to select a video card driver for the X server.
Drivers are typically named for the video card or chipset manufacturer, or for a specific model or family of chipsets.Then there should be a list of names, which are the drivers you can use[quote]
Select the desired x server driver:
apm, ark, ati, chips, cirrus, cirrus_alpine, cirrus_laguna, cryix, fbdev, glide, glint, i128, i740, imstt, mga, neomagic, newport, nsc, nv, rendition, riva128, s3, s3virage, savage, siliconmotion, sis, tdfx, tga, trident, tseng, vesa, vga, via, vmware.
It may be on **ati**, or something else, you need to scroll down and choose **vesa**.  

You can manually edit the xorg.conf, but I'd suggest this way first.



[QUOTE=ofer_w]I have the same problem - the xserver is not working

I wrote in the command line
$sudo dpkg-reconfigure xserver-xorg 

and this is what I recive

sudo: unable to lookup mysystem via gethostbyname()
postdrop: warning: unable to look up public/pickup : No such file or directory
Package 'xserver-xorg' is not installed and no info is available.
Use dpgk (...)
and dpkg ....
/user/sbin/dpkg-reconfigure: xserver-xorg is not installed

---
what should I do?

thanks[/QUOTE]
Hmm, have you only just installed Ubuntu?  Can you tell us the things that have happened up until the failure of the X server?

What method did you choose to install?  A normal installation or an expert installation?  

Did the installation complete succesfully?  After it installed GRUB, you should have done a reboot so that the installation could finish.  Were there any apparent errors? 

After the installation, where you booted straight to a command line login?  Or did you encounter the sort of error screen the original poster had?


[QUOTE=hellfried]ok right off the bat i have a question: following the first link, i am now looking at the 'binarydriverhowto/ati'. it says that i should install the kernel drivers. i am running on this new fancy dual core pentium chip. so what should i put as my cpu architecture #?[/QUOTE]
If you have an Intel Dual Core, then you should be using the linux-686-smp kernel over the default 386 kernel.  The SMP kernel allows you to utilise both cores of your CPU.

You may not already have that installed and you can check with```
uname -r
```This will tell you the kernel version and architecture.

To get the complete 686-SMP kernel, use
```
sudo apt-get install linux-686-smp
```

---

### Post by hellfried on 2006-04-19
well when i did 'uname -r' this is what i get. do i have to first uninstall this first and then only install the kernel that you have mentioned?

---

