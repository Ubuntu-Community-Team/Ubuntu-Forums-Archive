---
title: "No GUI on bootup"
date: 2010-04-11
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by teejay17 on 2010-04-11
Installing Lucid Lynx beta 2 went well except for one thing: when my machine reboots for the first time (I tried installing twice)there is no GUI. Instead, the machine boots into terminal mode; I punch in my user name and password and still there's no GUI. I can update the packages from the terminal, but there is no GUI. 
When I type "startx" I get a sort of terminal error message. 
Anyone know why this might be so? Anyone know how I might fix this? 
Thanks in advance.

---

### Post by ranch hand on 2010-04-11
What is the error message?

How about some information on you box?

---

### Post by teejay17 on 2010-04-11
> **ranch hand said:**
> What is the error message?

How about some information on you box?

[http://www-307.ibm.com/pc/support/site.wss/MIGR-4L4NTP.html#1n2](http://www-307.ibm.com/pc/support/site.wss/MIGR-4L4NTP.html#1n2)
The laptop is the Series Two, 1161 - 11U.
The error message I get is when I give the command startx is: > Fatal server error: no screens foundAfter that, it also says 
> xinit: No such file or directory (errno 2): unable to connect to X server
xinit: no such process (errno 3): server error
xauth: error in locking authority file /home/tj/.Xauthority

---

### Post by QLee on 2010-04-11
teejay17,

Which iso did you use, live desktop or alternate?
 
If alternate, did you install X? (And incidently, all the rest of the desktop applications that you want on the system?)

Did you try to re-use a "/home" partition from a previously working system?

Instead of us trying to wade through IBM info, please tell us what video interface you have.

I know that is a lot of questions but those things aren't clear from what you have already stated and might be related to what you have described.

---

### Post by teejay17 on 2010-04-11
> **QLee said:**
> teejay17,

Which iso did you use, live desktop or alternate?
 
If alternate, did you install X? (And incidently, all the rest of the desktop applications that you want on the system?)

Did you try to re-use a "/home" partition from a previously working system?

Instead of us trying to wade through IBM info, please tell us what video interface you have.

I know that is a lot of questions but those things aren't clear from what you have already stated and might be related to what you have described.
I used the alternate beta 2 of Ubuntu Lucid Lynx and it was a clean installation. 
I have installed Ubuntu on this machine before, specifically 8.04 and 8.10, and they worked well. There's just something about Lucid Lynx that's not jiving. 
The interface for this model is LCD 13.3" and I'm pretty sure the resolution is maxed out at 800X600.

---

### Post by QLee on 2010-04-11
Well, I did wade around in big blue's info and found this:

Product: ThinkPad i Series 1200 1161-11U 

Original description: Celeron 550MHz (128KB), 32MB RAM, 5.0GB HDD, 12.1 SVGA(800x600) HPA LCD, 24x-10x CD-ROM, Modem, NiMH battery, WinMe

Does that still describe your system, still only 32MB RAM?

---

### Post by teejay17 on 2010-04-11
> **QLee said:**
> Well, I did wade around in big blue's info and found this:

Product: ThinkPad i Series 1200 1161-11U 

Original description: Celeron 550MHz (128KB), 32MB RAM, 5.0GB HDD, 12.1 SVGA(800x600) HPA LCD, 24x-10x CD-ROM, Modem, NiMH battery, WinMe

Does that still describe your system, still only 32MB RAM?
Yes, that's my system, but it has 128 mb of ram. And yep, I made a mistake, it is a SVGA(800x600) HPA LCD monitor.

---

### Post by ranch hand on 2010-04-11
128MB ram is awfully small.

Did you run;
```

sudo dpkg --configure -a

```
?
If not I would try that.

If so I would try;
```

sudo dpkg-reconfigure -a

```

---

### Post by teejay17 on 2010-04-11
> **ranch hand said:**
> 128MB ram is awfully small.

Did you run;
```

sudo dpkg --configure -a

```?
If not I would try that.

If so I would try;
```

sudo dpkg-reconfigure -a

```
Yeah, it is awfully small. What I want to do is install Ubuntu as the base system, then install Lubuntu so it will run quicker.  I will only attempt that after I can get X going.

---

### Post by QLee on 2010-04-11
Well teejay17, I don't think I would try to run Lucid with X (especially with a GNOME desktop environment on a system with those low resources. If you even got it to work, it would be very slow and probably not give you an acceptable user experience. You might try one of the forks with a lighter window manager. Someone who has done something similar with a low spec machine might post here if we wait long enough or, after 24 hours or so, bump this.

---

### Post by QLee on 2010-04-11
> **teejay17 said:**
> Yeah, it is awfully small. What I want to do is install Ubuntu as the base system, then install Lubuntu so it will run quicker.  I will only attempt that after I can get X going.

If I was going to try that I think I would download the Lubuntu beta and try an install from it.

---

### Post by ranch hand on 2010-04-11
I have Lubuntu installed on my system.

I think you are putting the cart in front of the horse here.  Check this;

[https://wiki.ubuntu.com/Lubuntu#Intended%20Audience](https://wiki.ubuntu.com/Lubuntu#Intended%20Audience)

This is a pretty nice OS.

[https://wiki.ubuntu.com/Lubuntu#Download%20Lubuntu](https://wiki.ubuntu.com/Lubuntu#Download%20Lubuntu)

Will get you a disk and instructions on adding the ppa to update the thing properly.  Give it a whack.

---

### Post by teejay17 on 2010-04-11
> **ranch hand said:**
> I have Lubuntu installed on my system.

I think you are putting the cart in front of the horse here.  Check this;

[https://wiki.ubuntu.com/Lubuntu#Intended%20Audience]("https://wiki.ubuntu.com/Lubuntu#Intended%20Audience")

This is a pretty nice OS.

[https://wiki.ubuntu.com/Lubuntu#Download%20Lubuntu](https://wiki.ubuntu.com/Lubuntu#Download%20Lubuntu)

Will get you a disk and instructions on adding the ppa to update the thing properly.  Give it a whack.
Thanks. I will check this out. Right now I'm doing _sudo dpkg-reconfigure -a_ and will see how it works out.

---

### Post by teejay17 on 2010-04-11
> **teejay17 said:**
> Thanks. I will check this out. Right now I'm doing _sudo dpkg-reconfigure -a_ and will see how it works out.
Still no GUI or startx available.

---

### Post by ranch hand on 2010-04-11
I just do not think you have the horses to pull gnome.  I think the recommended minimum is 256MB ram for 10.04.

---

### Post by cariboo on 2010-04-11
I agree the specs are low, but according to [this]("https://help.ubuntu.com/community/Installation/SystemRequirements"), it should be installable, although it may not run very well.

To the op have you tried:

```
sudo service gdm start
```

at the prompt?

---

### Post by teejay17 on 2010-04-11
> **ranch hand said:**
> I just do not think you have the horses to pull gnome.  I think the recommended minimum is 256MB ram for 10.04.
What if I install LXDE?
But at the same time, I think there's something larger at issue because yesterday I installed lubuntu-desktop after I installed Ubuntu and I still had no gui upon boot-up. 
I've since reinstalled so there's no issue of corruption.
Could it be a startup manager thing? Or something related to grub?

---

### Post by ranch hand on 2010-04-11
If you do not have enough ram it will not matter what else you put on it.  That will just make it worse.

I would try the Lubuntu install to see if it works.

If it doesn't I would get a minimal or net install disk and try that using either the Lxde or Gnome Desktop.  I would go with the Lxde first as it is a lot smaller.  The Gnome Desk top is a lot smaller than the Ubuntu Desktop as it does not pull in as much stuff but I am not sure you have the ram for gnome.

---

### Post by teejay17 on 2010-04-11
Gnome on older versions of Ubuntu worked on this system, so something makes me think that something has changed in the last year or so. For example, 8.04 worked no problem, but 9.10 and 10.04 does not--instead they boot to the command line. 
What has changed in the boot-up sequence during this time, and is this something that can be changed?

---

### Post by ranch hand on 2010-04-11
You are getting out of my depth but one thing that has changed across the board is the size of the kernel.

I do not think that it has to do with the boot sequence.  I think it has to do with what it takes to power the system.  There is, for instance, an awful lot of difference between 8.04 and 10.04.

10.04 is just a lot faster and more powerful.  This takes a toll on ram.

---

### Post by teejay17 on 2010-04-11
> **ranch hand said:**
> You are getting out of my depth but one thing that has changed across the board is the size of the kernel.

I do not think that it has to do with the boot sequence.  I think it has to do with what it takes to power the system.  There is, for instance, an awful lot of difference between 8.04 and 10.04.

10.04 is just a lot faster and more powerful.  This takes a toll on ram.
'Tis a very good point.

---

### Post by QLee on 2010-04-12
Is this the same system?

[http://ubuntuforums.org/showthread.php?t=1452651](http://ubuntuforums.org/showthread.php?t=1452651)

---

### Post by teejay17 on 2010-04-12
> **QLee said:**
> Is this the same system?

[http://ubuntuforums.org/showthread.php?t=1452651](http://ubuntuforums.org/showthread.php?t=1452651)
No, it is my other test machine, this one being a ThinkPad T41, with 30 gig hard drive, 1 gig of ram, and a Celeron Processor.

---

### Post by QLee on 2010-04-12
> **teejay17 said:**
> No, it is my other test machine, this one being a ThinkPad T41, with 30 gig hard drive, 1 gig of ram, and a Celeron Processor.

OK, so we have learned how it can be important to give some detail with a trouble report, eh?

Please don't make us drag everything about your system out with questions, you will get a good answer faster if people have some idea of what you are working with.

---

### Post by teejay17 on 2010-04-12
> **QLee said:**
> OK, so we have learned how it can be important to give some detail with a trouble report, eh?

Please don't make us drag everything about your system out with questions, you will get a good answer faster if people have some idea of what you are working with.
Gotcha.

---

