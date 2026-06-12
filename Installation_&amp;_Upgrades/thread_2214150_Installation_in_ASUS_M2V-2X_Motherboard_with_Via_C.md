---
title: "Installation in ASUS M2V-2X Motherboard with Via Chrome HC IGP onboard graphics card"
date: 2014-03-30
forum: Installation &amp; Upgrades
---

### Post by SERGIO_MARTINEZ_LO on 2014-03-30
Hi:

First at all, i'm new in this forum, and I am not an expert in linux. I've intalled ubuntu in other computers and it went well, but with the computer I have now I have a critical problem in the installation.

I Have a ASUS M2V-2X Motherboard, that has an integrated graphics card (Via Chrome HC IGP)
I'm trying to install Ubuntu 12.04 with the live CD. When the installation enters in the graphic mode the screen shows a lot of colour lines and I can do nothing. Is like the graphic card is not supported by Ubuntu.

I had the same problem when I tried to use a live CD of the aplication "clonezilla", that is based on linux too.

I don't know what can I do to solve this problem.

The computer is 6 or 7 years old.

If you need more info about the problem just ask me. It's very strange.

Thank you in advance

---

### Post by mörgæs on 2014-03-30
Hi, welcome to the fora.
Are you able to boot a live Lubuntu 14.04, the development release?

---

### Post by SERGIO_MARTINEZ_LO on 2014-03-31
> **mörgæs said:**
> Hi, welcome to the fora.
Are you able to boot a live Lubuntu 14.04, the development release?

Hi:

I tried to boot the Lubuntu 14.04 beta1 and, at the first, it seems to work, but 5 or 6 seconds after the graphic mode appears it do the same
[IMG]http://imagizer.imageshack.us/v2/320x240q90/59/lid9.jpg[/IMG]

And a seconds after...

[IMG]http://imagizer.imageshack.us/v2/320x240q90/203/o3lf.jpg[/IMG]

And that is what happens with ubuntu, lubuntu, and all the distributions I've tried. It seems impossible to install Linux in this computer.

---

### Post by mörgæs on 2014-03-31
Are you able to open a terminal with Ctrl + Alt + F1?

---

### Post by SERGIO_MARTINEZ_LO on 2014-03-31
> **mörgæs said:**
> Are you able to open a terminal with Ctrl + Alt + F1?

Nothing happens, impossible to open a console

---

### Post by SERGIO_MARTINEZ_LO on 2014-04-01
I could open the terminal just before the screen crashes. But, once in the terminal, it does the same after a few seconds, even being in text mode

---

### Post by mörgæs on 2014-04-01
What about a text-only system? 
[http://archive.ubuntu.com/ubuntu/dists/trusty/main/installer-i386/current/images/netboot/](http://archive.ubuntu.com/ubuntu/dists/trusty/main/installer-i386/current/images/netboot/)

---

### Post by SERGIO_MARTINEZ_LO on 2014-04-01
The computer should be capable of run ububtu (It ran in an even older computer I had). It is an AMD64 2GHz 1GB RAM., enough, in theory.  Perhaps with a text mode install (and driver update during installing), but ubuntu seems not to have it

---

### Post by mörgæs on 2014-04-02
Right now it's not about running anything but diagnosing the problem. A text-only system is a good beginning for that.

---

### Post by SERGIO_MARTINEZ_LO on 2014-04-02
Hi again, I used that netboot CD. Icould make a complete install but, after hours of install, i rebooted the system and, after the login, it did the same with the screen.
The CD has a rescue mode.maybe i can do something. What do you think?

---

### Post by mörgæs on 2014-04-03
I don't understand. How can a minimal install take hours? What exactly did you do?

---

### Post by SERGIO_MARTINEZ_LO on 2014-04-03
I choose install, set the options (country, keyboard, partitions). Then it asked for additional services & packages, and i choose ubuntu (perhaps that was the problem).
Then it started to download packages, then install them, and it took for at least 6 hours (it is not normal 6 hours install)

---

### Post by SERGIO_MARTINEZ_LO on 2014-04-03
Ok, i'm now in rescue mode, in the command line

---

### Post by sudodus on 2014-04-03
I think you have problems with the integrated graphics card (Via Chrome HC IGP), and you need a way to make linux cooperate with that card.

Maybe a re-spin or flavour based on Ubuntu 12.04 LTS will be more successful. It is often like that with old or middle-aged hardware.

So I suggest that you download the mini.iso version 12.04 (which cannot boot from USB, you must use a CD or DVD drive). And from that you can install ***Xubuntu***, which has long time support until April 2015. Lubuntu 12.04 had no long time support and has passed end of life.

There are several other alternatives, that are also based on Ubuntu 12.04 LTS, for example ***Bento, Bodhi, LXLE*** that have long time support until April 2017. But I think standard Ubuntu needs more horsepower and memory to run well.

-o-

You can also read the following thread, that might give you valuable tips (it is about another VIA graphics card)
[URL="http://ubuntuforums.org/showthread.php?t=2207391"]
Fujitsu-Siemens Amilo L7320: an Ubuntu's problematic installation[/URL]

---

### Post by mörgæs on 2014-04-03
From any working installation please run
```
sudo lshw -sanitize > lshw.txt
```
and post lshw.txt in CODE tags.

---

### Post by SERGIO_MARTINEZ_LO on 2014-04-04
Hi again:

I installed ubuntu 14 again without desktop. Only the text mode.

I login ok, and for one minute moreless i can work with the command line.
I can do the "lshw"in screenshot, but i have no time to mount an usb and save the file because the system crashes again( it does exactly the same that in desktop).
Is something that runs or happens one minute after login that crashes the system.

---

### Post by sudodus on 2014-04-05
We need trouble-shooting to find out what it can be. I can think of a few causes.

Some electronic component might fail, and it can be sensitive to temperature (it might be a good idea to get rid of dust inside the computer)

- low voltage from a failing power supply unit
- bad RAM - can be tested with memtest at the grub boot menu. Not one single error is allowed during several hours of testing.
- some other bad component on the motherboard

- problem with wifi, that fails after trying to configure automatically

- some other problem due to a driver or other program of Ubuntu version 14.04

Problems with electronic components should be (rather) independent of the version of Ubuntu. Problems with a driver or other program should depend on the version of Ubuntu.

---

### Post by SERGIO_MARTINEZ_LO on 2014-04-12
Hi again.
I bought a new graphics card and it still did the same, so i suppossed it was a motherboard incompatibilitywith ubuntu.
I have replaced the motherboard (i bought one with the same socket than mine) and it worked with no problem, so it was an ASUS M2V-MX incompatibility.
Thank you for your help!

---

### Post by mörgæs on 2014-04-12
Good, please mark the thread 'solved'.

---

