---
title: "Installation of Ubuntu 8.04"
date: 2008-05-21
forum: Installation &amp; Upgrades
---

### Post by Unr3a1r00t on 2008-05-21
Hey all.  I am new to these forums, and new to Ubuntu.  I am trying to install Ubuntu on my laptop, which it does, however, either the drivers don't get installed at all, or the wrong ones get installed for my network hardware.  Specifically my wired ethernet connection.  

The thing is though, that it works fine when I load the LiveCD.  Everything works perfectly.  However, when I go to install the OS actually on the hard drive, my ethernet card is not recognized, neither is my touchpad, or sound card.  So my question is how do I go about installing Ubuntu with the same configuration as the LiveCD?  This would be a big help.  Thanks.

---

### Post by Unr3a1r00t on 2008-05-22
No one has any suggestions?

---

### Post by kami_iwinaru on 2008-05-22
see if you can get on another computer that connects to the internet and download the drivers for your hardware for ubuntu
that is if the hardware is supported

---

### Post by Unr3a1r00t on 2008-05-22
Why would the LiveCD support my hardware, but not the installed version?  How can I install Ubuntu to my hard drive so that it works like the LiveCD?

---

### Post by Cap'n Skyler on 2008-05-22
> **Unr3a1r00t said:**
> Why would the LiveCD support my hardware, but not the installed version?  How can I install Ubuntu to my hard drive so that it works like the LiveCD?

first off,welcome to teh forums
Unreal,as in unreal tournament?
LOL
first--
it sounds like you need to go and set up and install your internet connection.
go to system
then administration
then network
you may have to click the "unlock" tab
from there highlight your connection and then click properties
 i always add a network icon to the bar at the top of the screen
you can do that by clicking the right mouse button on the bar
click add to panel
navigate to the internet icon and drag it to the panel.
then close
then right click the icon and click properties and select from the drop down box your connection type.that is,if it is different from what you have in your network settings you did prior to this.you can also use this 
to change the connection if you need to.make sure to save your settings otherwise you will need to re do all that each time you log in.
either of these will get you to the same point to work on the connection.:popcorn:

---

### Post by Cap'n Skyler on 2008-05-22
i dont know how to help with the touchpad--sorry
for the soundcard you need to open a terminal
go to applications
accessories
terminal
then you need to do you alsa configuration.
 sudo alsa config 
into your terminal and click enter
and if more issues than that
this should be a good start
[http://ubuntuforums.org/showthread.php?t=205449:popcorn:](http://ubuntuforums.org/showthread.php?t=205449:popcorn:)

---

