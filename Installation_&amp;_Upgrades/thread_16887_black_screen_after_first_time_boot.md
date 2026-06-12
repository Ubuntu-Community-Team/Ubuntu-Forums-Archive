---
title: "black screen after first time boot"
date: 2005-02-24
forum: Installation &amp; Upgrades
---

### Post by Jay-DK on 2005-02-24
ubuntu is all new to me!!

i have just installed ubuntu, without errors, but when i try to boot my installation, i shows all the information where it says [ok] to a lot of things, but when it reaches the point where i have to log in my monitor turns off and the only way i can turn on the monitor again is to press the power button, but then the system off course turns off


what can i do ?

---

### Post by jdonnell on 2005-02-24
I'm having the exact same problem.

---

### Post by jdonnell on 2005-02-24
I figured out what my problem is. For some reason my monitor doesn't like the settins in /etc/X11/XF86Config-4

I took out all instances of 1024x768 and left 800x600. Now it boots fine, but the color depth sucks and who wants 800x600. Oh, my monitor is an envision en-710

I'll post again if I can get the color and resolution fixed. I don't need x for this comp because I'm just going to use it for a small subversion server so I may not spend a lot of time on trying to get x working right.

---

### Post by jdonnell on 2005-02-24
Ok, I got everything working right. All I did was boot with the live cd, which setup the display perfectly. While running the live cd I emailed myself the /etc/X11/XF86Config-4 file. I then booted into the installed version of ubuntu, downloaded the file from my web based email, and copied it over the /etc/X11/XF86Config-4 created by the install. You might want to back this file up first ;)

---

### Post by Jay-DK on 2005-02-25
allrigthie then,  i will try that as soon as i get home, thanks for the reply

---

### Post by Wim Sturkenboom on 2005-02-25
Your monitor usually goes black when the Horizontal Refresh (HorizsSync) is too high. Some monitors give an out-of-sync message, some go black. This is a protection. Older monitors don't have this protection and may get damaged.

Fixing the problem is usually applying the correct settings for HorizSync and VertRefresh and restarting X. You can find those in your monitor manual.

---

### Post by Jay-DK on 2005-02-25
how can i do that when i cant even log in? as i mentioned before i am all new to ubuntu and linux, so i havent got at clue off what to do with this, or how to do it  ](*,)

---

### Post by jdonnell on 2005-02-25
when the screen is black you can hit ctl+alt+f1 and it will take you out of x and to the command line. I think ctl+alt+f7 will take you back. Once your in the command line you can login and edit your x86 conf file.

---

### Post by jdonnell on 2005-02-25
[QUOTE=Wim Sturkenboom]
Fixing the problem is usually applying the correct settings for HorizSync and VertRefresh and restarting X. You can find those in your monitor manual.[/QUOTE]

Yes, I played around with this for a while, but I couldn't get it setup right. It was a lot easier to just copy the config created by the live cd :)

---

### Post by yclept on 2005-03-17
I am having similar trouble.

I am installing Hoary on a Dell Latitude c400.  I can get the LiveCD to work, but not the install.  I get all the way to the end, and get a black screen.  I presume this has something to do with the laptop video controller, etc.  

I cannot hit ctrl-alt-f1 and get out of X11 because Hoary uses X.org.  Is there another way to edit the HorizSync now?  

Is there a newer thread on this?

I did install and boot using pci=noacpi but it doesn't seem to matter.  I'll keep tinkering.

I am a linux newbie.  This past week I have been obsessed with Linux, somehow gravitated to Ubuntu, and away I go.  By the way, I can't get the Warty Warthog to work on LiveCD on this same machine.  

Any help/guidance/pointers to threads would be appreciated.

---

### Post by jdonnell on 2005-03-17
I haven't used hoary or x.org so I can't really help. You should create a new thread for this. You'll probably get more help that way.

Welcome to linux.  :)

---

### Post by yclept on 2005-03-17
Thanks.  I got the thing working after some frustration by editing xorg.conf and changing all monitor references to 800x600.  I'll see if I can get it working better myself before making a new thread.  

I did like how the thread popped up to the top of the list when I posted, so perhaps some others will see too.

-----
addicted to linux...must...get...back...to...work

---

