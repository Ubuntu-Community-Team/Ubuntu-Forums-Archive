---
title: "Small screen after installing 10.4 on Laptop"
date: 2010-07-24
forum: Installation &amp; Upgrades
---

### Post by Richard3 on 2010-07-24
Hi. I am a new user. I installed 10.4 on my Satellite Pro via CD replacing XP.

Screen resolution is now only 800x600 which fills only 3/4 of available screen space and there are no greater options in System Preferences Monitors. It is also operating rather slower than the previous OS, maybe these two  issues are connected?

I have checked Administration for any required Proprietary Drivers. There is just one for a modem which is activated.  

During installation I aborted it then closed down and restarted, which may have  affected the process? 

Any advice as to how to increase the visible screen area?

---

### Post by davidmohammed on 2010-07-24
difficult to say without knowing what your graphics card is....

in a terminal type

lspci | grep VGA

also

copy and paste the contents of the file (if it exists) here

/etc/X11/xorg.conf

finally in a terminal run

xrandr

and copy and paste the contents here.

---

### Post by Richard3 on 2010-07-25
Took me a little while to work out your instruction and carry them out as I am new to this

Result as follows doesn't look encouraging

01:00.0 VGA compatible controller: Trident Microsystems CyberBlade XPAi1 (rev 82

gedit/etc/X11/xorg.conf: No such file or directory

Screen 0: minimum 320 x 240, current 800 x 600, maximum 800 x 600
default connected 800x600+0+0 0mm x 0mm
   800x600        60.0*    56.0  
   640x480        60.0  
   400x300        60.0     56.0  
   320x240        60.0

---

### Post by Krabby.Linux on 2010-07-25
Do you have a monitor? Connect it if you have one and take a look on the display. Is it the same there?

---

### Post by Richard3 on 2010-07-25
It displays full screen on the monitor

---

### Post by Richard3 on 2010-07-25
Yes I do have a separate monitor I have connected it and it displays full screen

---

### Post by overdrank on 2010-07-25
Hi and welcome, You may look [here]("http://ubuntuforums.org/showthread.php?t=830643&highlight=Trident") for some help.

---

### Post by Richard3 on 2010-07-25
Hi very useful thanks and I have learned a lot.
I have followed through on the links run the checker again and got the following:

Checking for texture_from_pixmap...               [ OK ]
 Checking for non power of two support...          [ OK ]
 Checking for composite extension...               [ OK ]
 Checking for FBConfig...                          [ OK ]
 Checking for hardware/setup problems...           [FAIL]

There has been (at least) one error detected with your setup:
 Error: Software Rasterizer in use 

I could do with a prompt as to how to repond

---

### Post by Richard3 on 2010-07-26
Hi

This is the steer I got from the Compiz Forum after following their guidance and then run the Compiz checker a couple of times

"Compiz will not work with that particular GPU. As for your screen  resolution problems, you should probably ask on the Ubuntu forums".

I now know that Compiz is not a solution. 

Is there any solution for supporting a rasterizer or rendering function in Ubuntu?

---

