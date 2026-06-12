---
title: "Login Screen Problem"
date: 2005-09-28
forum: Installation &amp; Upgrades
---

### Post by SwitchShift on 2005-09-28
I have a dell dimension 8300 with NVIDIA GeForce 5200 and an 1703fp dell monitor. The problem i'm having is that when i go to boot up linux and get to the login screen (well i think it might be the login screen) my screen goes black and then turns into blocks of different flashing colors. I have also tried different versions of ubuntu and i get the same problem. I am completely new to linux and i have no clue as to how i am supposed to fix this problem, so if anyone can help me out i would be extremely grateful.

---

### Post by mlomker on 2005-09-28
It probably automatically set the wrong video driver.  Hit Escape at boot-up to go into the grub menu and select 'rescue'.  Once you get to a command prompt type **dpkg-reconfigure xserver-xorg**.  That'll run you through the setup for the graphical environment.  Pick 'vesa' when it asks you for a video driver and just take the default settings for whatever you're not sure about.

Once you get logged in and going you can look into installing a better video driver.

---

### Post by SwitchShift on 2005-09-28
I did what you said but at first it didn't work, so i tried it again but instead of choosing 'vesa' for the video driver i chose 'nvidia' and it worked. :D Anyways thanks for the help in solving my problem.

---

### Post by mlomker on 2005-09-28
VESA is an industry standard that works with most cards, but it's slow and low-resolution.  Glad it worked out.  :cool:

---

### Post by elin2004 on 2005-09-29
Good day …….. I need help im a newbie and decided to try Ubuntu! Its really super cool it can detect my network computer all of them and its already PlugNPlay cool! But I enjoyed it for just an hour! i install a new themes and it  installed no sweat! But when I tried to use it (i logout  it hangUp (error is corrupted themes!) then I rebooted but it keep stoping @  LogIn Screen how could i return to Ubuntus Default LogIn Screen (Human) and how would i unInstall the theme using a terminal i know im a newbie but i need to do it i need help ASAP please..............

---

### Post by mlomker on 2005-09-29
>  i know im a newbie but i need to do it i need help ASAP please..............

I've never installed a gnome theme, since I run KDE.  I'd recommend creating a new post in the desktop support forum.

---

### Post by bullraiser on 2005-09-30
Hi,

 I installed Hoary 5.04 from the CD. Everything went well until I get the login screen which was blank. I use Dell Latitude CPxJ (Pentium III, 650Mhz, 128MB). There was also few installation error during the base configuration and the installation process prompted to insert the boot CD. I did, and it tried (seems!!) to install the missing packages. 

 Everything went well and upon starting, I get a blank screen. My video driver is ATI (8-16MB) and could anyone help me, what should I need to get my system up and running.

PS: I tried re-installing & rebooting several times. Few times, it stopped during the installation (some pkgs are missing or I/o error) and few times, i land up to login screen but couldnt login with some bizarred "Gnome Session Manager" crash dialog box on login. 

However, I can dual boot to my Win XP, but I would really like to move over to Linux and can someone help me with this problem?

--Thanks

---

### Post by mlomker on 2005-09-30
You could try the reconfigure command that I mention in the first post of this thread, but I think you should start over and install Hoary again.  If you burned your own CD then you might want to reburn it at 4x speed.  Nero, in particular, has problems with linux boot discs that are burned any faster than that.

---

### Post by bullraiser on 2005-09-30
BTW, I am using the install boot CD, I got from Ubuntu. So, shouldnt really a problem with the CD, I guess!!.

---

