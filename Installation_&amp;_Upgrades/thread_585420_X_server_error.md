---
title: "X server error"
date: 2007-10-21
forum: Installation &amp; Upgrades
---

### Post by Smoothcrm7 on 2007-10-21
Hey sorry, Im pretty much a noob with linux been using windows since 3.2 just decided to give it a shot, anyways i used the live cd to install and rebooted after that i decdied to try and fix the resolutions so that i coudl use my external monitor anwayys now on boot up i get


/etc/gdm/failsafexserver:line 47

Could not retreieve EDID get edid not installed


*using latest ubuntu release*

Laptop config

Fujitsu T4220 lifebook 
2.4 ghz santa rosa
4 gigs of ram

---

### Post by ohyea on 2007-10-21
Yea so I got the exact same error. I was just about to start a thread about it when I noticed this one. If anyone could point us in the right direction, that'd be great. Thanks!

---

### Post by JSD116 on 2007-10-21
Right before it tries to boot hit Esc and go in to recovery mode to get back to the command prompt. Then type in:

```
sudo dpkg-reconfigure xserver-xorg
```
Run through the questions. Then reboot.


If that doesn't work try

```
sudo dpkg-reconfigure -phigh xserver-xorg
```

If that doesn't work try this section of the forums: [http://ubuntuforums.org/forumdisplay.php?f=138](http://ubuntuforums.org/forumdisplay.php?f=138)

---

### Post by Smoothcrm7 on 2007-10-21
first one worked perfectly thanks so much!

---

### Post by ohyea on 2007-10-21
So if I'm getting that error when I'm trying to install, when should I hit Esc?

---

### Post by bockman on 2007-10-21
Neither works for me, all that works is using the vesa driver instead. The ATI driver (the one that comes with linux, not the ATI Proprietary driver) worked in Feisty perfectly.

---

### Post by JSD116 on 2007-10-21
> **ohyea said:**
> So if I'm getting that error when I'm trying to install, when should I hit Esc?
Right after the boot screen when you turn on the computer. It should show at the bottom a countdown and and says hit Esc for options or something.  At least it does on mine, can't speak for other computers. 

Try looking in that other forum section I posted above. It is the dedicated video forum here that has a lot more info on video problems.

---

### Post by ohyea on 2007-10-21
So right after I get to the install ubuntu screen I hit Esc which takes me to a text based screen. I type in sudo dpkg-reconfigure xserver-xorg and it says that sudo is not a recognized command. Any ideas?

Again, orginial problem: failsafeXServer: line 47
Warning: Could not retrieve EDID because get-edid is not installed

---

### Post by JSD116 on 2007-10-21
> **ohyea said:**
> So right after I get to the install ubuntu screen I hit Esc which takes me to a text based screen. I type in sudo dpkg-reconfigure xserver-xorg and it says that sudo is not a recognized command. Any ideas?

Again, orginial problem: failsafeXServer: line 47
Warning: Could not retrieve EDID because get-edid is not installed
I had the EDID problem and 

```
sudo dpkg-reconfigure -phigh xserver-xorg
```  

fixed it.

---

### Post by ohyea on 2007-10-21
Yea, but where do you type that code? I tried typing it in after the install failed and that didn't work. I tried hitting Esc after the cd loaded and it took me to a command screen and the command sudo wasn't recognized. So where do I type that code in?

---

### Post by m0gely on 2007-10-23
> **bockman said:**
> Neither works for me, all that works is using the vesa driver instead. The ATI driver (the one that comes with linux, not the ATI Proprietary driver) worked in Feisty perfectly.

ditto!  Really wish there was more input on the forums about this.

---

### Post by Bleyze on 2007-11-24
Try sudo apt-get install read-edid to install it.

---

### Post by ewtrowbr on 2007-12-05
I think what the other users are confused about, is that they are hitting the escape key at the initial boot CD menu, and it drops them into a prompt that looks like this:

boot: 

This looks like its waiting for kernel arguements, not bash commands.

I am trying to install ubuntu on a working windows installation, and am having the same problem... I don't see how to get to a shell before the system boots...

thanks,
Erich

---

