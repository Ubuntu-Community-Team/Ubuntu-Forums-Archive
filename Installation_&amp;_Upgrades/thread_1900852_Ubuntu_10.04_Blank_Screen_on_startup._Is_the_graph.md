---
title: "Ubuntu 10.04 Blank Screen on startup. Is the graphics card the problem? EN9500GT"
date: 2011-12-27
forum: Installation &amp; Upgrades
---

### Post by andrewhg on 2011-12-27
Hi I am new to Ubuntu. I recently had Ubuntu 10.04 installed on my computer. It worked great the first day, second day it was freezing a bit then it froze a bit on the third day it froze and a bunch of text started to appear on a black screen. I restarted and ended up getting tty2 which I guess is the terminal.  
I logged on as my user. From the research I have done I think that it might be related to my graphics card? I have a EN9500GT. 
The rest of my system is as follows.
A-Data 2GB DDR2
Asus P5QL Pro
Intel C2Q 2.33ghz
WD5000AAKS

EDIT: I tried 'startx' mainly because I didn't know any better and got a bunch of gibberish. The part that hints at some sort of error seems to be "(EE) Microsoft Mocrosoft(R) 2.4 GHz Transceiver v6.0 failed to initialize for relative axes...."
I am new to ubuntu so you will have to speak slowly :)
Thanks

---

### Post by jerrrys on 2011-12-28
If graphic drivers are needed, its usually from day one.  So not owning one, I cannot say for sure.  The links below show some possibilities.

[http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=9500GT+driver&sa=Search&cof=FORID:9](http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=9500GT+driver&sa=Search&cof=FORID:9)

[http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=9500GT&sa=Search&cof=FORID:9](http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=9500GT&sa=Search&cof=FORID:9)

Did you update after you installed ubuntu?

If not, open up a tty and enter:

sudo apt-get update

and if that works without any errors; enter:

sudo apt-get upgrade

Also when you enter your password, there will be no visual verification in terminal when entered.

Please post back with any questions you may have.

EDIT:  also **Ctrl Alt F7** will terminate your tty session and return you to your desktop.

if you have one

---

### Post by andrewhg on 2011-12-28
I just suspected that my graphics card might be the problem, you should definitely not take my word for that. I really have no idea:). Yes I updated after installing and it was working fine for the first couple of days. There is obviously some problem with either my hardware or software. How do I fix this.That is, what steps do I take with ubuntu 10.04 to diagnose a problem and fix it? I am not interested in becoming an ubuntu admin just to fix a standard stable installation of ubuntu. Thanks for your help. :P

---

### Post by andrewhg on 2011-12-28
When I press ctrl-alt-f7 i get
Speech-dispatcher configured for user sessions
starting virtualbox kernel modules
starting commin unix printing system:cupsd
pulseaudio configurerd for pre-user sessions
enabling additional executable binary formats binfmtp-support
checking battery state..... (and this is a desktop installation)

each with [ok] 
 and then it just sits there and does nothing.

---

### Post by dFlyer on 2011-12-28
From a terminal enter:

cd /var/log          (press enter)

than use the last command to read your log files. Hopefully something will be there to help ID the problem.

---

### Post by andrewhg on 2011-12-28
Lots of logs in there. I changed my user to root then tried to open boot.log
open boot.log    didn't work. 
How do I open documents and read their contents? Which logs should I check first? Are beginner users expected to wade through log files to find problems with fresh installations? Doesn't seem very user friendly.

---

### Post by jerrrys on 2011-12-29
dFlyer is trying to pin down the problem and I am trying general fixes.  Something else to try:

At boot, drop back one kernel version in the grub menu.  The kernel you are running will be the top one (usually generic),  You need to drop down to the previous kernel.  If your grub menu is not shown during boot you will need to press **ESC** during timeout. 

[https://help.ubuntu.com/community/Grub2#Boot_Display_Behavior](https://help.ubuntu.com/community/Grub2#Boot_Display_Behavior)

---

