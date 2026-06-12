---
title: "Can't install Version 7.10"
date: 2008-02-16
forum: Installation &amp; Upgrades
---

### Post by Quattro_Driver on 2008-02-16
Never used a Linux OS; read the posts; still stumped.

I have been trying to install 7.10 and get a welcome-type screen prompting for options: Install or execute; run in safe video mode; check memory; etc.  (Text not exact, but you will recognise the screen I am describing).

Taking any option from this menu causes the same result: CD activity for a minute or so, followed by a black screen and no activity.  (I just tried another distro, PcLinuxOs, with similar results).

I have an Nvidia 8600 GTS graphics card (though my Vista OS always reports it as an 8800 GTS) and I suspect that my problems are directly related to this hardware, although I also have a 1TB SATA HDD running in AHCI mode, which I wouldn't mind betting could compound my problems.

This is what I don't understand - the posts that I have seen seem to suggest that I need to install a suitable Linux driver for the Nvidia card, but as I understand it graphics drivers are loaded by the OS at start up.  I can't start the OS, so how do I get a driver loaded?  Other posts suggest the use of a product called Envy.  I looked on the Envy web site, but failed to see how this could help, as it seems to have instructions for use once Ubuntu is running.

As you will have noticed I have Vista as my current OS and wish to keep this.  My initial intention is to try Ubuntu from the boot CD, until happy, followed by a full install with dual-boot options for Linux and Vista.

The CD executes without issue on my son's PC.

Can anyone help me please?  Go easy though, as terms such as GRUB and GNOME mean little to me as yet.

Thanks in anticipation.

---

### Post by oilchangeguy on 2008-02-16
linux tends not to play well with the latest and greatest hardware. the reason is hardware vendors take their time to make source code available. you can try the alternate cd, and see if that works. if not your computer may have to wait to be a linux computer.

---

### Post by klein de usa on 2008-02-16
hi
i don't think it is the vid card, reboot the cd and at the menu it should give you the option to check the cd for defects. what type and model is the computer you are having trouble with ? i'v had my fair share of problems installing including a bad burned cd from sent to me from ubuntu,

---

### Post by oilchangeguy on 2008-02-16
> **klein de usa said:**
> hi
i don't think it is the vid card, reboot the cd and at the menu it should give you the option to check the cd for defects. what type and model is the computer you are having trouble with ? i'v had my fair share of problems installing including a bad burned cd from sent to me from ubuntu,

you may want to read the users post again. he states the cd runs fine in his son's computer.

---

### Post by klein de usa on 2008-02-16
hi 
i would think they are two diffrent computers, wouldn't you think they would load diffrent things from the cd? i'm not sure but i don't think it changes over to the nv driver till after the ubuntu logo and the orange bar becomes solid,  i'm no expert

---

### Post by M00_cow on 2008-02-17
. nvm

---

### Post by sirgogo on 2008-02-18
bummp?


I just got a 8600 GT from Newegg. I have the same issue and cannot get past the Ubuntu install menu (I'm trying to reinstall Ubuntu). The screen will go blank. Additionally, I've noticed that my onboard graphics card (*listed in signature) is not active while the 8600 card is plugged into the PCI-E slot of my motherboard.

So:
Is there anyway to use the card to install? Because I want it set as default and don't want my onboard graphics even installed (meaning, I don't want to install Ubuntu with onboard graphics, then install the 8600 card).

Thanks!

---

### Post by mwellen76 on 2008-02-21
i'm having the same exact problem except that i have an evga 8800gts...unfortunately i don't have an onboard graphics card so i can't try that...anyone know how to fix this??

---

### Post by Partyboi2 on 2008-02-21
what happened when you tried installing with the [alternate]("http://releases.ubuntu.com/releases/7.10/") cd? Once you have ubuntu installed you will need to install the correct driver from the nvidia website

---

### Post by mwellen76 on 2008-02-21
okay i got it installed...it hangs with a blank screen after it boots...i can get to the command prompt...from there how do i download drivers from nvidia?

---

### Post by Partyboi2 on 2008-02-21
install build-essential
```
sudo apt-get install build-essential 
```then
get the driver from nvidia 
```
wget http://us.download.nvidia.com/XFree86/Linux-x86/169.09/NVIDIA-Linux-x86-169.09-pkg1.run
```then run the installer
```
sh NVIDIA-Linux-x86-169.09-pkg1.run
```then
```
sudo dpkg-reconfigure xserver-xorg
``` choosing nvidia driver
then
```
startx
``` or ```
reboot
```

---

### Post by KuroNeko_13 on 2008-02-21
I have a problem after installing Ubuntu.:( 
When I start it screen goes black and then a message "Computer doesn't support this video mode" appears. I have a feeling it's because there's no video driver.
So how do I install ATI video driver?

---

### Post by Partyboi2 on 2008-02-21
> **KuroNeko_13 said:**
> I have a problem after installing Ubuntu.:( 
When I start it screen goes black and then a message "Computer doesn't support this video mode" appears. I have a feeling it's because there's no video driver.
So how do I install ATI video driver?
try using envy to install the ati driver, if you can boot into recovery mode or get to a working terminal (Ctrl+Alt+F2) 
download envy
```
wget http://albertomilone.com/ubuntu/nvidia/scripts/ubuntu/envy_0.9.10-0ubuntu2_all.deb
```install envy
```
sudo dpkg -i envy_0.9.10-0ubuntu2_all.deb
```then to start envy
  ```
sudo envy -t 
```
then follow the process to install the ati driver.

---

### Post by KuroNeko_13 on 2008-02-21
U R my saviour![http://ubuntuforums.org/images/smilies/guitar.gif](http://ubuntuforums.org/images/smilies/guitar.gif)
:guitar:

---

