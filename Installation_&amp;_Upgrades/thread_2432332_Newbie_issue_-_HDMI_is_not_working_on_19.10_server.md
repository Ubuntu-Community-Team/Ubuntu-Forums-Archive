---
title: "Newbie issue - HDMI is not working on 19.10 server/ rpi 4 install"
date: 2019-11-30
forum: Installation &amp; Upgrades
---

### Post by ccchill on 2019-11-30
Hi,

Long time lurker, first time poster...

I'm trying to install 19.10 server on a rpi 4 with 4gb ram.

I downloaded the ISO and flashed it to an SD Card using Rufus (partition FreeDOS and rest default settings).

Once RUFUS was done, I put the SD Card into the rpi 4 and plugged ethernet, usb keyboard, monitor in first before plugging in power.

Lights come on including ethernet but the monitor I have hooked up is not showing any activity.

I've tried two different SD Cards.

I feel like I'm missing something small but not sure as I'm fairly new to raspberry pi, especially rpi 4.

Any suggestions?

Many thanks!

---

### Post by gnusci on 2019-12-01
Try reintalling lightdm

sudo apt-get install --reinstall lightdm ubuntu-desktop

Which video card you have? post the ouput of:

lspci -k | grep -A 2 -i "VGA"

---

### Post by ubfan1 on 2019-12-01
The server release does not even have X, so you are expecting a console to appear on hdmi?   Can you ssh into the server?  Maybe you really want a desktop release -- you can add anything the server has like a web server.

---

