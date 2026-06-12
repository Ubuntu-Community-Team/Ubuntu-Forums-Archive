---
title: "Graphic Driver Installation Question"
date: 2006-11-08
forum: Installation &amp; Upgrades
---

### Post by Deronius on 2006-11-08
First I want to say I'm a very new Linux user so please be gentle with me ;) 

On my system I have an older GeForce2 card that has served me well in a couple of other rigs.  I would like to use the nvidia drivers but if I follow the instructions of downloading and then changing nv to nvidia it errors out and I can't reboot to desktop until I restore the oringinal setting.  

So the question...

Why does every guide say to change nv to nvidia?  It doesn't seem to be working for me.  I don't expect it but if someone could hold my hand a bit and walk me through getting the nvidia driver correctly I'd really appreciate it.  My goal is to be able to use Open GL.

](*,)

---

### Post by Ay Deverrick on 2006-11-08
You need the nvidia drivers afore you can replace nv with nvidia.

As to getting them and installing them, there is an excellent howto here:

[http://doc.gwos.org/index.php/Latest_Nvidia_Dapper](http://doc.gwos.org/index.php/Latest_Nvidia_Dapper)

or here if Edgy

[http://doc.gwos.org/index.php/Latest_Nvidia_Edgy](http://doc.gwos.org/index.php/Latest_Nvidia_Edgy)

---

### Post by Deronius on 2006-11-08
Ah thank you very much.  It looks like I have a card that the legacy driver will work with which from the sounds of it will be easy to install.

Thanks for the help.

---

### Post by Deronius on 2006-11-08
Whelp I'm still having some problems but I'm narrowing them down.   I'm fairly certain that I need the nvidia legacy drivers.  However, when I try to get them I receive this message:

Package nvidia-glx-legacy is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package nvidia-glx-legacy has no installation candidate

I know this might seem dumb, but when I was reading the instructions I thought perhaps the drivers would be unpacked somewhere.  Do I need to get the drivers from Nvidia first?  (I hope there's not laughter after that)

:D

---

### Post by Deronius on 2006-11-09
Sorry to bump this but I just wanted to make one more attempt to see if anyone knew how to get the nvidia legacy drivers.

I've been trying to follow the instructions listed here:

[http://doc.gwos.org/index.php/Latest_Nvidia_Edgy](http://doc.gwos.org/index.php/Latest_Nvidia_Edgy)

They're very detailed but when I try to use the command:

sudo apt-get install nvidia-glx-legacy nvidia-xconfig nvidia-settings

I get the message:

Package nvidia-glx-legacy is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package nvidia-glx-legacy has no installation candidate

I'm almost positive that I need the legacy drivers for my GeForce2 TI so if anyone could help me find them I would be very thankful.

---

### Post by bscardin on 2006-11-18
I am not usually on for "me too" posts, but me too :).  I recently put edgy on an old PC and for the life of me I cannot get my legacy nvidia drivers installed.  I get the same message in the post above.  I have searched and searched and most posts just lead to very similar HowTo articles that make it look so easy but do not address the simple problem of not finding the package.  Any help would be appreciated.  Thanks.

---

### Post by bscardin on 2006-11-19
Well, I tried several things and I finally got the install to work.  In case anyone is still interested I think what finally did it was I ran 'sudo aptitude update'  After that apt-get found the nvidia-glx-legacy and things are going better now.

---

### Post by prescor on 2006-11-22
I'll throw in a "me too" too!  I'm trying to get the Beryl stuff working and have an Nvidia Quadro2 Pro in my Dell and get the same message trying to install the legacy driver package.

Where'd it go??

---

### Post by oblib on 2006-11-23
First instruction in method 1:
Make sure you have both the Universe and Multiverse repositories enabled.

Have you done this? I think he should have included restricted in there too. If it can't find nvidia-glx-legacy, that means the repositories aren't there. You should have a line similar to this in your /etc/apt/sources.list:
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) edgy universe main restricted multiverse

---

### Post by cantormath on 2006-11-23
> **Deronius said:**
> First I want to say I'm a very new Linux user so please be gentle with me ;) 

On my system I have an older GeForce2 card that has served me well in a couple of other rigs.  I would like to use the nvidia drivers but if I follow the instructions of downloading and then changing nv to nvidia it errors out and I can't reboot to desktop until I restore the oringinal setting.  

So the question...

Why does every guide say to change nv to nvidia?  It doesn't seem to be working for me.  I don't expect it but if someone could hold my hand a bit and walk me through getting the nvidia driver correctly I'd really appreciate it.  My goal is to be able to use Open GL.

](*,)
since you are new,
I would suggest using Automatix2 at [getautomatix.com]("http://getautomatix.com/wiki/index.php?title=Installation&Itemid=38#Installing_on_.28K.2CX.29Ubuntu_6.10_i386_.28Edgy.29")
Read the directions on how to install, and ask us questions if you have a problem.

The program will install the nvidia drivers for you, and many other codecs etc, if you choose.

---

### Post by peebly on 2006-11-23
> **Deronius said:**
> First I want to say I'm a very new Linux user so please be gentle with me ;) 

On my system I have an older GeForce2 card that has served me well in a couple of other rigs.  I would like to use the nvidia drivers but if I follow the instructions of downloading and then changing nv to nvidia it errors out and I can't reboot to desktop until I restore the oringinal setting.  

So the question...

Why does every guide say to change nv to nvidia?  It doesn't seem to be working for me.  I don't expect it but if someone could hold my hand a bit and walk me through getting the nvidia driver correctly I'd really appreciate it.  My goal is to be able to use Open GL.

](*,)

Hello

I find the following method one of the best ways to install nvidia drivers.

[http://www.ubuntuforums.org/showthread.php?t=301499](http://www.ubuntuforums.org/showthread.php?t=301499)

Click on the link at the bottom of the post and use the ENVY script.

---

