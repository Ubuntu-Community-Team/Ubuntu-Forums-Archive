---
title: "Wireless mouse not working"
date: 2016-12-17
forum: Installation &amp; Upgrades
---

### Post by CarpCharacin on 2016-12-17
So I am trying to get ubuntu 16.10 installed, but the mouse isn't working.  It is a wireless mouse and the mouse works fine on windows, but when I boot to the USB drive and try to install it, the cursor is just stuck in the corner and it won't move when I move the mouse.  I don't have a wired mouse.

I want to get it installed, but I can't because the mouse just don't work.  How do I fix it?

Ok so I got a wired mouse, but it still dosen't work.  I have tried different usb ports and everything.  What is wrong with it?

So the mouse actually is working, but the cursor just isn't moving.  It stays in the corner of the screen.  How do I fix it?

---

### Post by druillich on 2016-12-18
What Desktop environment are you using? I have similar issue with Lubuntu DE. I think it is a bug with no permanent fixes at the moment. I have found a solution for my mouse issue: Ctrl+Alt+F1 and then Ctrl+Alt+F7.

---

### Post by CarpCharacin on 2016-12-18
It is just regular ubuntu with unity.

---

### Post by RobGoss on 2016-12-18
Hello and welcome, try using another **USB** port or changing the** batteries**, I had issues with wireless mouses when I started using Ubuntu sometime back but after few updates the problems seem to go away not really sure what caused it.

---

### Post by CarpCharacin on 2016-12-18
I did change the usb port and the batteries and when that didn't work, I got a wired mouse and the cursor still stayed in the corner.

---

