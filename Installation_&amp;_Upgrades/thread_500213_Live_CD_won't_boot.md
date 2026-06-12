---
title: "Live CD won't boot"
date: 2007-07-13
forum: Installation &amp; Upgrades
---

### Post by john8791 on 2007-07-13
I have a Dell Inspiron E1505 laptop with an ATI Radeon X1300 video card and Duo processor.  The Feisty live CD gets to the point where you can select the boot method but then the screen goes blank about 30 seconds later and the CD stops spinning.  I have tried all the standard stuff like noacpi but nothing seems to work.  Is there an issue with processor or video card.

---

### Post by Pumalite on 2007-07-13
You might want to take a look at this thread. It'ss not EXACTLY your box , but I think a lot of the issues discussed might interest you. You could have problems with your graphics and/or wifi.

[http://ubuntuforums.org/showthread.php?t=399913](http://ubuntuforums.org/showthread.php?t=399913)

---

### Post by wpshooter on 2007-07-13
> **Pumalite said:**
> You might want to take a look at this thread. It'ss not EXACTLY your box , but I think a lot of the issues discussed might interest you. You could have problems with your graphics and/or wifi.

[http://ubuntuforums.org/showthread.php?t=399913](http://ubuntuforums.org/showthread.php?t=399913)

You mean you have to read and do all of that just to get the O/S installed ???

---

### Post by Pumalite on 2007-07-13
You mean you have to read and do all of that just to get the O/S installed ???

It's always better to be well informed and prepared for what's coming.

---

### Post by john8791 on 2007-07-23
Sorry for the delay in getting back.  It is my wife's laptop; I just want to run the live cd for a while before installing.  Is there a way to modify the live cd to incorporate the dellinstall script?

---

### Post by Pumalite on 2007-07-23
Sorry, I don't know. Somebody will jump in, I hope.

---

### Post by jynyl on 2007-07-26
Similar problem here, in that the live CD won't boot.  Hardware here is HP laptop with ATI x1600.
This works for me on Kubuntu 7.04;
1. At the first screen after starting on the live CD, press F4 and select 640x480x16.
2. Start up, although this gives a black screen.
3. Ctrl Alt F1 to get command line.
4. Enter command
  sudo dpkg-reconfigure -phigh xserver-xorg
then select vesa 640x480
5. Enter command
  sudo killall kdm
(May then need ctrl alt F1 to get back to command line.)
6. Enter command
  sudo kdm

This got the Kubuntu 7.04 live CD working on my laptop.

HTH

Peter

---

### Post by john8791 on 2007-07-26
Well, it certainly got farther this time.  Why does'nt bootong to safe graphics mode work the same way?  I didn't have to ct-alt-f1 to get to the console because the X server crashed and did it for me.  I could not get the command:
sudo dpkg-configure -phigh xserver-xorg to work at all.  It says something like "-o option invalid". 

 I looked at the /etc/X11/xorg.conf file already said "vesa" under the display section but the X server will not start.  Any idea what's going on here?

Thanks!

---

### Post by jynyl on 2007-07-26
Oh sorry - my bad, typo in that command :(
should be ...
  sudo dpkg-reconfigure -phigh xserver-xorg

My apologies, I'm typing this in on another PC.

HTH

---

### Post by jynyl on 2007-07-26
Also, are you running Ubuntu or Kubuntu or ?
I'm running Kubuntu 7.04 here.
If you are using Ubuntu, you might need to change kdm in the above commands to gdm or something.

HTH

Peter

---

### Post by john8791 on 2007-07-26
Thanks for the clarification.  I'll give it a try tonight.  I am running standard Ubuntu.  I tried both gdm and just startx with the same result.

---

### Post by john8791 on 2007-07-26
Got it working!  Thanks for the assistance!:)

Just for anyone else with a Dell E1505, here's a recap of JYNYL's instructions modified for Ubuntu (gdm):

1. At the first screen after starting on the live CD, press F4 and select 640x480x16.

2. After a few minutes of the startup bar going back and forth, the X server will crash and a badly formatted text screen will come up asking you if you want to troubleshoot.  Answer No, and No again.  You will then be at the Linux command line.

3. Enter command:
sudo dpkg-reconfigure -phigh xserver-xorg
then select vesa,  640x480 (make sure all other resolutions are not unselected or it won't work!

4. Enter command:
sudo killall gdm

6. Enter command:
sudo gdm

Everything including my sound and wireless networking took right off.  Hopefully the Ubuntu developers will fix this on the next release.  I still don't understand why "safe graphics mode" does not work.

---

