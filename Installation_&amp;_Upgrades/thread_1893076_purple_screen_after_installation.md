---
title: "purple screen after installation"
date: 2011-12-09
forum: Installation &amp; Upgrades
---

### Post by geith on 2011-12-09
hello,
i'm completly new to linux, so i tried installing ubuntu 10.04 on my pc (pentium 4 3,0GHz H/T, 2 gb ram, geforce 5200fx, 160gb hdd).everything was fine, but i didnt get internet, becaus of my wlanstick (tp-link tl-wn821n v3). but i heard on 11.10 it will work, so i tried. at the livesession, wlan works perfec. now i installed 11.10. first i checked apci=off because there were a lot of timeouts and s.th. like this. after installing, graka and mainbourd are loading, then i can go to grub-menu: ubuntu with linux 3.0.0-12-generic / with recovery, memorytest etc.
if i choos normal mode, theres just a purple screen, nothing else. if choose recoverymode theres just a black screen, like terminal, just completly black.
i have searched for hours now and i cant fix it. can someone help me?

thanks a lot
g

---

### Post by Rubi1200 on 2011-12-09
Hi and welcome to the forums :)

You can try using nomodeset following the instructions in post # 1 here:
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)

---

### Post by MAFoElffen on 2011-12-09
> **Rubi1200 said:**
> Hi and welcome to the forums :)

You can try using nomodeset following the instructions in post # 1 here:
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
+1 on Rubi1200's sugeggestion, plus an explaination and direction. --> do that to "temporarily" get you into a GUI desktop so that you could get to the Additional Driver to install your video card driver.

The driver for your NVidia Geforce 5200 FX card should be nvidia-173.

---

### Post by geith on 2011-12-13
@Rubi1200 thank you for the link

but still no idea how to get it started.i boot, go into grub menu with kernel, memorytest. then i press >e< to edit the latest kernel. behind "quiet splash" is a "vt.handoff=7", i replaced it with nomodeset and apci=off and nothing happend, just a black screen. and with apci_osi= i get this (image1).

@MAFoElffen thanks, but i'm not that far :)


edit: this is how my default boot-para look like (image2)

edit: should i try a new installation with nomodeset?

---

### Post by mebigfatguy on 2011-12-16
I get the same exact behavior, and i also have a GeForce FX 5200. It only boots in 2.6.8...

one clarification, 

before nomodeset -> pure purple screen no cursor
after nomodeset -> black screen, with cursor

---

### Post by MAFoElffen on 2011-12-16
> **geith said:**
> @Rubi1200 thank you for the link

but still no idea how to get it started.i boot, go into grub menu with kernel, memorytest. then i press >e< to edit the latest kernel. behind "quiet splash" is a "vt.handoff=7", i replaced it with nomodeset and apci=off and nothing happend, just a black screen. and with apci_osi= i get this (image1).

@MAFoElffen thanks, but i'm not that far :)


edit: this is how my default boot-para look like (image2)

edit: should i try a new installation with nomodeset?
Okay... What happens if you select recovery from the Grub Menu? Does it go to the VGA Recovery menu?  If you select the 1st item on that menu, "resume," does it boot the Desktop in Low graphics mode? If so, you could install the driver from the hardware Driver applet.

If not go to the Recovery menu and choose the last option, "root." That will take you to a "root prompt" and install your drivers from the command line:
```
[FONT=monospace][/FONT]
apt-get update
nvidia-installer --uninstall
apt-get remove nvidia-*
apt-get install linux-headers-'uname -r' 
apt-get install nvidia-173
nvidia-xconfig[FONT=monospace]
[/FONT]echo RUN+="/sbin/modprobe nvidia" > /etc/udev/rules.d/90-modprobe.rules
echo options nouveau modeset=0 > /etc/modprobe.d/nouveau-kms.conf[FONT=monospace]
[/FONT]update-initramfs -u
apt-get upgrade

```
Some of those commands in removing old drivers may get a file not found. That's okay. We just want to make sure that old fragments aren't left over.

Tell me how it goes.

---

### Post by MAFoElffen on 2011-12-16
I'm sorry... I just looked at your attached pic.  If that's where it's locked, you have bigger troubles.  (That is not even close to where it init's the graphics.)  Are you sure you even have a bootable kernel?  Because that is where the messages stop / at the kernel init.

Do you have any "previous" kernels that you could try to boot off?

If not, I have further instructions (using a LiveCD.)

---

