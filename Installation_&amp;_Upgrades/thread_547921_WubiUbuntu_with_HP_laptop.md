---
title: "Wubi/Ubuntu with HP laptop"
date: 2007-09-10
forum: Installation &amp; Upgrades
---

### Post by celtic426 on 2007-09-10
Hey guys,

I have a fairly new HP dv6000 series laptop.  I know that these hp's are pretty bad with linux and can be difficult to install.  That's pretty much what I need help with.  First of all, I have tried about 10 different live cd's of different distros and I have had a problem with all of them.  Most of them just crash or blank out at some point.  Now I am using Wubi to try to install Ubuntu onto my Windows Vista Machine (I want to keep Vista).  The Wubi set up goes well and everyone works until the Ubuntu loading screen comes up.  It completes the load then after more writing comes up, and then the screen goes blank.  But it doesn't just go black, it's like the actual plasma or whatever inside the screen goes away like the computer is shut down.  But the computer is still on.  I have read some tutorials and help online and I have tried adding things like "no alcid" and those 5 things like that to the boot string.  This has not worked.  Acutally when I add those things to the boot string I think the process gets a little further and something says something about login in just plain and black writing along with other things but then the screen goes blank again.  I was wondering if you guys had any more advice for me.  I really hope I can get Ubuntu to work on here.  Thanks a lot!

Tim

---

### Post by tuxcantfly on 2007-09-10
> **celtic426 said:**
> Hey guys,

I have a fairly new HP dv6000 series laptop.  I know that these hp's are pretty bad with linux and can be difficult to install.  That's pretty much what I need help with.  First of all, I have tried about 10 different live cd's of different distros and I have had a problem with all of them.  Most of them just crash or blank out at some point.  Now I am using Wubi to try to install Ubuntu onto my Windows Vista Machine (I want to keep Vista).  The Wubi set up goes well and everyone works until the Ubuntu loading screen comes up.  It completes the load then after more writing comes up, and then the screen goes blank.  But it doesn't just go black, it's like the actual plasma or whatever inside the screen goes away like the computer is shut down.  But the computer is still on.  I have read some tutorials and help online and I have tried adding things like "no alcid" and those 5 things like that to the boot string.  This has not worked.  Acutally when I add those things to the boot string I think the process gets a little further and something says something about login in just plain and black writing along with other things but then the screen goes blank again.  I was wondering if you guys had any more advice for me.  I really hope I can get Ubuntu to work on here.  Thanks a lot!

Tim

Do you have the necessary drivers for your graphics card? Get to a command line using Ctrl-Alt-F2, login, then follow the commands in the documents below to install the drivers:

[https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia](https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia) if you have an nvidia card

[https://help.ubuntu.com/community/BinaryDriverHowto/ATI](https://help.ubuntu.com/community/BinaryDriverHowto/ATI) if you have an ati card

---

### Post by celtic426 on 2007-09-10
thank you, i will try that and get back to u soon.

---

### Post by backstrap on 2007-09-10
if you are still having problems, i have an HP DV6105 and it took me forever to figure out how to install ubuntu, gentoo, or any other distro. for ubuntu it worked with 1 tweak.


at the boot prompt from the live DvD it will ask you if you want to start or install ubuntu. press f6 (or whichever f-key gets you the other options listed at the bottom of screen) . it should provide you with the boot parameters for the kernel. at the very end of all of it you should see something like.. 
<blah blah blah> splash quiet -- 
add the following parameter to it.

<blah blah blah> splash quiet noapic --

and you will boot 100%  with no problems.

onece you get ubuntu installed edit the grub menu file.

sudo nano -w /boot/grub/menu.lst (i think it is ,lst)
and at the bottom of the file you will see the kernel parameters again. on the default boot kernel add noapic to the same like you did for the cd and you will be set.


dont forget to do that for every kernel update you do.

---

### Post by celtic426 on 2007-09-11
(1) tuxcantfly: from that nvidia driver install site, i cant really find how to acutally do it.  the closest i find is this but im not really sure what it means:

"As of Ubuntu 7.04 (Feisty Fawn) the recommended way to install the binary drivers is to use System &#8594; Administration &#8594; Restricted Devices Manager. "

I cant get to the desktop so how would i do that?

(2) backstrap: I've been trying that splash quiet noapic thing but its not working.  i made sure i was typing it in correctly.  i also got some information about this from this useful website: [https://wiki.ubuntu.com/hp_dv6000_series_(dv6116eu)]("https://wiki.ubuntu.com/hp_dv6000_series_(dv6116eu)")

maybe you can see something there?

(3) Doing some googling I found that this worked for someone: use display device DFP in /etc/x11/xorg.conf

Now this fixes an error that happens when llinux defaults to the CRT (monitor).  i think thats what my computer is trying to do cause that makes sense.  My screen goes totally empty like the plasma goes away which could definitely mean that it is deafulting to the CRT.  but i didnt fully understand how to add that option and where to put that in.  so if someone could tell me exactly how to do that, that would be great.  

thanks  a lot.

---

### Post by celtic426 on 2007-09-12
can someone help me please?  i just need to figure out how to get linux to recognize my laptop screen and NOT try to resort to CRT.  Thanks! :)

---

### Post by bbl232 on 2007-11-01
I had the same problem with my HP Pavilion dv6307ca notebook, what you need to do is insert the live cd distro and when the boot menu pops up press F6 and you will see a command line, at the end of this line type;

boot:live vga=771 noapic nolapic


this should fix your problem, you will also probably have a problem with your broadcom wireless adaptor, during the boot be sure to be connected via a cable to your router or server or whatever so that you can enable the restricted driver.


ANY MORE PROBLEMS, EMAIL ME via my site :

[http://basiccomputerhelp.cjb.net/](http://basiccomputerhelp.cjb.net/)

---

