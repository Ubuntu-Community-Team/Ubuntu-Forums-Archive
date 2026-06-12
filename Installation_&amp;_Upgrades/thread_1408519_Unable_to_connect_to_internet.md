---
title: "Unable to connect to internet"
date: 2010-02-16
forum: Installation &amp; Upgrades
---

### Post by papajoe41 on 2010-02-16
Hello. This is my first post as I just downloaded Ubuntu yesterday, and I have to say, I was surprised at how easy Wubi made it for me to complete the download.
   
  However, I cannot get connected to the internet. I have checked out a number of online instructions for this, and I found one instruction that said to “Open System>Administration>Networking. 
   
  I have tried System>Administration but there is no “Networking,” or at least none that I can see.. I have found Network Tools, but that doesn’t work.
   
  Another instruction that I found instructed to click the Network Manager in the Taskbar. To the top right side of my screen, the first symbol says “No Network Connection.” I have played around with that, but no luck. 
   
  As you have probably gathered, I do not have much computer experience. However, I have cable and my other computer is connected to XP wireless. 
   
  From some of the internet comments that I have seen, this seems to be a fairly common problem. I am about ready to give up on Linux, but I was wondering if anyone has any suggestions.
   
  [FONT=&quot]Thanks[/FONT]

---

### Post by dabl on 2010-02-16
First, did you try booting and running the ubuntu Live CD?  Did it have network/Internet connectivity?  Second, if you open a terminal this command will show your ethernet chip make and model (among other devices):

```
lspci -v
```

Third, also in the terminal window, this command will show the status of an ethernet connection, if it was already set up:

```
sudo ifconfig
```

If can post back with that kind of information, help may be possible.

---

### Post by papajoe41 on 2010-02-16
Thanks for your help dabl. I don't have the CD as I just downloaded Ubuntu on the internet. Would I order that CD from Ubuntu?

As I have no idea how to open a terminal, ethernet chips, or much of anything else, I guess that it is probably better for me just to forget about the whole idea. 

I appreciate the time you spent replying to my query.

Thanks.

---

### Post by dabl on 2010-02-17
I assume you are working from a Windows system, so you obviously can work a keyboard and mouse.  If you're still interested, and your PC has a CD ROM drive and burning software, then you can download a Ubuntu ISO image file and burn it to a CD.  That CD then becomes one that you can boot and run the Linux operating system from.  If you like it, and things like networking work satisfactorily (which it normally does), then you can choose to install it on your computer.  There is a version of Ubuntu that uses the "K" Desktop Environment (KDE), called Kubuntu.  Here are some pointers regarding burning the ISO image to a CD, that were written for Kubuntu users:

[http://kubuntuforums.net/forums/index.php?topic=3106270.0](http://kubuntuforums.net/forums/index.php?topic=3106270.0)

[http://kubuntuforums.net/forums/index.php?topic=3104464.0](http://kubuntuforums.net/forums/index.php?topic=3104464.0)

---

