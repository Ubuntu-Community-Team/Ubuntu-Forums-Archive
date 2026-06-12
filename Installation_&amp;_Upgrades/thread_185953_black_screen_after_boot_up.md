---
title: "black screen after boot up"
date: 2006-06-01
forum: Installation &amp; Upgrades
---

### Post by richie60 on 2006-06-01
I currently use Mepis at the moment, but thought I would give the latest Ubuntu 6.06 a try.  After downloading & burning to a disc, it boots up fine, I hear sound (drum roll, etc) but have a black screen.  Help.

Current hardware is an ATI Radeon X700 AGP 8x, AMD Sempron 2800+, MSI NForce Delta motherboard, 512 MB RAM.

This seems to be a problem unique to Ubuntu as I have tried a few other distros it the past with no problems.

Richie

---

### Post by midna on 2006-06-01
Same Problem Here... Watched the brown ubuntu screen bootup sequence, and then everything went black. Cool startup sound plays but no visual. I than alt-ctrl-f1 and i can see the alternative text screens but no gui. Maddening really. 

NVIDIA 6800, AMD64 fx-55, Asus sli-delux, 1 gig Ram

---

### Post by midna on 2006-06-01
Got the solution from irc. Soundray, great guy told me once i was booted up inside the install cd to ctrl-alt-f1 to the first screen than. sudo dpkg-reconfigure xserver-config and enable vesa but change nothing else. No auto-detect. Next restart gdm. And walla it worked for me..

---

### Post by richie60 on 2006-06-01
Thanks for the advice, i'll give that a try...

Richie

---

### Post by Carrots171 on 2006-06-02
This happened to me back when I had an Nvidia 6200. I had to install the official nvidia drivers to get it to work. I'd suggest installing the appropriate drivers for your graphics card. Press ctrl+alt+f1 to get into a command line.

[Click here]("http://easylinux.info/wiki/Ubuntu_dapper#How_to_install_Graphics_Driver_.28NVIDIA.29") for the commands to install Nvidia drivers.

---

### Post by richie60 on 2006-06-02
Well I didnt have much luck figuring this out.  Went through a few screens of gibberish, then got a fatal server error at the end.

---

