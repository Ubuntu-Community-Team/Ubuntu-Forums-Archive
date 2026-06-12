---
title: "install to 12.04 no graphics"
date: 2012-05-20
forum: Installation &amp; Upgrades
---

### Post by oxman on 2012-05-20
I just did a clean install from 10.04 to 12.04. No matter what method I use to boot up I am pushed to a tty1 prompt. When booting up I get a purple screen then a bump to tty1. I suspect it has something to do with nvidia drivers (it's an 64 bit presario) Please give me instructions on how to get and install drivers that will get me to the desktop.

When I do ls -al from cli it appears the installation went well apart from the graphics issue. 

Any help is appreciated.

---

### Post by oldfred on 2012-05-20
Usually nomodeset on the grub line.

How to set NOMODESET and other kernel boot options in grub2 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

I had to do this with my Nvidia 9600GT:
To install Ubuntu, boot from the cd press any key at accessibility circle and keyboard, press F6 and then select the nomodeset option.
USB boot - At the menu press tab on the first option to edit the boot options and replaced the 'splash' option with 'nomodeset'. 
then
[COLOR=DarkRed]On first boot after install, press e on getting the GRUB bootloader. 
Hold shift from BIOS boot to get menu if only one system installed.
Using arrow keys navigate to and delete quiet and splash and type the word nomodeset in their place[/COLOR]
Press Ctrl and X to boot (low graphics mode), install nVidia driver suggested my Ubuntu

---

### Post by darkod on 2012-05-20
I think unless the video card is really old, you need to install nvidia-current.

You can try it from the command line if it loads fine, or as oldfred suggested boot into the GUI once with nomodeset and install it in terminal there:
sudo apt-get install nvidia-current

---

### Post by oxman on 2012-05-21
So... I did apt-get install nvidia-current

Installed

reboot

grrrr wirrrrrr  

login screen and then no desktop

no joy

tried boot from alt cd with nomodeset

no joy

Progress  though. I have a graphical login then a consistent dark screen with a  mouse cursor that works. Occasionally I will pass the cursor over the  screen and it changes as though it is passing over a dialog box of some  kind.  Crazy stuff.

I may have missed some of the nuances of your instructions. Not sure.

---

### Post by darkod on 2012-05-21
Since you already have it installed, you will need to try the nomodeset on the hdd installation, not the live/alternate cd.

If you have only ubuntu and it doesn't show the grub2 boot menu, hold Shift to show it.

In the boot menu highlight the ubuntu entry, hit 'e' for edit. That will display the boot lines.
With the arrows move the cursor towards the end of the line starting with linux, and after the 'quiet splash' add nomodeset.
Press Ctrl + X to boot.

See if that helps it boot the desktop all the way. If it does, look in Hardware for drivers the system suggests to install/activate.

---

### Post by oxman on 2012-05-21
> **darkod said:**
> Since you already have it installed, you will need to try the nomodeset on the hdd installation, not the live/alternate cd.

If you have only ubuntu and it doesn't show the grub2 boot menu, hold Shift to show it.

In the boot menu highlight the ubuntu entry, hit 'e' for edit. That will display the boot lines.
With the arrows move the cursor towards the end of the line starting with linux, and after the 'quiet splash' add nomodeset.
Press Ctrl + X to boot.

See if that helps it boot the desktop all the way. If it does, look in Hardware for drivers the system suggests to install/activate.

Yes, added nomodeset and still no desktop. I have copied the proprietary nvidia drivers for this system to /media but it keeps screaming about linux headers. Is there a good tutorial for installing them on 12.04? Thanks for the help BTW. It is appreciated.

Edit: After waiting for 15 minutes I now have a cursor and colorful splash screen. No unity desktop or icons available. Haven't found explicit 12.04 instructions on the driver install as of yet

---

### Post by oldfred on 2012-05-21
nVidia needs the headers as it is recompiled/integrated into the kernel. I have always had good luck booting with nomodeset and then installing the recommended  nVidia from the pop-up.

Since it was an upgrade, did you have an old nVidia already installed and kernel versions/nVidia got out of sync?

I have seen this posted, if you can get to command line or chroot into your install:

```
sudo apt-get update
sudo apt-get remove --purge nvidia-*
sudo apt-get install nvidia-current
sudo apt-get upgrade
sudo reboot

```

---

### Post by oxman on 2012-05-21
oldfred, no joy after your procedure. After the login dialog I get a user unlock dialog and a pretty splash screen-no desktop or icons of any kind.

> **oldfred said:**
> nVidia needs the headers as it is recompiled/integrated into the kernel. I have always had good luck booting with nomodeset and then installing the recommended  nVidia from the pop-up.

Since it was an upgrade, did you have an old nVidia already installed and kernel versions/nVidia got out of sync?

I have seen this posted, if you can get to command line or chroot into your install:

```
sudo apt-get update
sudo apt-get remove --purge nvidia-*
sudo apt-get install nvidia-current
sudo apt-get upgrade
sudo reboot

```

---

### Post by oldfred on 2012-05-21
Are you getting the graphical login or a command line login & password. The little icon (gear/star/) in upper right has a couple of options and you may need 2d or just limited version. I have installed gnome-panel, so I am not running Unity and have to use the more limited version to get it to work well.

---

### Post by oxman on 2012-05-21
I login with the graphical login. It looks great. The resolution is perfect. When it goes to load my user desktop it requires some time to load. The background image appears and then it goes black with a usable mouse cursor. Nothing else. After some time I spacebar and a the background image and an unlock dialog appears. Login and there I sit with the background image and no desktop icons. Weird. Never come across that before. Before the clean install 10.04 was working great.

---

### Post by oldfred on 2012-05-21
Near the bottom of this, shows the login screen and if you click on the icon do you get the choice of Ubuntu & Ubuntu 2d?

[http://www.howtoforge.com/the-perfect-desktop-ubuntu-12.04-lts-precise-pangolin](http://www.howtoforge.com/the-perfect-desktop-ubuntu-12.04-lts-precise-pangolin)

---

### Post by oxman on 2012-05-21
oldfred!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!

YOU DAH MAN!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!

Ubuntu Joy flowing like a river at Singing Falls. May you receive many days in like return!

That was it - 2D

Geez. And for what she needs that's just fine.  Just WOW.

My heart felt gratitude to you and all who took interest

---

### Post by oldfred on 2012-05-21
Glad it worked. :)

---

