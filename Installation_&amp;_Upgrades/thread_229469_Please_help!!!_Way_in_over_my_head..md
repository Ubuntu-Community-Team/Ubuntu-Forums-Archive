---
title: "Please help!!! Way in over my head."
date: 2006-08-04
forum: Installation &amp; Upgrades
---

### Post by anarchyburger on 2006-08-04
Hey guys

Alright so I used instalux to get ubuntu loaded on my srx77.  I had to use the breezy version though because they dont have a network install option for dapper drake yet.  Well the install went smoothly and it detected everything just fine until it got to rebooting the system.  It rebooted and started to load ubuntu but instead of a nice pretty gnome gui I get a bash screen asking me to login.  I am guessing that it only installed the base system so where do I go from here?????  Anyone have a walkthrough.  Also the srx77 is a sony vaio notebook with no optical drive and cant boot from usb.  I really need instructions on how I can install more packages and get this thing up and running.  If I could atleast get gnome then I can go from there but being a n00b a nix I dont know bash.

Please Help me

---

### Post by Tomosaur on 2006-08-04
Sounds like you downloaded the server version. Either download an install the  Desktop version, or type this into the terminal:

sudo apt-get install ubuntu-desktop

---

### Post by anarchyburger on 2006-08-04
alright I tried that and it kinda worked it tried to get it but then it told me that it cant find Ubuntu-desktop.

---

### Post by zxee on 2006-08-04
> **anarchyburger said:**
> alright I tried that and it kinda worked it tried to get it but then it told me that it cant find Ubuntu-desktop.

Your reply has an uppercase "U" in ubuntu it should be lowercase.
Also you may need to enable repositories in /etc/apt/sources.list and do > sudo apt-get update

---

### Post by pomegranate on 2006-08-04
> **zxee said:**
> 
Also you may need to enable repositories in /etc/apt/sources.list and do

Sorry to butt in, but how do I do that? I think that might be the cause of a problem I'm having installing new programs...

---

### Post by Jagot on 2006-08-04
> **pomegranate said:**
> Sorry to butt in, but how do I do that? I think that might be the cause of a problem I'm having installing new programs...

Use either of these guides:

[http://psychocats.net/ubuntu/sources.php](http://psychocats.net/ubuntu/sources.php)
[https://help.ubuntu.com/community/Repositories/Ubuntu](https://help.ubuntu.com/community/Repositories/Ubuntu)

If you're stuck without a GUI then use nano.

---

### Post by avtolle on 2006-08-04
Just so I'm clear; to anarchyburger: you installed 5.10, a/k/a "Breezy", right? This may make a difference to those who are helping you. As an example, the souces.list would need to be those for "Breezy", not "Dapper" (the current version). I'm not going to be able to follow this for long, as I must leave (it's Friday, quitting time).

---

### Post by pomegranate on 2006-08-04
thanks Jagot I will check those out

---

### Post by anarchyburger on 2006-08-04
hey guys

well been installing stuff as I find it in the source list but I need to know how do you run things in bash and also how do you go about setting the thing up to boot into a gui and not bash.  That is my biggest problem now.

Thanks 
Anarchyburger
Hold the government

---

### Post by MasterXandrex on 2006-08-04
After you 'get' ubuntu-desktop or gdm it should default into the GUI. If it doesn't do this:

sudo ln -s /etc/init.d/gdm /etc/rc2.d/S13gdm

then reboot

---

### Post by zxee on 2006-08-04
> **anarchyburger said:**
> hey guys

well been installing stuff as I find it in the source list but I need to know how do you run things in bash and also how do you go about setting the thing up to boot into a gui and not bash.  That is my biggest problem now.

Thanks 
Anarchyburger
Hold the government

Have you been successful in installing ubuntu-desktop?
If I understand you correctly you want to boot into gnome or whatever your DE is. /etc/inittab has the default runlevel setting.
 The begining of that file looks like this:> # /etc/inittab: init(8) configuration.
# $Id: inittab,v 1.91 2002/01/25 13:35:21 miquels Exp $

# The default runlevel.
id:2:initdefault:

Check that file out with an editor and make sure the default runlevel is set as shown above.

---

### Post by anarchyburger on 2006-08-05
hey guys

thanks for you awesome help I got the gui installed and have upgraded to dapper with one slight problem no my monitor is stuck in 640-480 res and cant get it to change no matter what I try

---

