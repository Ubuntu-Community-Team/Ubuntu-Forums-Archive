---
title: "jaunty installation 90% complete and nothing happens"
date: 2009-04-08
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by jayramj on 2009-04-08
Hello,

I am trying to install Jaunty Beta on my desktop. I want to have a dual boot with Windows 2000. 

Installation goes through fine till its 90% complete and installer tries to detect the hardware. At this point the installation progress bar disappears. The Gnome Desktop is displayed like when you run from Live CD. But installation is not complete. After waiting for ever if I reboot, I get a Grub error.

I have installed all versions since 7.04 on the same desktop without a glitch.  

Thanks in Advance

Regards
Jayram

---

### Post by ramjet_1953 on 2009-04-08
Hi, there!

Did you check the integrity of your installer CD before using it?
There is a menu item when the disk first boots.

Also when you burnt the iso did you burn it as slowly as possible on good quality media?

Regards,
Roger ;)

---

### Post by jayramj on 2009-04-10
> **ramjet_1953 said:**
> Hi, there!

Did you check the integrity of your installer CD before using it?
There is a menu item when the disk first boots.

Also when you burnt the iso did you burn it as slowly as possible on good quality media?

Regards,
Roger ;)

Yes. I verified the MD5 checksum. It was correct. Also when I run ubuntu from the same CD as "LiveCD" it works fine.

---

### Post by RIchard James13 on 2009-04-10
I found that because I had a slow Internet connection Ubuntu would halt at about 90% while it searches for updates. Don't know if that is your problem?

---

### Post by cl333r on 2009-04-10
> **jayramj said:**
> Hello,

I am trying to install Jaunty Beta on my desktop. I want to have a dual boot with Windows 2000. 

Installation goes through fine till its 90% complete and installer tries to detect the hardware. At this point the installation progress bar disappears. The Gnome Desktop is displayed like when you run from Live CD. But installation is not complete. After waiting for ever if I reboot, I get a Grub error.


I had a similar problem, also with Jaunty, because I chose "Install Ubuntu" (2nd option)
The workaround was: I inserted the same CD but this time I chose "Try Ubuntu without.." (the 1st option), got into the live session and from there chose "Install" (the icon on the desktop) and the installation completed 100%.
Could work for you too.

BTW I don't know whether it's reported as a bug or not, but Ubuntu should really disable the screensaver when in live session cause during installation the screen goes black and makes one think the PC is screwed, and only a key press brings it back - mouse won't help.

---

### Post by amano on 2009-04-10
Please file a bug and mention cl333r's workaround, if it works for you.

---

### Post by jayramj on 2009-04-11
> **cl333r said:**
> I had a similar problem, also with Jaunty, because I chose "Install Ubuntu" (2nd option)
The workaround was: I inserted the same CD but this time I chose "Try Ubuntu without.." (the 1st option), got into the live session and from there chose "Install" (the icon on the desktop) and the installation completed 100%.
Could work for you too.



I tried this but it didn't work for me.

Also it doesnt seem to be problem with slow internet connection because it has already configured APT and detected mirrors. I believe these are the 2 actions for which it needs internet connection.

It doesnt go beyond the point where it says "Detecting Hardware". From there, the installation takes me back to livecd

---

### Post by ashmew2 on 2009-04-11
Same Problem here..Didnt know this thread existed so i made one here : [http://ubuntuforums.org/showthread.php?t=1122425](http://ubuntuforums.org/showthread.php?t=1122425)

The only difference was that instead of the LiveCD , i used the LiveUSB(Made using UNetBootin).

---

