---
title: "A few problems"
date: 2009-11-18
forum: Installation &amp; Upgrades
---

### Post by Ganjafreak on 2009-11-18
I have a few problems with my Ubuntu 9.04 It says there is something wrong with my nvidia server settings when i click it says to run in terminal something sudo nvidia-xconfig

Does anyone know how to help me I did do this and this is the results I got for it


ganjafreak@ganjafreak-desktop:~$ sudo nvidia-xconfig

Using X configuration file: "/etc/X11/xorg.conf".
Backed up file '/etc/X11/xorg.conf' as '/etc/X11/xorg.conf.backup'
New X configuration file written to '/etc/X11/xorg.conf'

ganjafreak@ganjafreak-desktop:~$ ^C
ganjafreak@ganjafreak-desktop:~$ 



I don't know what the problem is.?

---

### Post by realzippy on 2009-11-18
> **Ganjafreak said:**
> I have a few problems with my Ubuntu 9.04 It says there is something wrong with my nvidia server settings when i click it says to run in terminal something sudo nvidia-xconfig

Does anyone know how to help me I did do this and this is the results I got for it


ganjafreak@ganjafreak-desktop:~$ sudo nvidia-xconfig

Using X configuration file: "/etc/X11/xorg.conf".
Backed up file '/etc/X11/xorg.conf' as '/etc/X11/xorg.conf.backup'
New X configuration file written to '/etc/X11/xorg.conf'

ganjafreak@ganjafreak-desktop:~$ ^C
ganjafreak@ganjafreak-desktop:~$ 



I don't know what the problem is.?

After nvidia-xconfig you have to log out and in (restart X)
to load the new xorg.conf file ....

---

### Post by Ganjafreak on 2009-11-18
You mean log out my user account and log back in

---

### Post by realzippy on 2009-11-18
Yep,e.g. ...

Edit:
In fact I cannot know what your problem is,..until you specify it...  ;-)
also *might* be good to know:
nvidia-driver version
graphic card
laptop?

---

### Post by Ganjafreak on 2009-11-18
Im on a desktop and how do I pull up that information I searched on google a fix I installed something about nvidia and edit the xconf file but you see it still didn't work


What is the terminal command to pull all that information you need up.?

---

### Post by realzippy on 2009-11-18
**man xorg**

edit:

what information?what xorg changes you made?And why?

---

### Post by Ganjafreak on 2009-11-18
I google'd for the problem to why I couldn't check my nvidia card settings and to turn my 3d graphics and **** on it made me installsomething that had nvidia in it and edit the xorg if you can tell me how to pull the xorg  you can tell what I added.

And here



Xorg(1)                                                                Xorg(1)

NAME
       Xorg - X11R7 X server

SYNOPSIS
       Xorg [:display] [option ...]

DESCRIPTION
       Xorg  is a full featured X server that was originally designed for UNIX
       and UNIX-like operating systems running on Intel x86 hardware.  It  now
       runs on a wider range of hardware and OS platforms.

       This  work  was  derived  by  the  X.Org  Foundation  from  the XFree86
       Project's XFree86 4.4rc2 release.  The XFree86 release  was  originally
       derived from X386 1.2 by Thomas Roell which was contributed to X11R5 by
       Snitily Graphics Consulting Service.

PLATFORMS
       Xorg operates under a wide range  of  operating  systems  and  hardware
       platforms.   The  Intel x86 (IA32) architecture is the most widely sup&#8208;
       ported hardware platform.   Other  hardware  platforms  include  Compaq
       Alpha, Intel IA64, AMD64, SPARC and PowerPC.  The most widely supported
 Manual page Xorg(1) line 1

---

### Post by realzippy on 2009-11-18
sorry, *man xorg* was all you need.you asked for it...
please type:

**gksudo nvidia-settings**

what happens?(what does it say?)

---

### Post by Ganjafreak on 2009-11-18
ganjafreak@ganjafreak-desktop:~$ gksudo nvidia-settings
\/home/ganjafreak/.themes/diehard/gtk-2.0/gtkrc:53: Clearlooks configuration option "sunkenmenu" is not supported and will be ignored.


And it also popped up the server window to edit etc..


Now I have another question When I adjusted my scren resolution my monitor said input signal out of range please change How do I change it when I cant see nothing...?


Um, I have a thing called screenlets with info panel on it and we'll and when I click to edit it's settings the editing window pops up real huge the size of my flatscren(im on now cause moonitor said the above) and we'll I can't go to the bottom to click close or apply I just hit tab and enter How do I get that to go back down....? and I can't adjust it cause When I clck the corner to drag it don't go no where,

---

### Post by Ganjafreak on 2009-11-18
Now when I click display a pop-up asks me if I should start with nvidia or default and when i click yes to nvidia it pops up my control panel for it

thanks for helping me with that problem.

---

### Post by Ganjafreak on 2009-11-18
I just tryed to change my visual effects to the best one and it says effects could not be enabled.?

Why is that I have my nvidia stuff working now and it says on the hardware drivers the one that they recommend is active anit that strange in the past I use there recommended one and I could change the effects right afterwards what is happening lol.

---

### Post by realzippy on 2009-11-18
run again :

**gksudo nvidia-settings**

change something if need,but** hit** (important!!) that "save to X configuration file" button.
Then restart X server,means again to log out an in.Then try again starting desktop effects.

---

### Post by Ganjafreak on 2009-11-18
Okay I did restart the computer and the nvidia settings are now working everything is starting to work like it was I just need to get all my stuff back it crashed on me last night..

Um, I didn't know when you first install ubuntu after you have installed everything you have to restart. lol.

---

### Post by Ganjafreak on 2009-11-19
I have another question,

When I am on either my flatscreen or my monitor and I open my infopanel screenlet it goes fullscreen and there is no way to minimize it cause when I click the edges to drag it to adjust it it don't move. And  I can't see the "Apply" or "Cancel" buttons I have to tab down to it or hit alt+t Can anyone tell me how to fix this.???

So far it's only on that one applet.

---

### Post by realzippy on 2009-11-19
Maybe you better start a new thread.The problem should be seen in the thread title....something like:
*"Strange screenlet behaviour with TwinView.."*

Cannot help you,not using screenlets.Used to test them,but did not like it,and remember also having problems with screenlets and compiz...

---