### Post by RobGoss on 2016-12-18
Take a look at this thread it might have some helpful tips for this issue [http://askubuntu.com/questions/838145/mouse-cursor-stuck-in-top-left-of-screen-but-can-still-move-and-interact-with-in/838155](http://askubuntu.com/questions/838145/mouse-cursor-stuck-in-top-left-of-screen-but-can-still-move-and-interact-with-in/838155)

---

### Post by CarpCharacin on 2016-12-18
The problem is that I can't get it installed without the mouse.  It needs to be installed to install the graphics drivers.

---

### Post by RobGoss on 2016-12-18
Is this the only mouse you have? maybe try another to see if you have the same issue

Here's a few other things you can check

[https://help.ubuntu.com/stable/ubuntu-help/mouse-problem-notmoving.html#wireless-mice](https://help.ubuntu.com/stable/ubuntu-help/mouse-problem-notmoving.html#wireless-mice)

---

### Post by CarpCharacin on 2016-12-18
Like I said, when the wireless mouse didn't work, I got a wired mouse and tried that and it has the same issue.

---

### Post by RobGoss on 2016-12-18
I think in most cases when installing Ubuntu it should recognise your wireless mouse, I was reading that when this happens you may need other software that will be supported

You can read about it in this thread
[https://ubuntuforums.org/showthread.php?t=1828851](https://ubuntuforums.org/showthread.php?t=1828851)

Maybe someone else can shed some light on this issue

---

### Post by CarpCharacin on 2016-12-18
I just tried Ctrl+Alt+F1 and then Ctrl+Alt+F7 and that didn't work.  I just want my mouse to work :(

---

### Post by DuckHook on 2016-12-18
A few thoughts:

First, let's try a shot in the dark. Without the use of a mouse, you will have to <Ctrl>+<Alt>+<t> to bring up a terminal:```
gsettings set org.gnome.settings-daemon.plugins.cursor active false
```You may have to reboot or at least logout/login. Linux is very persnickety about spaces, case, exactitude, so you will have to type carefully. If it doesn't work, set it back to default with```
gsettings set org.gnome.settings-daemon.plugins.cursor active true
```…then

[LIST=1]
[*]Please post output of:```
lsusb >> ~/Desktop/output
``````
xinput --list >> ~/Desktop/output
```The above commands have been structured to pipe their output to a file on your desktop called "output". You can use this syntax to pipe the output to just about anywhere, but you will need to know a little bit about Linux file structure if you want to pipe it to, say, a USB stick. The double greater-than signs ">>" are important. Single signs will just overwrite the file with new data whereas double signs append it.
[*]Please provide as much HW specs as possible. We know nothing about your system or either of your mice.
[*]Why do you need Yaketty (16.10)? It is a non-LTS version, meant for power-users, is therefore less stable, and is unlikely to become much more stable.
[*]Try running Xenial (16.04) in a LiveUSB. If this solves your problem, I recommend replacing your current Yaketty install with Xenial.
[/LIST]

---

### Post by CarpCharacin on 2016-12-18
They are both logitech mice.  One is wireless and one is wired.  The motherboard is an x99 motherboard.  So should I just open the terminal in the live usb?

---

### Post by DuckHook on 2016-12-18
> **CarpCharacin said:**
> They are both logitech mice.  One is wireless and one is wired.  The motherboard is an x99 motherboard.  So should I just open the terminal in the live usb?My bad. I re-read your OP more carefully and see where this is happening to you during install. You can try it, but above command may not work in LiveUSB. It was a shot in the dark anyway.

I would go directly to #3 in my suggestions and try Xenial over Yaketty. See if the LiveUSB works.

Also, how did you download the ISO and what app did you use to burn to LiveUSB?

---

### Post by CarpCharacin on 2016-12-18
But I don't want to use an old version :(.  I downloaded the ISO off of ubuntu.com and I used rufus to burn it.

---

### Post by DuckHook on 2016-12-18
> **CarpCharacin said:**
> But I don't want to use an old version :(.  I downloaded the ISO off of ubuntu.com and I used rufus to burn it.Please read contents of #3 carefully again. Xenial is not "old". It is, in fact, more stable than Yaketty and meant to serve a more general purpose and a broader audience. Most of the power users on this forum (including me) who aren't developers, testers or those with bleeding edge equipment use Xenial for our important work and might just play around with Yaketty on the side.

You have the wrong impression of how the versioning system works. The biggest kicker is: Yaketty is supported for another 7 months. At that point, you will have to wrestle with upgrading to 17.04 only to be supported for another short 9 months, etc. You can choose either bleeding edge upgrade treadmill, or Xenial which, as a LTS, is supported until 2021.

If former, then others will have to step in shortly. I don't run 16.10 yet and am of limited help.

---

### Post by CarpCharacin on 2016-12-18
I know ho the versioning system works and I still want to go with 16.10.

---

### Post by DuckHook on 2016-12-18
> **CarpCharacin said:**
> …I still want to go with 16.10.

> **DuckHook said:**
> …then others will have to step in shortly. I don't run 16.10 yet and am of limited help.

&#8593;

---

### Post by RobGoss on 2016-12-19
> **CarpCharacin said:**
> I know ho the versioning system works and I still want to go with 16.10.

The suggestion is16.04 is much more stable and LTS, which makes using it more enjoyable 

16.10 still have some issues and may not suit that machine you're using 

With Linux we have to keep a open mind and see what works the best for us

I only use LTS releases because I avoid issues like this

---

### Post by mörgæs on 2016-12-19
How does Lubuntu 16.10 work in a live boot using the wired mouse?

---

### Post by CarpCharacin on 2016-12-20
I haven't tried lubuntu.  This is ubuntu unity.  It still isn't working :(

---

### Post by CarpCharacin on 2016-12-21
It should be working.  I just want to know what is wrong.  The graphics drivers aren't installed, but I can't install them until after the OS is installed.

---

### Post by mörgæs on 2016-12-21
> **CarpCharacin said:**
> I haven't tried lubuntu.  This is ubuntu unity.  It still isn't working :(

When people encourage you to try something it serves a purpose. Trying Lubuntu 16.10 does not mean that it is the final goal nor that it has to be installed, but it serves as a data point when diagnosing the problem. 

If you don't experiment there is no point for us in posting in the thread.

---

### Post by CarpCharacin on 2016-12-21
Ok I will try it.

---

