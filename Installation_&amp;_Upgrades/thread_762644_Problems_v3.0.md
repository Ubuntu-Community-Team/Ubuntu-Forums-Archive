---
title: "Problems v3.0"
date: 2008-04-22
forum: Installation &amp; Upgrades
---

### Post by Exsecrabilus on 2008-04-22
[color=red]**PLEASE READ EVERYTHING AND DO NOT JUST ASSUME MY PROBLEM! THANK YOU!**[/COLOR]

So I installed Ubuntu 8.04 RC amd64 fresh.

When I opened the new **Restricted Drivers Manager** called "Hardware Drivers" or something like that, I got confused.

It didn't have the drivers like Gutsy did:

[img]http://i212.photobucket.com/albums/cc134/Exsecrabilus/Picture1.png?t=1208872751[/img]



Instead, it only had one restricted driver, named ATI Firewall GL or something like that.

So here I am, writing this on Ubuntu 7.10 amd64 Live CD, waiting for a reply.

So here are my questions!:

1. Where did the Firmware-thing go in the Restricted drivers-thing? I need that to extract the .o file and help me connect to the Internet!

2. When I enable the ATI Firewall GL thing, it says I need to restart, and when I do, it says it's still not in use!

PLEASE HELP!!!!! Thanks.

---

### Post by Ayuthia on 2008-04-22
> **Exsecrabilus said:**
> 1. Where did the Firmware-thing go in the Restricted drivers-thing? I need that to extract the .o file and help me connect to the Internet!
From what I am reading, it looks like you have a Broadcom wireless card.  Hardy is using a new kernel that introduces a new Broadcom driver, b43.  It replaces the bcm43xx driver.  From what I can tell, there are some people who are having problems using the b43 driver if they have a 4306, 4311 rev02, and 4312.  If you want to use it, you will need to install b43-fwcutter.

---

### Post by Exsecrabilus on 2008-04-22
After I install that, how do I extract the .o file if a section for the Firmware doesn't appear in the Hardware Drivers thing?

---

### Post by Ayuthia on 2008-04-22
If I recall correctly, when you download b43-fwcutter from the repositories, it should run like the Restricted Drivers process once did.  It should ask you if you want it to download the .o file and then it will install the .fw files into the proper places in /lib/firmware.

If for some reason the b43-fwcutter does not run immediately after installing, you should be able to run the process by typing:
```
sudo /usr/share/b43-fwcutter/install_bcm43xx_firmware.sh
```
This is the script that is usually executed.  If you look at the script, you will see where it will grab the .o files and what it executes.  It also creates a temp directory where it will store the downloaded files and then it will remove that directory when it completes.

---

### Post by Exsecrabilus on 2008-04-22
This is what happens:

[color=red]I AM WRITING THIS FROM UBUNTU 7.10 AMD64 LIVE CD BECAUSE UBUNTU 8.04 AMD64 I INSTALLED WON'T CONNECT TO THE INTERNET.[/color]

I click on *b43-fwcutter_011-1_amd64.deb* and GDebi Package Installer opens up.

It installs it, and midway through, it asks me if I want to extract firmware from somewhere.
If I check and press Forward, the package breaks and I have to go to Synaptic Package Manager and completely remove it.
Then I install it again, this time *not* checking the box asking me if I want to extract a firmware file. It works.

I go to Hardware Drivers under System -> Administration. I open it, and here is what it looks like:

[img]http://i212.photobucket.com/albums/cc134/Exsecrabilus/Screenshot1-1.png?t=1208875811[/img]

I think to myself, how can it be in use if the box isn't checked?
So I click Enable, and this comes up:

[img]http://i212.photobucket.com/albums/cc134/Exsecrabilus/Screenshot2-1.png?t=1208875848[/img]

It needs a computer restart, so I give it a restart.

And guess what happens when I open up Hardware Drivers again? This comes up!:

[img]http://i212.photobucket.com/albums/cc134/Exsecrabilus/Screenshot1-1.png?t=1208875811[/img]

I think to myself, "What the heck?"

Here is my problem:

HOW DO I USE THE wl_apsta-3.130.20.0.o FILE THAT I HAVE SO I CAN CONNECT TO THE INTERNET?????

Please help and thanks for reading!

---

### Post by lswest on 2008-04-22
look at the tutorial [_here_]("http://linuxwireless.sipsolutions.net/en/users/Drivers/b43") it gives you all you need to know.  Also, if your card is a BCM4311 rev2 (check with "lspci" in the terminal) the new kernel 2.6.24-16 doesn't support it anymore, as they removed the patch that patched up some compatibility problem with the b43 driver (at least, last time i checked, my hardy still runs on the 2.6.24-12 kernel).

---

### Post by Exsecrabilus on 2008-04-22
[color=gold]I went there and looked, but it's not easy, you see.

As I have said, I am typing this on a 7.10 LIVE CD, not on the installed Ubunu 8.04.

And if I copy that documentation and put it onto my flash drive and import it onto my system, I don't have Internet so it won't work.

If I follow the directions now, I don't need it since I can already make Ubuntu 7.10 connect to the Internet.

So can someone please give me a simplified set of directions? That'd be so much help.....thanks.

---

### Post by Ayuthia on 2008-04-22
> **Exsecrabilus said:**
> This is what happens:

I think to myself, "What the heck?"

Here is my problem:

HOW DO I USE THE wl_apsta-3.130.20.0.o FILE THAT I HAVE SO I CAN CONNECT TO THE INTERNET?????

Please help and thanks for reading!
Ok.  I just made the connection.  You don't have an internet connection while you are on 8.04 (that is what caused the break).  If I recall correctly, you will have to install b43-fwcutter again and then not have it download the driver for you (or else it will get stuck again).  You do need to have two files--the wl_apsta-3.130.20.0.o and broadcom-wl-4.80.53.0.tar.bz2.  You can them here (I know that you have the first one):
```
http://downloads.openwrt.org/sources/wl_apsta-3.130.20.0.o
http://downloads.openwrt.org/sources/broadcom-wl-4.80.53.0.tar.bz2
```Store those files in the same folder.  You will need to go to the Terminal and cd to the folder where you stored the files and type the following:
```
sudo b43-fwcutter -w /lib/firmware wl_apsta-3.130.20.0.o
tar xfvj broadcom-wl-4.80.53.0.tar.bz2
sudo b43-fwcutter --unsupported -w /lib/firmware broadcom-wl-4.80.53.0/kmod/wl_apsta_mimo.o
```That should get you installed.

---

### Post by Exsecrabilus on 2008-04-22
Omg Omg Omg Omg Omg!!!!!

It Worked!!!!!

I Am Writing This On My Installed 8.04!!!!!

Thanks So Much!!!!!

You Are The Best!!!!!

---

