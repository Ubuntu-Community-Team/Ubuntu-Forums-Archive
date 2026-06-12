---
title: "Ubuntu 7.04 Install Trouble...Cannot Start X Server"
date: 2007-07-13
forum: Installation &amp; Upgrades
---

### Post by vwaj on 2007-07-13
Okay, so I'm a bit new with Linux, but here goes:

I just got a new laptop.  It's a Dell Latitude D830 with a 256 MB NVIDIA Quadro NVS 140M video card.  The screen's aspect ratio is 5:8 (standard widescreen, I think).

I've been trying to get Ubuntu 7.04 going on it.  The standard install was giving me some problems, so I used the text install, which seemed to work just fine, for a while.  However, once I rebooted after installing, I saw a blue screen with an error message that read,

"Failed to start the X server (your graphical interface).  It is likely that it is not set up correctly.  Would you like to view the X server output to diagnose the problem?"

Upon pressing "yes," I saw a bit of text which ended with the following:

"(EE) NV(0): No display devices found
(EE) Screen(s) found, but none have a usable configuration.

Fatal server error: no screens found"

So the graphical interface would not load.  After scratching my head for a bit, I thought maybe my graphics card was not supported by the default "nv" drivers that X was using.  So I got the nVidia drivers from
[http://us.download.nvidia.com/XFree86/Linux-x86/100.14.11/NVIDIA-Linux-x86-100.14.11-pkg1.run](http://us.download.nvidia.com/XFree86/Linux-x86/100.14.11/NVIDIA-Linux-x86-100.14.11-pkg1.run)
and installed them according to the instructions on
[http://www.albertomilone.com/latest_nvidia_udsf_feisty.html](http://www.albertomilone.com/latest_nvidia_udsf_feisty.html) (Method 2).

After doing that, X Server still would not start.  I got to a similar screen as before, but the error message was a little different:

"(EE) Failed to load module "nvidia" (module does not exist, 0)
(EE) No drivers available.

Fatal server error: no screens found"


I'm still not sure whether the initial issue was actually caused by a lack of support for my video card or something else.  I'd really really really appreciate if someone could help me with this!

---

### Post by Pumalite on 2007-07-13
The problem is that you cannot install Nvidia propietary driver without having this installed: build-essential, make, automake, autoconf, latest gcc, kernel-headers matching your kernel(the driver needs them to compile the kernel) I would first try: sudo dpkg-reconfigure xserver-xorg. Once IN the system I would worry about installing the driver.

---

### Post by vwaj on 2007-07-13
I actually had tried using dpkg-reconfigure xserver-xorg, but to no avail.  I stuck with the default settings when I tried -- "nv" driver, "nVidia Corporation NVIDIA Default Card" as the video card identifier, "PCI:1:0:0" as the video card bus identifier, "Generic Monitor" as the monitor, etc.  I still get the same error message -- no screens found.  Is it possible the video card bus identifier is wrong?  Is there any way to tell what the appropriate identifier is?  Maybe the operating system is confusing my onboard graphics card with the dedicated one...I don't know.

Any other suggestions?  I'm still pretty stuck, though I'll keep playing around with it.

---

### Post by merlinus on 2007-07-13
Did you try selecting "vesa" from the options in  dpkg-reconfigure xserver-xorg?

-merlin

---

### Post by AlexenderReez on 2007-07-13
> **vwaj said:**
> I actually had tried using dpkg-reconfigure xserver-xorg, but to no avail.  I stuck with the default settings when I tried -- "nv" driver, "nVidia Corporation NVIDIA Default Card" as the video card identifier, "PCI:1:0:0" as the video card bus identifier, "Generic Monitor" as the monitor, etc.  I still get the same error message -- no screens found.  Is it possible the video card bus identifier is wrong?  Is there any way to tell what the appropriate identifier is?  Maybe the operating system is confusing my onboard graphics card with the dedicated one...I don't know.

Any other suggestions?  I'm still pretty stuck, though I'll keep playing around with it.

instead of using dpkg-reconfigure xserver-xorg ...better if you reboot in live cd then
> gksudo gedit /etc/X11/xorg.conf

copy it to file...save..then paste it...default detection is better than reconfig....i'm using nvidia 7900gs.....and i'm using nvidia-xgl-new ...download restricted modules for kernel....then

> sudo nvidia-xconfig --add-argb-glx-visuals

restart ...and i check

> 
reez@aLeXeNdeRreEz:~$ lspci | grep VGA
01:00.0 VGA compatible controller: nVidia Corporation GeForce 7900 GS (rev a1)
reez@aLeXeNdeRreEz:~$ glxinfo | grep direct
direct rendering: Yes
reez@aLeXeNdeRreEz:~$ X -version

X Window System Version 1.3.0
Release Date: 19 April 2007
X Protocol Version 11, Revision 0, Release 1.3
Build Operating System: Linux Ubuntu
Current Operating System: Linux aLeXeNdeRreEz 2.6.22-8-generic #1 SMP Thu Jul 12 15:59:45 GMT 2007 i686
Build Date: 13 July 2007
        Before reporting problems, check [http://wiki.x.org](http://wiki.x.org)
        to make sure that you have the latest version.
Module Loader present


---

### Post by vwaj on 2007-07-13
OK I tried selecting "vesa" and it worked!  Thanks a lot merlin, and others who offered advice.  I'm still a bit confused though -- what does the "vesa" option mean, and why would it work for this video card?

---

### Post by Pumalite on 2007-07-13
Vesa is a generic driver; 'a jack of all trades' Now you can get your propietary driver if you want. Place it in /home/<username>. Make sure you have everything I told you installed. Then Crtl-Alt-F2> Login with your username and password> sudo /etc/init.d/gdm stop> sudo sh /home/<username>/NVIDIA-Linuxxxxx.run>Accept License>Let the driver compile the modules>Let the driver reconfigure your xorg file>Installation Completed> sudo /etc/init.d/gdm start

---

### Post by Zeenomorph on 2007-07-13
I think that I have the same problem, though I don't think that I have the intellectual ability to figure out the advice that was given!

I bought a new laptop, (Asus F5V) and I'd very much like to install Linux on it.  I was talking up a storm to my friends about how great Linux seemed, (I've never used it, only read a little, but I hate Microsoft).  They were there when I was installing it, and saw the error message, and mocked, and still are mocking me!

This is what happened;

I installed (tried to) Linux Ubuntu, everything goes good for a minute or two then;

Failed to start the X server (your graphical interface).
It is likely not set up correctly.                       <---p.s Strange to me that it could be set up wrong...       it's a new laptop!
Would you like to view the X server output to diagnose the problem?       <---- p.s. "Sure"

Then I get this;

X windows system version 7.2.0
Release date: 22 January 2007
X protocol version 11, Revision 0, realease 7.2
(==)log file: "/var/log/xorg.0.log"
(==)using config file "/etc/x11/xorg.cong
(EE) VESA(0): No matching modes
(EE) Screen(s) found, but none have a usable conguration

      Fatal server error:
                   no screens found

This seems to be the problem in this thread.  And advice was given, and the user seemed happy with it, but it might as well have been in Greek to me!  Something about selecting "Vesa".  Who?  What? When? Where? and Why?

I'm sorry, but I'm a complete noob at this.  I've never even seen a working Linux machine.  I love the idea of it.  I'd love to learn more about how to take care of these issues on my own, but for the time being, I'm going to need a helping hand.  And any that you could offer would be greatly appreciated!  

p.s. Baby steps please!

---

### Post by merlinus on 2007-07-13
Give this a try:

When you get the error message, Ctrl-Alt-F1 to get to prompt.

Enter:

sudo dpkg-reconfigure xserver-xorg

Use arrow keys to move between choices; spacebar will select the one you want.

You can probably go with the default for most screens, but select "vesa" for your video driver.

Then:

startx

-merlin

---

### Post by Zeenomorph on 2007-07-13
I thank you for your timely response Mr. Merlin.  

Though I fear that you are not done with me yet.  I followed your advice, but I don't seem to be any closer to the goal of a working computer yet.  

Here's what it says now;

Fatal server error:
no screens found
XIO: fatal IO error 104 (connection reset by peer on x server ":0.0"
after 0 requests (0 known processed) with 0 events remaining.

I beg of your assistance once again!

---

### Post by merlinus on 2007-07-13
OK, let's backtrack for a bit.

Are you trying to run the ubuntu live cd (booting your computer from it)?

If so, when you get to the startup menu, try selecting Safe Video Mode.

If that does not work, you may be better off getting the Alternate Install cd, which is text-based.

Also, are you wanting to dual-boot with windows?  If so, which version?  This is important to know before trying to install ubuntu.

-merlin

---

### Post by Zeenomorph on 2007-07-13
I downloaded the Ubuntu file, and made an image CD.  And I'm booting from that.

I tried safe video mode, and got the same thing.

I have Windows XP SP2 on the computer already.  I didn't want to, but I want to be able to use my computer while I (and by "I", I mean _*you*_) try to figure this out.

I don't know what you mean by a "text based" version.  I only see the one posted.  And that's what I took.

Thank you again.

---

### Post by merlinus on 2007-07-13
Alternate Desktop Install cd:

[http://www.ubuntu.com/getubuntu/download](http://www.ubuntu.com/getubuntu/download)

Tick the box below green Start Download graphic, then click the the graphic to begin the process.

But before doing this -- what make and model of video card does your computer have?

-merlin

---

### Post by Zeenomorph on 2007-07-13
I have a 

[CENTER]ATI Mobility radeon X2300[/CENTER]

---

### Post by merlinus on 2007-07-13
Your problems are related to that video card.  After installing, you can get the correct drivers.

Again, using the Alternate Install cd from the link in my last post is the way to go.  Because it is text-based, you will not have these video problems.

But before attempting to intall ubuntu, clean up your windows installation by deleting temporary files and other unused stuff, backup your i-cannot-live-without-this data, and defrag several times.

Give it a go....

-merlin

---

### Post by Zeenomorph on 2007-07-13
Thank you I will.  It'll take me a LONG time to get that file, so I won't be on here for a while.  I'd just like to thank you again for all of your kind help.

Zeenomorph

---

### Post by Zeenomorph on 2007-07-16
I hope that you're still out there Mr. Merlin!

I have now made a boot disk for the 'alternate text based' version.  
I installed it.  I think it's on my computer, but I can't tell.

Here's the situation now.  I installed it to the point that the disk ejected and the computer rebooted.  It came up as loading Ubuntu.  I was very happy, and then, the same ****!  All that Xserver stuff again.  I typed into the command line the same thing that you told me to do last time.  This time I get this message;

xserver-xorg postinst warning: overwritting possibly-customised configuration file, backup in /etc/X11/xorg.conf.20070715180334

Then i'm at the command line, and I have no idea what you type.

As a further problem, I can't seem to get into windows anymore, so now I'm effectively without a computer until this gets fixed.  I reallly do want to use Linux, I have no desire to use Windows whatsoever, but I must admit that I am becoming frustrated.  I just want to boot an operating system, and use my computer.  

Anyway, if anyone out there in the Ubuntu community can get me through this snag so that I may begin to enjoy this software I'd be eternally grateful.

---

### Post by merlinus on 2007-07-16
> 
xserver-xorg postinst warning: overwritting possibly-customised configuration file, backup in /etc/X11/xorg.conf.20070715180334

Then i'm at the command line, and I have no idea what you type.


```

startx

```

-merlin

---

### Post by Furax- on 2007-07-16
I'd suggest you to read this:

[http://terenzioberni.blogspot.com/2007/06/ubuntu-704-on-asus-z53jr-f3jr.html]("http://terenzioberni.blogspot.com/2007/06/ubuntu-704-on-asus-z53jr-f3jr.html")

In that post there is a quick guide to install the correct drivers for ati mobility radeon X2300 graphic card on Ubuntu. Maybe you'll find it usefull ;)

---

### Post by Zeenomorph on 2007-07-16
I'm sorry to say that that didn't get me anywhere.

Fatal server error:
    no screens found
XIO: fatal IO error (connection reset by peer) on X server ":0.0" after 0 requests (0 known processed with 0 events remaining.

---

### Post by Pumalite on 2007-07-16
Avoid the graphical interface problem installing with 'Alternate CD'. If 256 MB RAM or less>Xubuntu Alternate CD. Get IN the system first, THEN worry about proprietary drivers. Besides that; with your card, you have to install a 'Legacy' driver.

---

### Post by Zeenomorph on 2007-07-16
I'm using the alternate text based CD.  I'll try Legacy and see if that gets me anywhere though.

---

### Post by Zeenomorph on 2007-07-16
I'm in!  I got Linux!  Sweet!  Thank you Ubuntu Community!

---

### Post by ckh on 2007-07-21
I had excact the same problem when I just changed my laptop to HP 6910p
but I just solved this probelem.

steps below:

sudo apt-get update
sudo apt-get dist-upgrade
sudo apt-get install linux-restricted-modules-$(uname -r)
sudo apt-get install xorg-driver-fglrx
sudo depmod -a
sudo aticonfig --initial
sudo aticonfig --overlay-type=Xv
sudo /etc/init.d/gdm restart

(This solution was form [http://terenzioberni.blogspot.com/2007/06/ubuntu-704-on-asus-z53jr-f3jr.html](http://terenzioberni.blogspot.com/2007/06/ubuntu-704-on-asus-z53jr-f3jr.html))


-ckh

---

### Post by foonzy on 2007-08-13
Hey,
I have just installed ubuntu 7.04 on my Asus F3Jr Laptop. I did it form the live dvd and I had the same problem couldnt load up the "startx" So i did what you have done to run the live dvd

sudo apt-get update
sudo apt-get install linux-restricted-modules-$(uname -r)
sudo apt-get install xorg-driver-fglrx
sudo depmod -a
sudo aticonfig --initial
sudo aticonfig --overlay-type=Xv
sudo shutdown -r now

instead of the reboot though to runt he live dvd i just did "startx" there

sudo startx

and it run the live dvd fine. But thats where the problem started for me. I installed it all fine and did all that again to load up the OS for the first time and it runs great...But I cannot use any of the effect for some reason it will not allow me to use the cube or anything. I was wondering if anyone can help me out with this. It would be great help.
Kind Regards
Foonzy

---

### Post by Pumalite on 2007-08-13
I think you should start a new thread in Sub-Forum Desktop Effects and Customization. Better and faster answers.
[http://ubuntuforums.org/forumdisplay.php?f=223](http://ubuntuforums.org/forumdisplay.php?f=223)

---

