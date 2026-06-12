---
title: "Xubuntu 7.10 on a Toshiba Satellite 1800 (xserver-xorg issues)"
date: 2007-12-09
forum: Installation &amp; Upgrades
---

### Post by wheezy360 on 2007-12-09
I'm having a heck of a time getting X/Ubuntu installed on my Toshiba Satellite 1800 laptop.  Understandably so, as it is a rather old machine (Intel Celeron 800MHz / 128 Mb RAM / don't even want to guess at the video).

It is constantly failing at configuring/starting xserver-xorg.  In several different attempts, I've tried the following:  *(Note, all installations were Alternate Installation CDs, integrity verified)*

[LIST]
[*]Installing Ubuntu 7.10 in Text Mode /  **fails at "Configuring xserver-xorg" - Shows a blank screen with flashing cursor in upper left**

[*]Installing Ubuntu 7.10 **Command Line** and subsequently trying to run *apt-get-install ubuntu-desktop* / **fails, not exactly sure when as I was out of the room, but same symptoms as above**

[LIST]
[*] When trying to remedy the above installation using *sudo -dpkg --configure -a* it will **fail at "Launching xserver-xorg" and leave me with the same blinking cursor as above**
[/LIST]

[*]Installing Xubuntu 7.10 in Text Mode /  **fails at "Configuring xserver-xorg" - Shows a blank screen with flashing cursor in upper left**

[*]Installing Xubuntu 7.10 using the boot: command *install debian-install/framebuffer=false* (or similar, don't remember the exact syntax offhand but that's the idea) **fails, again not totally sure where as I was out of the room, but same symptoms**

[*]Installing Xubuntu 7.10 Command Line
[/LIST]

So, I'm at the last bullet right now, wondering how (if possible) I can go about getting a desktop installed, or figuring out just what's the fuss with xserver.  Any suggestions?  I understand that the hardware is limited, perhaps too much, so if you don't think it'd be possible I'd like to hear that just the same.

---

### Post by DM-125 on 2007-12-09
I also have an older Toshiba 1800 laptop that is giving me the same problem :(

I was able to install a command line system under xubuntu alternate install cd...  
but it isn't what i wanted as i am a total linux noob.

this dosn't realy help but at least you are not alone.  :)

---

### Post by pmiln099 on 2008-01-07
Any solution to these problems yet? Ubuntu 6.06, 6.10, and 7.04 all work fine on my Toshiba 1800. 7.10 comes up with a black screen after either upgrading from 7.04 or after install with alternate CD. Feel free to PM me if you have a workaround.

---

### Post by thierman on 2008-01-09
FYI, this is also being discussed in the following thread:

[http://ubuntuforums.org/showthread.php?t=652905](http://ubuntuforums.org/showthread.php?t=652905)

I've also submitted a bug report.

---

### Post by thierman on 2008-01-12
Just in case anyone is still running into this and hasn't found this thread. The solution posted in this thread fixed my problem.


[http://ubuntuforums.org/showthread.php?p=4123324#post4123324](http://ubuntuforums.org/showthread.php?p=4123324#post4123324)

---

