---
title: "[SOLVED] How to install radeonhd driver"
date: 2008-10-31
forum: Installation &amp; Upgrades
---

### Post by luziva on 2008-10-31
I am not able to install Kubuntu 8.10. See [here]("http://ubuntuforums.org/showthread.php?t=964076") or [here]("https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-ati/+bug/274234")

The radeonhd driver seems not to be on the install CD, but it is in the [repositoy]("http://packages.ubuntu.com/intrepid/xserver-xorg-video-radeonhd") for Intrepid.

How do I get the driver installed. I'm not able to download it directly to my laptop. For a Internet Connection I need to set up my wlan and the login over a web page.

Is there some way to put the driver on a pen-drive and install it from there?

---

### Post by Peter09 on 2008-10-31
On the page you have given there is a link to the .deb package. If you download this you can install it (just click on it and the dialogue should come up). You may find that you need other packages as dependencies as well.

---

### Post by luziva on 2008-10-31
Thanks....but

_IF_ i had a working driver I would be able to get to a desktop. 

But as described in the posts the xserver does not start, due to not available or not working drivers!

---

### Post by Peter09 on 2008-10-31
Can you download the driver to another machine and transfer it? Then you can use dpkg to install it.


Also will your graphics card work with the default (2d) driver such as MESA?

---

### Post by Peter09 on 2008-10-31
Just realized that you should be able to install using apt-get on the command line as long as you have an internet link.

```
apt-get install radeonhd
```

I am assuming radeonhd is the name of the package that you want.

On first reading your post I assumed that you did not have an internet connection, if you can get a wired connection you can do this.

---

### Post by luziva on 2008-10-31
> **Peter09 said:**
> Can you download the driver to another machine and transfer it? Then you can use dpkg to install it.

How do i do this? And am i not messing with my system by not using apt-get?

> **Peter09 said:**
> Also will your graphics card work with the default (2d) driver such as MESA?
I think you mean vesa, but no, the card does not work in veasa or safe-graphics mode.

---

### Post by Peter09 on 2008-10-31
Yep - should have been vesa. apt-get is the command line front end to synaptic. If you cannot get a GUI then its the best way to install stuff. You are not messing with your system in doing this.

If you look through the forums you will see that apt-get is normally used as it is easier to describe that going through the GUI in synaptic.

If you have an internet connection use the apt-get method.

---

### Post by luziva on 2008-10-31
I think you do not get my point. I have
[LIST]
[*]no internet connection
[*]no desktop
[/LIST]
and I want to install a single .deb from a e.g. pen-drive.

Is this possible and how?

---

### Post by Peter09 on 2008-10-31
I would also do at the command line

```
sudo apt-get update
sudo apt-get upgrade
```
this will ensure that all necessary packages are updated and downloaded. Do this before you download the driver if possible.

---

### Post by luziva on 2008-10-31
????:???:
Please read my previous post again

---

### Post by Partyboi2 on 2008-10-31
Are you able to get to a terminal (ctrl+Alt+F2) If you can then change directory to where your pen-drive is.
```
cd /media/disk
``` then use the list command to check the contents
```
ls
```then if you are in the correct directory and can see the download deb file install it by typing
```
sudo dpkg -i packagename
``` change packagename to the whole file name of the deb package.

---

### Post by luziva on 2008-10-31
Ok, thnks to partyboi2 I got my system running. The complete setup:
[LIST=1]
[*]download the .deb and put it to pen-drive
[*]find out the dev name by using dmseg
[*]create a directory fo the pen drive e.g. mkdir /media/disk
[*]mount the pen-drive with mount -f vfat /dev/sdb1 /media/disk
[*]install the package with sudo dpkg -i /media/disk/"packgename"
[/LIST]

---

### Post by s1moe2 on 2008-11-03
hi all

i'm having the same problem and I couldn't fix it for now.
My laptop is a toshiba a200-1c3 which has an ATI Mobility Radeon HD2400.. When installing Intrepid the prompt "ubuntu@ubuntu$:" appears and no desktop in sight. I tried to install the deb file from pen drive but it didnt work :S

in this case I do have an internet connection but I tried apt-get install radeonhd and it didnt work out either.. please help =)

tks a lot

---

### Post by Peter09 on 2008-11-03
s1moe - you should really start a new thread as this one is marked solved.

What Ubuntu are you installing - have you installed the Desktop or the Server version?

---

### Post by blackSP on 2008-11-04
This is a major problem, basically a big f-up!
I had to rebuild x-server after which the whole system died on me. Reinstalling from the freshly downloaded 8.10 iso didn't resolve it. I thought it was a corrupt disk/device problem so I installed Vista after which I tried 8.10 again. I then found out that my Radeon HD2400 drivers were missing in the iso so I'm now installing 8.04 and will then do another upgrade to 8.10. As for some reason I could not access my hard drive I lost all docs and pics and stuff since my last backup (-1month). Damn, I'm angry!

edit: I don't think this is solved, not until Radeon cards are recognized during a fresh install.

---

