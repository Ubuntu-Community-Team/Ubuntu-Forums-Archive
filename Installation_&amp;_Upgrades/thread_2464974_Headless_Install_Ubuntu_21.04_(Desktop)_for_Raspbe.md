---
title: "Headless Install Ubuntu 21.04 (Desktop) for Raspberry Pi 4 using Serial UART PuTTY?"
date: 2021-07-17
forum: Installation &amp; Upgrades
---

### Post by rajhlinux on 2021-07-17
Hello ):P,

I want to install Ubuntu onto my Raspberry Pi 4 using the desktop release build, not the server release build, because I do not have the time for the Pi to install all the huge packages and massive downloads via the internet for the desktop environment when using the server release build.

Now with that said, Ubuntu made it extremely difficult for raspberry pi users to enable SSH-server on the desktop build since it does not come with it. Yes, ubuntu expects pi users to hook up a monitor, keyboard and mouse for the first installation or use the server release build.

Theres a tutorial on how to use the Pi's UART interface and connect the pins to a TTL to USB converter and this will allow users to communicate with the raspberry Pi without all the hassle of a monitor, keyboard and mouse.

Here is the link to the tutorial: [https://limesdr.ru/en/2020/10/17/rpi4-headless-ubuntu/](https://limesdr.ru/en/2020/10/17/rpi4-headless-ubuntu/)

This actually works, (Thank Goodness). But the problem is the tutorial is for Ubuntu Mate and not for Ubuntu 21.04 (Desktop Release), and now I can not figure out the user "login" and "password" credentials when I am on the serial console on PuTTY communicating with the Raspberry Pi 4.

I tried all kinds of passwords and logins and none of them works. ](*,)
Maybe I am doing something wrong? :-k
I read that there is no login and password for Ubuntu installation Live CD system. :(
If this is the case, then why is the serial console keep asking for one and rejecting all the common credentials? :-s

I downloaded the 20.04 desktop build straight from Ubuntu's website for Raspberry Pi.

I also included a picture of where I get stuck with the Ubuntu 21.04 installation login via Serial Console:

[IMG]https://i.imgur.com/BnlOIAh.jpg[/IMG]
PuTTy Serial Console on Windows 10 using a "USB to TTL converter" device connected to the Raspberry Pi 4.


Any advice or help would be great to get this working, Thanks. :-)

Edit problem fixed:

All I had to do was to add a password into the "etc/shawdow" file.
Since Ubuntu does not add a root password in their installers, you need to add one yourself.
Here is a youtube video on how to do it:
[https://www.youtube.com/watch?v=vyG1bMk522I](https://www.youtube.com/watch?v=vyG1bMk522I)

Here is a pic of me logged into Ubuntu 21.04 desktop release as root:

[https://i.imgur.com/N4Y7TTT.jpg](https://i.imgur.com/N4Y7TTT.jpg)

All I needed is an Ubuntu desktop installation. I do not need security updates, since it is for a project not connected to the interwebs. 
Now I can install Ubuntu 21.04 Desktop into the raspberry pi 4 heedlessly. :guitar:

---

### Post by ActionParsnip on 2021-07-18
Install server image then install something like lxde or xfec4. It will install a DM for you and you'll get a desktop OS. It will work just fine.

---

### Post by ActionParsnip on 2021-07-18
I also recommend Ubuntu 20.04 as it is LTS, Hirsute (Ubuntu 21.04) is only supported for 9 months and you'll need to upgrade to the next release for continued support when Hirsute goes end of life

---

### Post by rajhlinux on 2021-07-18
Thanks for your replies. So it is just the curiosity of logging into the serial console of the Ubuntu installer.

Is there anyway how I can setup or modifying the boot files to be able to login and install Ubuntu thanks to UART TTL serial communication?

This is just for future reference so that I can be able to do the same for a new release or installation.

Thanks.

---

### Post by MAFoElffen on 2021-07-19
I also have a Raspberry Pi4 and have Ubuntu Desktop 20.04 LTS installed. The Rasp images for Ubuntu already have a user setup with a password.

If you install the 21.10 desktop image, it's going to boot first into the installer, and it  is going to ask you to setup a user and password. Unfortunately, I couldn't find a 20.04 image for Desktop any where.

The Server images that are compatible for Pi4 start out at version 19.10 on. To get an  To get a LTS version of Desktop, I had to start out with the 20.04 LTS version Server image, then upgrade and install ubuntu-desktop. The prebuilt server image comes with openssh-server installed. The process didn't take that long, compared to the x*^ version as the AArm64 packages are much smaller. The image already has a default user and password setup.

The default user is: ubuntu
The default password is ubuntu

Not sure on doing just serial, but should be the same as serial console... with is just a text screen. Surprisingly,it runs very well.

I also had an SD card setup for Ubuntu Server 20.04 LTS.

My question is how you plan on using the desktop version as headless? As the desktop version is going to try to bring up Xorg XServer... It doesn't seem to matter though. Mine still comes up if I don't have the monitor turned on, and ssh into it from my other computer. Probably okay. Then just ssh'ing into it...
.

---

