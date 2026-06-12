---
title: "Installing Ubuntu 7.10 stuck Running Local boot scripts"
date: 2008-02-06
forum: Installation &amp; Upgrades
---

### Post by Gimpojones on 2008-02-06
All, I've been browsing the forums the last few days and I havent been able to find the answer to my problem  The closest I've come is some steps on how to bypass this problem using a mac. (not sure if this will help)

Anyway, I have an asus Fv3 series laptop, it can be booted to vista (QQ)  But when i'm going through the install for ubuntu it gets stuck and Running Local boot scripts.

Everything I'm reading talks about after the user has installed the app, everyonce and a while there will be a blurb about seeing this during the install with no follow ups.

Just to give a bit more information:

1. When I boot from the 64bit version, I see the ubuntu splash it allows me to select the install.
2. Then during the process the video warning 'use low graphics' pops up.
3. I then tried to configure, accept low settings, and simply clicking next to no avail.
4. After I progress forward the system stops on the boot scripts.
5. I can't get past this point, nor do i have any type of teriminal access. When I press keys I get strange text that appears [[C for example.
6. When i press the power button on the lap top the system then comes up with some text then exits.


Anyone know if the mac fix I've read will work?

---

### Post by Partyboi2 on 2008-02-07
when you say you don't have terminal access, does that mean you have tried pressing Ctrl+Alt+F2?
You could  try the [alternate]("http://releases.ubuntu.com/releases/7.10/") cd Its a text base installer if you can't get to a working terminal.

---

### Post by Gimpojones on 2008-02-08
I'm able to alt-F2...etc...  Sorry i'm a noob I didn't figure that out until yesterday.  I tried the alternate CD but when the system boot it just showed me a corrupted picture of ubuntu logo.

I have a 8600gts in my laptop, does ubuntu have hardware compatability issues?

---

### Post by Partyboi2 on 2008-02-08
You can try installing the drivers for the graphics card.
boot into the recovery kernel (should be 2nd choose at the grub screen)
Once at a terminal install build-essential package
```
apt-get install  build-essential
```then get the driver
```
wget http://us.download.nvidia.com/XFree86/Linux-x86/169.09/NVIDIA-Linux-x86-169.09-pkg1.run
```Then start the installer
```
sh NVIDIA-Linux-x86-169.09-pkg1.run
```then when that has finished installing type
```
dpkg-reconfigure xserver-xorg
```answer all the questions and if you are unsure choose the default ones which are the ones displayed highlighted on screen.
After that type
```
startx
```
or type
```
reboot
``` to reboot into normal mode

---

### Post by Gimpojones on 2008-02-09
This almost worked.....


Well, it seems that my laptop will not connect to the internet I guess i need to install the ethernet driver.  I'm surprised it wasn't installed during the alternate cdrom install.

Any tips on how to install?  Should i use the alternate cd and do something similar to the essential build?

Thanks for your help.


Attansic L1 Gigabit Ethernet

---

### Post by JimD2008 on 2008-03-16
This post is a wee bit dated, but I had the same exact problem.

I also tried the suggested fix and encountered the scenario where I wasn't able to download the driver.

Just on a whim I tried the "safe graphics mode" from the live disk options and the GUI had no problem loading.  From there install was as intended.  I suggest giving this a go.

GL

---

