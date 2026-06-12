---
title: "uh... what happened?"
date: 2007-05-30
forum: Installation &amp; Upgrades
---

### Post by spowell398 on 2007-05-30
Hi... Um. I'm new to Ubuntu, and I ran into a hitch. It installed fine and even let me use some of my Windowz files in Ubuntu. The only problem is that I noticed that the screen savers were kind of slow (especially some of the more detailed ones) and my screen resolution would not go  above 1024 by 768. My screen is at 17in. at 1280 by 1024. I used the Restricted Device Manager to install the nVidia driver (I'm running an 8800GTS). It installed fine but when I rebooted my system it wouldn't boot into the visual system. A bunch of jumbled stuff came up... which I couldn't understand at all and now I can't even use the visual stuff at all now... Can anybody help me?

---

### Post by bulldog on 2007-05-30
I think you need to install the restricted modules for your kernel.
Go into console [recovery mode] and perform ```
uname -a
``` to see which kernel you use.
You'll get something like ```
bulldog@AMD64:~$ uname -a
Linux AMD64 2.6.20-16-generic #2 SMP Wed May 23 01:46:23 UTC 2007 i686 GNU/Linux
bulldog@AMD64:~$ 
```

Install the restricted modules ```
sudo aptitude install linux-restricted-modules-2.6.20-16-generic
```
Use you kernel specs of course.
Reboot and it should work fine.

---

### Post by spowell398 on 2007-05-30
um... ok... I booted Ubuntu into the recovery mode. I typed in uname -a like you said... It popped up with what you said it would. Then I typed in sudo aptitude install linux-restricted-modules-2.6.20-16-generic like you said. (I have the same parameters). Then I rebooted like you said. It when it rebooted it said the exact same thing. In quotes (Failed to start x-server (your graphical interface) It is likely that it is not set up correctly. would you like to view the X server output to diagnose the problem. <yes> <no>    Is there anything else I can do? ... I forgot... also, when I tried to type in what you said it popped up saying that 0b of something could not be installed... and something about it that 0b being installed when it was unpackaged or something... Sorry I'm really new at this stuff.

---

### Post by bulldog on 2007-05-30
Well,you need to read carefully what errors you get,otherwise we can't help you.
You can try to reconfigure xserver```
sudo dpkg-reconfigure xserver-xorg
```
and set the correct parameters.
But to run you graphics driver,you need the restricted modules installed.

---

### Post by spowell398 on 2007-05-30
ok... I tried to get you some more information this time... sorry I didn't get you more info last time. I went into the reconfigurer for x server. Everything went fine until I got to the option that asks (desired default color depth in bits. I select 24 because above it says that 24 is actually 32 bit. When I highlight 24 and click ok the command line interface pops up at the bottom saying (xserver-xorg protinst warning: overwriting possibly-customized configuration file; backup in /etc/X11/xorg.config.20070530163945) what do I do then. I think this is going to fix it but I can't get passed this point... thanx for the help.

---

### Post by bulldog on 2007-05-30
The warning only means it's making a backup from the 'old' xorg.conf,nothing to worry about.
If you mess things up,you can always return to the 'old' copy.

You default depth  should be 24 indeed,so select it and proceed.

---

### Post by spowell398 on 2007-05-30
so... its not actually freezing there and waiting for a command from me?... It looks like its waiting for me to type something.

---

### Post by bulldog on 2007-05-30
You have to select it with the space bar if I'm correct [it's been a while sins I used it]
so you have to see for your self what to do,there should be some explanation in your screen I suppose.
But try to proceed beyond this item,there's always the possibility to change it later by editing the xorg.conf.

---

### Post by spowell398 on 2007-05-30
I'm sorry I'm so stupid at this... LOL... I tried to do what you said... seeing if there was an explenation, using the space bar, etc... but nothing seems to do the trick. I still pops up with that same command line. Is there any command I can do to continue or escape that part? I even tried to set it to another setting and that still didn't work. 

Um. Ok... Let me start over from scratch. I'm going to reinstall Ubuntu and see what happens. When I install it, how do I install the nVidia drivers correctly? I never could get this to work. I'm mostly concerned with the screen resolution not going to 1280 by 1024 and some of the screen savers being choppy. I'm running an 640mb card so nothing should be slow or choppy, especially something as simple as a screen saver... LOL... thanx for the help you have been giving... If you could direct me on the way to properly install the drivers, that would be very helpful.

---

### Post by spowell398 on 2007-05-30
Ok... I tried re-installing Ubuntu, It did the exact same thing it did the last time. When I try to install the nVidia driver using the Restricted Device Manager. It installed easily but when it tried to reboot picture A came up. If you press <Yes> Pictures B1 and B2 pop up... <--- same page just scrolled down. Then if you hit continue which is just a continuation of the last two just another part I guess C comes up (which is very long, I didn't have time to take pictures of it being scrolled down). I restarted my rig and tried to configure the xserver like you said. Everything goes perfect until I get too pictures D1 & 2... Soooo is there anything I can do to install the nvidia drivers?  :(  ](*,)

---

### Post by spowell398 on 2007-05-30
wooops... I forgot to add the pictures... lol... It wouldn't let me send them because they were too big... let me take some more pics and i'll show you what they say.

---

### Post by spowell398 on 2007-05-30
ok here are the pictures... they might be some help... thanks again for helpin me with this prob... I'm REALLY new to this.

---

### Post by bulldog on 2007-05-31
If you take a look at screenshot three,you see that there is extra information available.
It has nothing to do with the restricted modules,it seems it has some problems with your graphics.

In your last screenshot you have to hit the tab-key to select ok and proceed.
You can try to let ubuntu make the choices for you.
```
sudo dpkg-reconfigure -phigh xserver-xorg
```

---

### Post by spowell398 on 2007-05-31
sigh... ok. I went and tried to hit tab when the command line popped up at the bottom but the only thing that happened was my computer made its annoying beep noise. After hitting tab I tried typing the following like you said.```
sudo dpkg-reconfigure -phigh xserver-xorg
``` That worked for one screen but when I got to the screen where I select the video size (1280 by 1026) the following picture popped up... Its basically the same as the other one just on another part of the setup. Is there away to avoid or get rid of it saying this warning?

---

### Post by bulldog on 2007-05-31
No the warning stays,I'm afraid.
It's only telling you,it makes a backup.

Did you read the additional info for your graphics?
It's a rather new card and I read some issues with Vista [driver] too.

If you're a little familiar with Linux,you can edit the xorg.conf manually with nano.
Of course you should know which settings you want to use.

---

### Post by spowell398 on 2007-05-31
Thanks for the help... I finally got it working right... :)  On my other thread another person told me to change nvidia to nv in the xorg configuration and that fixed my problem. I still can't use the 3d stuff like the screen savers but because it is a free driver but at least its working at full resolution now... :) Thanks for you help. Without the Ubuntu forum I would be completely lost right now... Thanx

---

