---
title: "Monitor issues"
date: 2006-06-30
forum: Installation &amp; Upgrades
---

### Post by jmank88 on 2006-06-30
I installed the latest version of ubuntu and the partitioning and installing all went fine, then i booted into ubuntu. The boot up screen shows up fine, and all the info on the bottom scrolls through, then the screen goes black and shows nothing, but there is a welcome noise or something. So the first time this happens i dont really know what to do cause it just stopped, so i hit the power button and then all of a sudden the screen shows up and there is a login prompt or something, then it goes back to terminal and displays all the shutdown jazz and whatnot, and turns off. So this time i boot up to try again and the same thing happens, blank screen. So then i type my username, enter, password, enter, and i hear another noise, login noise perhaps, and still nothing, just blank.
Im running an acer laptop, with a res of 1680x1050, so i dunno if its just having problems displaying or what, but it was perfectly fine during installing and the bootup screen. Is there something i can do from recovery? because that boots perfectly fine. Im sort of a linux newbie, so i dont know my way around the terminal very well, any help is greatly appreciated.

btw- reinstalling didnt help

-jordan

---

### Post by jmank88 on 2006-07-01
update: after doing some reading i tried ctrl+alt+f1 at the login screen, and the terminal pops up on the screen just fine. do i need to install some drivers for my ati card perhaps?

-jordan

---

### Post by jmank88 on 2006-07-01
got it all figured out ;) lol
updated to fglrx drivers or something? not really sure, just followed some stuff from the wiki and all is well lol

-jordan

---

### Post by cacharreo on 2006-07-01
I think you have selected default monitor resolution tha is not supported by this one.
Start in terminal mode and try:
***sudo dpkg-reconfigure xserver-xorg***
Be sure that the resolutions and frequencies that you select on the monitor configuration are supported by your monitor

---

