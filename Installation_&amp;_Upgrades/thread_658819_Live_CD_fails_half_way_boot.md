---
title: "Live CD fails half way boot"
date: 2008-01-05
forum: Installation &amp; Upgrades
---

### Post by axioma on 2008-01-05
Hi, 

First everybody: A Happy New Year.

I've got a problem when booting Live CD (Straight from Canonical Ltd.)
My hardware: a NEC- LaVie LL850/G using:  1.66 GHz, 1.46 RAM, ATI Radeon Xpress 1250; Windows XP Sp2. 

I have been working with Ubuntu in VMware-player. Liked it very much and want to try to install the OS but when I start booting Ubuntu, it just stops half way the boot. 

The check list till that point gives everything an [OK]. These are the last lines before the crash:

Starting Gnome display manager (OK)
Starting deffined execution scheduler ald  (ok)
Starting periodic commant scheduler crond (OK)
Checking battery state    (OK)
Running local boot scripts (/etc/rd.local)

And here it stops. Also after extended waiting no movement! What can I do!!!

Axioma

---

### Post by Craigus on 2008-01-05
Have you done the check CD option in the live cd boot menu to check cd integrity ?

---

### Post by PmDematagoda on 2008-01-05
When you reach the end of the boot process, press Ctrl+Alt+F1, that will bring you to a tty. Once there, execute:-
```
sudo dpkg-reconfigure xserver-xorg
```
select the driver as vesa, the other options may be anything but the driver **should** be selected as vesa.

After configuration execute:-
```
sudo startx
```
That should get you to the GUI.

---

### Post by axioma on 2008-01-05
HI,

Yes I checked the CD, I even tried two others.

I did as you suggested PmDematagoda, but I get the following result:

(==) log file: "/var/log/xorg.O.log
(==) using config file: "/etc/x11/xorg.conf"
(II) Module already built-in
(EE) Vesx(0): no matching modules
(EE) screen(s) found, but non have a usable configuration

Fatal server error:

No screens found
X10: fatal IO error 104 (connection reset by peer) on server ":0.0"
after 0 requests (0 known processed) with 0 events remaining.

I have  tried the procedure several times with the same result. I also went through the text setup with I got after going to the dpkg-reconfigure

Forgot to mention: I'm working with a laptop. 

Thanks!

---

### Post by Partyboi2 on 2008-01-05
Not sure if this will work. When you get to
>  Running local boot scripts (/etc/rd.local)Push Ctrl Alt F1 to go in a tty terminal.
Type
```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.bak
``` to backup xorg.conf
Then type
```
nano /etc/X11/xorg.conf
``` and look for  ```
Section "Monitor"
```and at the bottom add this to it.
```
HorizSync 36-52
VertRefresh 36-60
Option &#8220;MonitorLayout&#8221; &#8220;LVDS, AUTO&#8221;
``` Exit from nano 
```
Ctrl+o then press "enter" then press Ctrl+x
```and restart gdm 
```
/etc/init.d/gdm restart
```If that doesn't work maybe you will have more success with the alternate cd
[http://releases.ubuntu.com/7.10/](http://releases.ubuntu.com/7.10/)

---

### Post by axioma on 2008-01-05
Hi, 

I have tried that too but to no avail. 
Might try to boot with alternate CD, but will take me about a week to download. So in the meanwhile, if somebody has any other ideas; they will be very much appreciated. 

Please give me a week or so than I will let you know how things have worked out.

Anyway, many thanks so far!

---

### Post by axioma on 2008-02-05
Haven't found any solution yet but I'll be trying till I find the answers in live.
Everybody thanks so far!!!:popcorn:

---

### Post by Craigus on 2008-02-05
Does this help:

[http://warofwords.wordpress.com/2007/10/07/using-ubuntu-on-hp-6515b-ati-x1250/]("http://warofwords.wordpress.com/2007/10/07/using-ubuntu-on-hp-6515b-ati-x1250/")

---

### Post by iNerdSure on 2008-02-22
> **axioma said:**
> Haven't found any solution yet but I'll be trying till I find the answers in live.
Everybody thanks so far!!!:popcorn:

You need to use the Ubuntu-7.10-alternate-CD.  The installation is not as easy as the LiveCD.  But if you fllow the steps, you should be able to complete the installation.

---

### Post by PokerFacePenguin on 2008-02-24
> **iNerdSure said:**
> You need to use the Ubuntu-7.10-alternate-CD.  The installation is not as easy as the LiveCD.  But if you fllow the steps, you should be able to complete the installation.

I am getting to the same place using the alternate install....just thought I would throw that in.  I am currently troubleshooting this on a reinstall of a Kubuntu feisty upgrade gone bad.  I have burned practically every version of kubuntu and ubuntu complete with alternate installs and AMD versions (this is a core2duo machine).

I even went out and bought a new video card to throw in just to try to avoid sinking a whole weekend into it.  So much for that.

The text installer finished and asked me to remove the alternate cd. 

I will try some of these suggested solutions.  more later.

---

### Post by swatsbiz on 2008-07-05
The above worked for me ... had to do sudo nano and sudo /etc/init.d/gdm restart

Apart from those changes, started great

David

---

