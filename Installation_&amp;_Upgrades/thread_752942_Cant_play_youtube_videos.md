---
title: "Cant play youtube videos"
date: 2008-04-12
forum: Installation &amp; Upgrades
---

### Post by Neil_The_Newbie on 2008-04-12
Why isnt anything in Ubuntu straight forward?

I am running 7.10 i have installed flash and and restricted extras but still cant play youtube videos

I get the message "Hello, you either have JavaScript turned off or an old version of Adobe's Flash Player. Get the latest Flash player."

Javascript isnt turned off so i am assuming that i have an old version of flash player?

Any ideas?

---

### Post by PmDematagoda on 2008-04-12
Post the output of:-
```
sudo apt-get install flashplugin-nonfree
```

---

### Post by Neil_The_Newbie on 2008-04-12
i typed that and got
Reading package lists... Done
Building dependency tree       
Reading state information... Done
flashplugin-nonfree is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

---

### Post by theduffman on 2008-04-12
Dunno about anyone else but i have to manually install it from the tar.gz package from adobes site...  when asked for firefox path i use /usr/lib/firefox

---

### Post by james_bandido on 2008-04-12
i had the same problem before ... 
go to --> [http://www.adobe.com/shockwave/download/download.cgi?P1_Prod_Version=ShockwaveFlash](http://www.adobe.com/shockwave/download/download.cgi?P1_Prod_Version=ShockwaveFlash)
download and install the appropriate version ...
hope this works for you coz it worked for me ... 
cheers !!!

---

### Post by Neil_The_Newbie on 2008-04-12
thanks for that. i'm a complete novice so you will have to forgive me - but how do i install it once i have downloaded it onto my desktop?

thanks in advance

---

### Post by a-converted-sparky on 2008-04-12
I ran the downloaded file in terminal:

sparky@ihatems:~$ sudo /home/sparky/Desktop/install_flash_player_9_linux/flashplayer-installer 

Enter your root password

Output is:

Copyright(C) 2002-2006 Adobe Macromedia Software LLC.  All rights reserved.

Adobe Flash Player 9 for Linux

Adobe Flash Player 9 will be installed on this machine.

You are running the Adobe Flash Player installer as the "root" user.
Adobe Flash Player 9 will be installed system-wide.

Support is available at [http://www.adobe.com/support/flashplayer/](http://www.adobe.com/support/flashplayer/)

To install Adobe Flash Player 9 now, press ENTER.

To cancel the installation at any time, press Control-C.



NOTE: Please exit any browsers you may have running.

Press ENTER to continue...



Please enter the installation path of the Mozilla, Netscape,
or Opera browser (i.e., /usr/lib/mozilla): /usr/lib/firefox


----------- Install Action Summary -----------

Adobe Flash Player 9 will be installed in the following directory:

Browser installation directory = /usr/lib/firefox

Proceed with the installation? (y/n/q): y

Installation complete.


Perform another installation? (y/n): n


Please log out of this session and log in for the changes to take effect.


The Adobe Flash Player installation is complete.

---

### Post by Neil_The_Newbie on 2008-04-12
thanks for that. i ran it in terminal and it now works!

---

