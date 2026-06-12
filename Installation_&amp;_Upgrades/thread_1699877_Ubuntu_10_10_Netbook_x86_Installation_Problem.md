---
title: "Ubuntu 10_10 Netbook x86 Installation Problem"
date: 2011-03-04
forum: Installation &amp; Upgrades
---

### Post by Malc_Hegarty on 2011-03-04
I've just installed v10_10 x86 Netbook on an old Thinkpad T42 laptop I've been given. 
 
It appears to install OK but at the desktop if I move the mouse to the icons on the bar at the left of the screen the screen flashes multiple times, preventing me from accessing any of these icons.
 
I am an absolute beginner with Ubuntu. This looks like some sort of graphics problem and I foolishly didn't note any of the driver names before installing Ubuntu.
 
If anyone can help I would very much appreciate it.

---

### Post by sikander3786 on 2011-03-04
Welcome to the forums :-)

Please post your hardware specs and compare them with recommended one's for Ubuntu here.

[https://help.ubuntu.com/community/Installation/SystemRequirements](https://help.ubuntu.com/community/Installation/SystemRequirements)

If your Netbook is not up to the mark in specs, you can consider a light weight of Ubuntu called Lubuntu.

[http://lubuntu.org](http://lubuntu.org)

---

### Post by Malc_Hegarty on 2011-03-04
Thanks for your reply, it isn't a netbook it's an old ThinkPad T32 laptop.
 
Spec meets the minimum requirements, it's  Intel Pentium M 1.6GHz, 1GB RAM, 40GB hard disk, network card, DVD/CD-RW drive and the graphics card can easily handle the minimum res.

---

### Post by sikander3786 on 2011-03-04
Sorry I missed an important query in the above post. Which graphics card is there and are there any proprietary drivers installed?

Can you please log out, click your user name at the login screen and select 'ubuntu-desktop' from the Sessions menu near the bottom of your screen. Then type your password and login. Do things improve?

---

### Post by Malc_Hegarty on 2011-03-05
Thanks sikander3786, this has improved things a lot. I'm now going to get all the updates down.
 
Bearing in mind I don't know which graphics controller or card is in the laptop, is there any way I can check the correct graphics driver is installed?
 
Thanks again.

---

### Post by Matt__ on 2011-03-05
the gfx  card on that machine should be a [ATI Mobility Radeon 7500 16M DDR](http://www-307.ibm.com/pc/support/site.wss/document.do?lndocid=MIGR-41918) (T30 series)
//edit hmm other sources (an associate of mine) say the graphics are onboard intel....

[more specs here](http://www.ertyu.org/steven_nikkel/thinkpadspecs.html)

for more specs on your machine open terminal and do:
```
sudo apt-get install hardinfo
```

also in terminal
```
lspci
```

---

### Post by Malc_Hegarty on 2011-03-05
Thanks for all the info Matt, very much appreciated.
 
The first command you listed installed something and then the second one listed my main hardware components and the graphics card is indeed an ATI Mobility Radeon 7500.
 
Cheers.

---

### Post by sikander3786 on 2011-03-05
The new netbook interface is 3-D and you need to install the proper drivers for your graphics card before you can use the netbook interface. Until then, you can keep using the desktop session.

And I can't be of much help on how to install the drivers for you ATI mobility. You can check under System > Administration > Additional Drivers and if available, install the current version.

If not, you can start a new thread under the 'Multimedia & Video' sub-forum as most of the graphics issues are hosted there and the experts are there.

Hope you enjoy your stay with Ubuntu!

---

### Post by Matt__ on 2011-03-05
> **Malc_Hegarty said:**
> Thanks for all the info Matt, very much appreciated.
 
**[COLOR=Navy]_The first command you listed installed something _[/COLOR]**and then the second one listed my main hardware components and the graphics card is indeed an ATI Mobility Radeon 7500.
 
Cheers.

Look in applications/system tools/system profiler and benchmark or type hardinfo into the terminal.

I also suggest you stick with the desktop version, but thats my personal preference. I use desktop on my 10" netbook, make title bars as small as possible (8pix i think), remove all panels and run a dock (cairo, but there are lighter versions like docky/awn)

---

