---
title: "Failed To Start the X Server...I've tried everything"
date: 2007-08-17
forum: Installation &amp; Upgrades
---

### Post by zachmorelikezack on 2007-08-17
I cannot get rid of this error.

First I tried installing the normal version of Feisty, which wouldn't let me get past the first part because of the error.  Then I installed the alternate install and it installed perfectly, but when I rebooted, I got that error before I could do anything.

Failed To Start The X Server (Your Graphical Interface) 

I click No and I've tried so many things.

I've tried the apt-get update and it just comes up with a big list of things that weren't updated because I'm not connected to the internet.

I tried switching the drive to VESA, vesa, ati, radeon, and to no avail.  I have an ATI Radeon x1400 graphics card, which is the root of the problem.

Also, how do I get connected to the internet so I can get the ATI fix?

[http://ubuntuforums.org/showthread.php?t=414194](http://ubuntuforums.org/showthread.php?t=414194)

That is the one that I'm referring to.

I've tried editing the /etc/network/interfaces file with my IP, but it still doesn't work.  I plugged in my ethernet cable to my laptop and it doesn't connect to the internet like that either.

Thanks for your help,
Zack

---

### Post by zachmorelikezack on 2007-08-17
Sorry to bump this, but I really want to get it working, I've been trying for days and I'm really frustrated.

---

### Post by dabl on 2007-08-17
In text mode (which apparently is all you have), enter > startx and then tell us what the error message says.

---

### Post by zachmorelikezack on 2007-08-17
Thanks for the reply.

It says:

> 
(EE) No devices detected.

Fatal Server Error:
no screens found
X10:  fatal IO error 104 (Connection reset by peer) on X server ":0 . 0"
after 0 requests (0 known processed) with 0 events remaining.

xauth: error in locking authority file /home/zack/.Xauthority


Thanks!

---

### Post by dabl on 2007-08-17
It appears you are without a functioning video display.  Have you attempted to configure an xorg.conf file with the dpkg-reconfigure xserver-xorg script?

If not, do this:

```
sudo dpkg-reconfigure xserver-xorg
```

This starts the X server configuration script. On the first screen, answer "NO" to the autodetect question, and on the second screen choose "VESA" as your display type.  Then you can accept the defaults until you get to the "monitor" section. On that screen, put an "x" only in one resolution that you can comfortably use, like 1024 x 768, or if it is a small display maybe 800 x 600.  Then enter refresh rates appropriate for your LCD or CRT monitor.  When completed, it will dump you back to the text prompt. At that point you can enter

```
startx
``` 

and you should get a reasonable GUI, in which to continue your excellent adventure.

Now you can use the Adept Manager to install Firefox, if you wish, and any other packages that you are in urgent need of.

---

### Post by zachmorelikezack on 2007-08-17
Yes, I have changed the display to Vesa many times, and I've tried a few others as well.

It seems to work for everyone else but it doesn't work for me.

I typed in startx again and this time the error was a bit different.

It says Backtrace: and then there is a list of items 0-5 with various paths.  If you need to see those, I can type them in, but it's just a bunch of numbers and x's and things of the sort.

> 
fatal server error:
Caught Signal 11. Server Aborting

X10: fatal IO error 104 (Connection reset by peer) on X server ":0 . 0"
after 0 requests (0 known processed) with 0 events remaining.

xauth: error in locking authority file /home/zack/.Xauthority


---

### Post by dabl on 2007-08-17
Hmmm.  Well, I dunno -- there's something seriously wrong, and I agree that Radeon card is most likely the culprit.  I assume you've tried the fglrx driver? Did you run the Live CD for awhile on this same hardware -- did it seem pretty stable?  Using the Alternate Install CD, did you try installing it as a VESA display in the first place (as opposed to changing it later)?

That's about all I can think of to try.  I personally gave up on an ATI card -- I "fixed" it with my pocketbook!  :)

---

### Post by zachmorelikezack on 2007-08-17
Ugh, that sucks.

The Live CD (I assume that's the one other than the alternate install) wouldn't even install because of this problem.

And I installed it as VESA to begin with using he alternate.

I haven't tried the fglrx driver, what is that?  I don't see it on the list with vesa and the others.

There is a fix that I found for ATI drivers, but I can't get on the internet.  Any idea how I can do that without being able to actually load the display?

Thanks,
Zack

---

### Post by Herman on 2007-08-17
Hello zachmorelikezack and dabl,
zachmorelikezack, I don't have the same ATI card as you do, but I do have ATI 9200 cards in two of my machines, I haven't had any problem with those in Ubuntu a long time.
I was wondering why you can't even get it going with the vesa driver and I remember having problems with my new AL2016W Acer monitor. Every time I install Ubuntu (or Debian), with that monitor I get the wrong screen resolutions (mode lines) in /etc/X11/xorg.conf, and editing that file with suitable mode lines fixes the problem. Before you give up you could try what I do, it might work if your problem is in any way related.

The following link shows how to mount your rescue your new hard disk install with a Live CD and access a few of the important files like /etc/X11/xorg.conf to edit it, [Mount a Ubuntu ext3 or reiserfs filesystem]("http://users.bigpond.net.au/hermanzone/p10.htm#Mounting_Ubuntu_with_Dapper_Desktop_LiveCD") [COLOR=#666666]

[COLOR=Black] Here is a useful command you should be able to use to find out some important information. Maybe it would help if you post the output from that command here.[/COLOR][/COLOR]```
sudo ddcprobe
``` You could compare the output from that command maybe, with what's in your /etc/X11/xorg.conf and it might get you a little further I hope. 

If you post your new Ubuntu hard disk install's /etc/X11/xorg.conf file here it might help someone to help you. (Not your Ubuntu Live CD's /etc/X11/xorg.conf file :)  ).  Maybe someone who has the same ATI card as you or someone who is an expert with configuring xorg will come along and be able to give you exactly the right advice.
That reminded me of something else; I have heard of someone fixing their hard disk install by copying their LiveCD's /etc/X11/xorg.conf file to their hard disk installation. I'm not sure about that, I can't rememebr if I tested that myself, but I did read that here some time ago. It's an idea. It might work, it's something easy to try anyway. If the LiveCD works you should be able to get the hard disk install to work. :)

Regards, Herman :)

