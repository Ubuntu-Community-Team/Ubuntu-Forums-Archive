---
title: "New Laptop - Ubuntu 16.04 installs but fails to show unity or desktop"
date: 2016-04-24
forum: Installation &amp; Upgrades
---

### Post by ali60 on 2016-04-24
I'm trying to install Ubuntu on a new laptop: core i7-6820HK processor, Nvidia GeForce GTX 980M . 

When I boot via live USB, if I go into 'Try', it loads the desktop background, and I can  move the mouse pointer around  via the touchpad, but right click doesn't work. Unity doesn't load. And I see a lot of 'Ubuntu has experienced an internal error' popups, but they flash several times a second so its impossible to see the details. Ctrl + Alt T doesn't open terminal.

When I go under 'install', everything loads up correctly, I'm able to connect to wifi, and install Ubuntu. But when I boot after installation, I get to the same desktop background but no ability to right click, no unity, and after waiting a while, I see the 'Update information' dialog box, however this one also flashes several times a second so its impossible to react to it. Again unable to open terminal via ctrl + alt T.

It seems like other people are also having this issue, e.g: [http://ubuntuforums.org/showthread.php?t=2321090&p=13473075#post13473075](http://ubuntuforums.org/showthread.php?t=2321090&p=13473075#post13473075)

Any ideas?

I managed to get to terminal via ctrl + alt + f1, and there I tried to install the nvidia drivers, as per: [https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia#Ubuntu_14.04_and_up](https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia#Ubuntu_14.04_and_up)

However, it seems that its not connected to the internet, so it fails to resolve the apt repositories.

Since I don't get unity, I don't have any way of connecting to the internet via the applet.

Help please!

---

### Post by ajgreeny on 2016-04-24
If you have an ethernet port, try to attach an ethernet cable and update that way, then install the nvidia driver; you may then find all is running properly.

---

### Post by ali60 on 2016-04-24
Thanks for the reply.. I do  not have an  ethernet connection. Only wifi. Any other ideas?

If I do iwconfig wplans20 (or something like that), it does show my wifi connection

---

### Post by ubfan1 on 2016-04-24
You don't by any chance have an external monitor hooked up?  Your issues were like mine on a recent 16.04 install (but without Nvidia hardware).  The second monitor confused the desktop badly, and as a consequence, wireless (wlp1s0) was down.  Fix was to boot without the external monitor, then disable the laptop monitor, and just use the external.  Fixed everything.

---

### Post by ali60 on 2016-04-24
@ubfan1, no, I just have the laptop, no external monitor. My wifi does show up, i'm just not sure how to connect to it via the terminal. Were you experiencing the same issue w/ nothing but the desktop background showing up?

---

### Post by grahammechanical on 2016-04-24
There is something that you can try. At the Grub boot menu select Advance Options for Ubuntu and then select recovery mode. At the recovery menu select Resume. That might get you to a working desktop using a fall back open source video driver. Then you may be able to set up a WiFi connection and also use Additional Drivers to change video drivers.

It is strange that you were able to set up a WiFi connection during the installation process but you are not getting a WiFi connection now. The installed Ubuntu should have the network connection settings in Network Manager from the installation session.

The recovery menu also has a Network option that will make use of Network Manager's configurations file to set up an internet connection. Then selecting the Root shell prompt option we can run commands and remove or install video drivers. To update/upgrade

```
apt update
apt upgrade
```

You should not need an internet connection to purge the Nvidia driver.

```
sudo apt-get remove --purge nvidia-*
```

To find out what drivers are available for your video adapter

```
ubuntu-drivers devices
```

To install the current Nvidia driver

```
ubuntu-drivers autoinstall
```

When finished with the root shell prompt type exit to get back to the recovery menu and then select Resume.

Regards

---

### Post by ali60 on 2016-04-24
Thanks grahammechanical .

When I login via advanced -> resume, I get to the same 'desktop but no unity' screen. In the upper right corner I can see the 'wifi networks available' prompt which is flashing really fast over and over, so it can't be clicked. Everything just looks bigger, but not different from when I boot the normal way, i.e no unity, ctrl + alt + t doesn't open terminal, etc.

I tried to enable networking from the advanced menu, but it gets stuck on 'grep: /etc/resolv.conf: No such file or directory'.

I agree its weird that it didn't save my wifi info from the install. Just to confirm, I ctrl + alt + f1'd and did ping google.com, and got unknown host on that.

Edit: When I say desktop but no unity, i mean just the desktop background / wallpaper. There are no icons either.

---

### Post by ubfan1 on 2016-04-24
Your symptoms after install are pretty much just like mine.  From a virtual terminal, try running xrandr and see what the X stuff looks like.  My screen was 2304x1024, which was the sum of the two displays (1024+1280), and something in the desktop complained about an unreasonable screen size.  The only issue with wireless was that network manager was not running (because the desktop was borked), so fix the desktop first, and the wireless may just start working.  I did use xrandr to switch my primary monitor to the external one, booted with it unplugged, then the desktop straightened itself out, and worked (fixing wireless too).  Very strange, but trying to run networkmanager without the desktop was hopeless.

---

### Post by ali60 on 2016-04-24
ubfan1, When I try xrandr, I get 'can't open display' :(

Is it possible to download the nvidia drivers offline, and install them over a USB?

ubfan1, when I run xrandr, I get 'can't open display' :(

Is it possible to download the nvidia drivers offline, and install them over a USB?

I was able to use ethernet to install the nvidia drivers, but I'm having other issues now w/ the keyboard and trackpad. Made a new thread with them: [http://ubuntuforums.org/showthread.php?t=2321878&p=13476759#post13476759](http://ubuntuforums.org/showthread.php?t=2321878&p=13476759#post13476759)

---

### Post by veles666 on 2016-04-25
[COLOR=#000000][FONT=Ubuntu Mono]I have intel graphics and wasn't getting a desktop either, the following worked for me (ctr+alt+f1)
```
sudo apt-get remove --purge intel-*

```[/FONT][/COLOR]```
[COLOR=#000000][FONT=Ubuntu Mono]sudo ubuntu-drivers autoinstall[/FONT][/COLOR]
```[COLOR=#000000][FONT=Ubuntu Mono]
Then just reboot:
[/FONT][/COLOR][COLOR=#000000][FONT=Ubuntu Mono]```
sudo shutdown -r now
```[/FONT][/COLOR]

---

### Post by ali60 on 2016-04-25
**** YEAH

OK, I re-installed ubuntu, re-installed nvidia-361 drivers, rebooted, and now MAGICALLY ITS WORKING

HOWEVER, my touchpad buttons are still not working. Moving the mouse around works, but pressing the right / left click buttons on the touchpad don't work.

Any ideas on that?

One thing I changed - this time I didn't encrypt my hd, so i no longer have to come across that 'enter password to unlock' hd screen. But at least the rest of it works.

Any ideas on making the touchpad buttons work?

---

### Post by veles666 on 2016-04-26
There's some tips for troubleshooting touchpad here:
[https://wiki.ubuntu.com/DebuggingTouchpadDetection](https://wiki.ubuntu.com/DebuggingTouchpadDetection)

---

