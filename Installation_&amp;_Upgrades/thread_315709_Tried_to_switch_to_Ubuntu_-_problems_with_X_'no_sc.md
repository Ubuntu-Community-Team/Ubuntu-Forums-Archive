---
title: "Tried to switch to Ubuntu - problems with X 'no screen' error"
date: 2006-12-09
forum: Installation &amp; Upgrades
---

### Post by Exelsior on 2006-12-09
Ok so here's the deal.

Today I decided that i've had enough of Microsoft. Even after getting Vista RC2 in a vain hope it might be a significant improvement from XP I found it's worse. It won't recognize most of my applications. Those apps that come with it won't work properly. The useless visual effects of the Aero theme are just hogging my ram so when I run ram intensive applications like Games I get decreased performance, so on and so on. Anyway, enough ranting.


_The problem:_

After downloading both a 32 bit and a 64 bit version of ubuntu 6.10 and burning both to different CD-R/W as images (.iso files not just data files) I changed my bios settings to boot from CD-ROM first and started up. All goes fine so far and I am presented with an Interface that has several options, amongst which are 'Install or start' so i decide this is what I want since i'd like to see a live version and decide I like the OS enough to go for it and install it over Vista.

I hit enter and it loads, until the bar at the top reaches about 90-95% at which points the screen has a few lines of strange colour and all the colours of the Ubuntu logo change to some strange greeny reds. Eventually an error message appears that says something along the lines of X Window System finds 'no screen' and tells me to go to [http://wiki.x.org](http://wiki.x.org) which doesn't seem to be much help. This occured exactly the same with 32 and 64 bits.


_My specs:_

64 Bit AMD Athlon 3200+
1536mb of DDR Ram
K8N MSI Motherboard
Radeon X700 Series gfx card
19 inch standard monitor (where does the 'no screen' come from???)
320gb Hard drive


Not sure what more to add. Thanks in advance to any help I get, and maybe with someone's help I can finally get away from the buggy hell that is windows. Having to format my hard drive because of accumulating bugs in windows every month or two due to serious daily computer use isn't something I like :-|

---

### Post by Malakia on 2006-12-09
Most likely the problem is that your graphics card isn't supported by the live cd. Which would explain why x crashes. Try downloading and using one of the alternate cd's and do a text install and see if that helps.

---

### Post by igknighted on 2006-12-09
Try booting into graphics-safe mode.  I used to use an ATI x800 and the live CD never worked for me.  I am using NVIDIA now, but if you install from the live CD and then boot into recovery mode (yeah, its text only) then you can install the proper video drivers and it will work fine.

---

### Post by Exelsior on 2006-12-09
Ok well i've managed to get into the text installer after the GUI crashes, but i'm a complete rookie at TUI or whatever they're called, so I have no idea what to type?

I typed in help but that didn't come up with much useful stuff. Also, the console looks like this:

Ubuntu@ubtuntu > 

or something along those lines. I'm really confused here :S

How do I go about installing video drivers through the text interface?

---

### Post by Exelsior on 2006-12-09
Not sure if this will help but I found others with an x600 who had similar problems, but no solutions yet. Here's a screen of what my error looks like if this can help:

[Screenshot]("http://img144.imageshack.us/img144/2584/ubuntudapperdrakercinstallatio.jpg")

---

### Post by Xiile on 2006-12-09
Hey. As you know I've got the same problem as you. Do you have beta ATi drivers installed in your current WinXP partition? I do, so I'm starting to wonder if that might have an effect...

---

### Post by riven0 on 2006-12-09
Exelsior, have you tried these commands yet?

Log in, first:

I'm not sure if the alternate cd comes with the xserver, so: 

> sudo apt-get install xserver-xorg

> 
sudo apt-get install xserver-xorg-video-ati

> sudo apt-get install ubuntu-desktop

> sudo dpkg-reconfigure xserver-xorg

---

### Post by Exelsior on 2006-12-10
> **Xiile said:**
> Hey. As you know I've got the same problem as you. Do you have beta ATi drivers installed in your current WinXP partition? I do, so I'm starting to wonder if that might have an effect...

Aye, I just remembered that I installed the beta Vista drivers for my card, silly me ](*,) 

Going to try these: 
[Linux Radeon Drivers]("http://ati.amd.com/support/drivers/linux64/linux64-radeon.html")

Let's hope they'll work :)

If it doesn't though, i'll try what you recommended riven0, thanks :)

---

### Post by Exelsior on 2006-12-10
Ok when I use 
sudo apt-get install xserver-xorg-video-ati
it tells me that none installed as I already have the latest version.

When i then type in 
sudo apt-get install ubuntu-desktop
it tells me that it couldn't find the package ubuntu-dekstop.

What's going on here? :-k

---

### Post by beta.tester on 2006-12-10
> **Exelsior said:**
> Ok when I use 
sudo apt-get install xserver-xorg-video-ati
it tells me that none installed as I already have the latest version.

When i then type in 
sudo apt-get install ubuntu-desktop
it tells me that it couldn't find the package ubuntu-dekstop.

What's going on here? :-k

Hi

Not sure what is happening or what you mean precisely :) However *if* you are looking to install kde as well as gnome the command is:

sudo apt-get install kubuntu-desktop

(make sure you select gdm as you windows manager when given the option and not kdm in command above :)

(for xfw try: sudo apt-get install xubuntu-desktop i believe)

Hope this helps (btw kde and xfw are different desktop options that are "rivals" to gnome :)

Pax et bonum (Peace and all good)  john

ps the best way to install nvidia drivers (I have an fx5900 Ultra) is via the automatrix package that includes the nvidia driver as well as other goodies :))

---

### Post by Xiile on 2006-12-10
Hi again, a bit of an update on my side.

I managed to get Ubuntu installed. Sort of. Instead of using the CD, I had to go download the DVD for it and burn that, then install in text mode. After that I tried booting and got the XServer error and entered the console and typed the commands riven0 listed. I went through the xserver reconfiguration thingy and now when I try to boot into Ubuntu nothing displays, although my HDD LED is telling me something is definitely going on. Well, at least I got somewhere for a bit. ](*,)

---

### Post by Xiile on 2006-12-10
I'm up and running! :-D 
Exelsior: Check this thread! [http://www.ubuntuforums.org/showthread.php?t=190133]("http://www.ubuntuforums.org/showthread.php?t=190133")

---

