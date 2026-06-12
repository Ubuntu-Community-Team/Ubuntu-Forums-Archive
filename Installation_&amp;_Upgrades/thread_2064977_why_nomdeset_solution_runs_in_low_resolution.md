---
title: "why nomdeset solution runs in low resolution"
date: 2012-09-30
forum: Installation &amp; Upgrades
---

### Post by drillerccg on 2012-09-30
Installing 12.04 as dual boot on HP Pavilion dv4 with integrated intel graphic card, ran into the black screen. Tried nomodeset option and was able to bring the screen backup. I am also able to make it permanent by editing the grub.

The only problem is that it appears to be running on 640x480 resolution. I need it to run 1366x768 the windows partition is running.

I've tried everything in both the graphic card threads. I even tried 12.10 nightly release with 3.5 kernel. Nothing is working. Any help is appreciated.

---

### Post by drillerccg on 2012-10-01
Solved it. Done on HP Pavilion dv4 with Integrated Inte; graphic card, black screen  at install, and nomodeset has one low resolution of 1024x768

Not sure if the first 2 steps had anything to do with it but the last step for sure did it:

1- add medibuntu repositories [http://www.unixmen.com/how-to-add-medibuntu-repository-in-ubuntu-via-terminal-and-gui/](http://www.unixmen.com/how-to-add-medibuntu-repository-in-ubuntu-via-terminal-and-gui/)

2- add xorg crack pushers PPA:

```
ppa:xorg-edgers/ppa
``` to software center/edit/software resources other software/add

now just

```
sudo apt-get update && sudo apt-get upgrade
```There  were some packages held back from upgrading so I also did :

```
sudo apt-get dist-upgrade
```to force install them. This took  me to 3.5.0-15-generic kernel. Make suer all updates are installed.

3- Up to this point it still did not work but thanks to this web page 

[http://askubuntu.com/questions/152306/problems-with-intel-video-resolution-on-acer-laptop-wide-display](http://askubuntu.com/questions/152306/problems-with-intel-video-resolution-on-acer-laptop-wide-display)

It's all good now.

Basically, once you see the purple screen with little stick figure at  the bottom, click the space bar to get to the languages, press esc or  enter on English to get to grub menu, highlight the first choice and  press e for edit. Find quiet splash on the second line to last and type  nomodeset. Now press Ctrl X and it you are now in Ubuntu 12.04 but with  low resolution.

Now 

```
gksudo gedit /etc/default/grub
```and change the last two lines  of the file to (not the ones with #, look carefully, they should look  similar):```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash  acpi_backlight=vendor" GRUB_CMDLINE_LINUX="acpi_osi=Linux"
```press  save and then

```
sudo update-grub
```Restart and profit :guitar:

---