---

### Post by dabl on 2007-08-17
Herman, you da man!

@zachmorelikezack, see if Herman's advice helps you -- the problem could indeed be related to the monitor itself.

If not, search this forum on your Radeon card model, and also on "fglrx".

If you can get any kind of GUI working, even a crappy VESA one, then I would recommend you go to [[COLOR="Magenta"]**this**[/COLOR]](http://albertomilone.com/nvidia_scripts1.html) site and download the Envy script installer. You want the file named "envy_0.9.7-0ubuntu8_all.deb" about halfway down the page.  Just download it to your desktop, then right-click it and "GDebi Install" it. An icon will be placed in your System menu, and you can also run it at any (desperate) time at the CLI text prompt by entering ```
sudo envy -t
```

That little lifesaver has got me back my Nvidia GUI many times!

---

### Post by zachmorelikezack on 2007-08-18
I've been trying to mess around with the display settings, but I really don't know what to do...

I found a fix for the ATI card, but I can't download it because it comes from online.  How do I get connected to the internet?

Thanks,
Zack

---

### Post by cooney on 2007-08-18
I don't know if this will help but it got me going after having similar problems with my NVidia card.

I had to comment out the BusID line in my xorg.conf file to get X to start.  I was able to solve the rest from there being able to "see" what I was doing.


> Section "Device"
        Identifier      "Generic Video Card"
        Driver          "nvidia"
#       BusID           "PCI:0:2:0"
        Option          "AddARGBVisuals"        "True"
        Option          "AddARGBGLXVisuals"     "True"
        Option          "NoLogo"        "False"
        Option          "DynamicTwinView" "False" 


Hope this helps,

Bob

---

### Post by Herman on 2007-08-18
>  I found a fix for the ATI card, but I can't download it because it comes from online.  How do I get connected to the internet? Does your LiveCD connect to your internet easily?
You could try booting your Ubuntu Live CD and mounting your hard disk installed Ubuntu and chrooting into it and downloading your fix and installing it.

I'm not too experienced in how to do that, (chrooting), I did that once to install LiLo in a hard disk install for an experiment, chrooting isn't something I do every day. It isn't very difficult, but I'd have to look up how to do it again, unless you already know or someone else who's used to it comes along.

---

### Post by Ub1476 on 2007-08-18
Hi, I have the same ATI card as you, and _had_ exact the same problem.

Alright, let us see if I remember this correctly..

First, boot up, and when you get the x error, choose no to view details. Press Enter to enter the terminal (sometimes you have to press F2 instead). Write your username and password to login. 

Now, you'll have to edit the xorg.conf file:

```
sudo nano /etc/X11/xorg.conf
```

Go down to the monitor section and add this:

```
HorizSync                36-52
VertRefresh              36-60
```

Next you will have to remove all resolutions in the "Screen" section, except for **640x480**.

Press F2, save and exit.

Write this after you have edited xorg.conf:

```
sudo killall gdm

sudo gdm
```

Login, update, enable the ATI restricted driver through System>Administration>Restricted Driver Manager. Do not reboot yet!

Final step! :

Open the terminal and write..  

```
sudo gedit /etc/x11/xorg.conf
```

Go to  the screen section and add the resolutions you removed earlier (if you want to you can only add your highest res).

This works fine on a new clean install too. You don't need to use the alternative CD, just follow the same instructions. Ubuntu will install/use the modified xorg.conf file instead of the default one. Note that the final steps (update and install ati driver etc) you do after you have installed.

Hope that helps:popcorn:

---

### Post by zachmorelikezack on 2007-08-18
> **Ub1476 said:**
> Hi, I have the same ATI card as you, and _had_ exact the same problem.

Alright, let us see if I remember this correctly..

First, boot up, and when you get the x error, choose no to view details. Press Enter to enter the terminal (sometimes you have to press F2 instead). Write your username and password to login. 

Now, you'll have to edit the xorg.conf file:

```
sudo nano /etc/X11/xorg.conf
```

Go down to the monitor section and add this:

```
HorizSync                36-52
VertRefresh              36-60
```

Next you will have to remove all resolutions in the "Screen" section, except for **640x480**.

Press F2, save and exit.

Write this after you have edited xorg.conf:

```
sudo killall gdm

sudo gdm
```

Login, update, enable the ATI restricted driver through System>Administration>Restricted Driver Manager. Do not reboot yet!

Final step! :

Open the terminal and write..  

```
sudo gedit /etc/x11/xorg.conf
```

Go to  the screen section and add the resolutions you removed earlier (if you want to you can only add your highest res).

This works fine on a new clean install too. You don't need to use the alternative CD, just follow the same instructions. Ubuntu will install/use the modified xorg.conf file instead of the default one. Note that the final steps (update and install ati driver etc) you do after you have installed.

Hope that helps:popcorn:

Ah!!!! THANK YOU!!!  

Ok, I'm in Ubuntu right now, and everything is kind of fine.

It won't let me enable the ATI driver though.  I tried to click it and it just loads but then the box isnt checked.  I tried to put in more resolutions and update it and then it just went back to the same old error.

Any idea why it won't let me?

Thanks a ton,

Zack

---

### Post by Ub1476 on 2007-08-19
You have to install all the other updates first.

```
sudo apt-get update

sudo apt-get upgrade
```

---

