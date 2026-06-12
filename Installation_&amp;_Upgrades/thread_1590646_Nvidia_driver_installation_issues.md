---
title: "Nvidia driver installation issues"
date: 2010-10-08
forum: Installation &amp; Upgrades
---

### Post by febro on 2010-10-08
Hello guys, I need some help from experienced linux users on how to properly install newest nvidia drivers on my Ubuntu 10.04

Being a total beginner to linux, I can't seem to find a decent guide on how to install these drivers without much hassle, even though I've been searching for almost couple of hours now.

[I]**First, my system specs, taken with HardInfo**

Processor		: 2x AMD Athlon(tm) II X2 240 Processor
Memory		        : 3091MB (1865MB used)
Operating System	: Ubuntu 10.04.1 LTS

[COLOR="DarkSlateGray"]-Display-[/COLOR]
Resolution		: 1360x768 pixels
OpenGL Renderer		: GeForce GT 220/PCI/SSE2
X11 Vendor		: The X.Org Foundation

[COLOR="DarkSlateGray"]-Multimedia-[/COLOR]
Audio Adapter		: HDA-Intel - HDA NVidia
Audio Adapter		: HDA-Intel - HDA NVidia

[COLOR="DarkSlateGray"]-SCSI Disks-[/COLOR]
HL-DT-ST DVDRAM GH22NS50[/I]

---
Now, I've installed the "default" (dunno if that would be the correct categorizing :P) driver with the "Hardware drivers" utility from _System->Preferences->Hardware drivers_ because I've failed numerous times trying to install the package from [[COLOR="Red"]nVidia site[/COLOR]]("http://www.nvidia.co.uk/object/linux-display-amd64-256.53-driver-uk.html") ; I would always get an error while trying to run the package :
[COLOR="Sienna"]"It seems that X server is running on your linux, please deactivate it to install this package" [/COLOR] or something like that, but I'm sure it was about X running.

I would really appreciate if someone experienced would advise me on how to remove old drivers (if that step is needed) and properly installing the ones provided in the link a bit above.
I remind you that I'm a total beginner for linux, so it would be awesome if You could explain it to me like I am a retard :D

Thank You in advance :)

---

### Post by febro on 2010-10-08
Bump ? :P

---

### Post by andrewthomas on 2010-10-08
Try this thread.

[http://ubuntuforums.org/showthread.php?t=1571606](http://ubuntuforums.org/showthread.php?t=1571606)

---

### Post by febro on 2010-10-08
Thanks for the link, but new problem appeared.
When I'm in terminal mode, it wont accept my normal login that I use to login to ubuntu on startup, any suggestions (maybe to login as root) ?

---

### Post by andrewthomas on 2010-10-08
> **febro said:**
> Thanks for the link, but new problem appeared.
When I'm in terminal mode, it wont accept my normal login that I use to login to ubuntu on startup, any suggestions (maybe to login as root) ?
Do not log in as root.  
After you  type your username <enter> and password <enter> what error do you get?

---

### Post by febro on 2010-10-08
I get "Login incorrect" message, which is foolish because I'm in ubuntu right now and I've logged in with that same info :S

OK, I've got it, I have numbers in my password and I've tried to enter them with my numeric part of the keyboard, didn't know they don't type in over it.
I'm an idiot XD

I'm gonna try that tutorial you posted as a solution to me and I'll report back, thank You for assisting me.

---

### Post by andrewthomas on 2010-10-08
are you sure that you are typing the correct username?

from Applications > Accessories > Terminal 

enter 

```
pwd
```

it should read 

```
/home/username
```

Is this the same one you were typing in?

---

### Post by febro on 2010-10-08
> **andrewthomas said:**
> are you sure that you are typing the correct username?

from Applications > Accessories > Terminal 

enter 

```
pwd
```

it should read 

```
/home/username
```

Is this the same one you were typing in?

Ye, I've found out what I was doing wrong, I edited my previous post with an explanation ><

---

### Post by febro on 2010-10-08
Sigh, new problem, I've managed to start installation from terminal and installer now says that it isn't compatible with Nouveau.
Any solutions, or that's all I can do ?

---

### Post by andrewthomas on 2010-10-08
please post the complete error message

---

### Post by febro on 2010-10-08
Ok I've managed to finally install the drivers following guide on this page 
[http://uk.download.nvidia.com/XFree86/Linux-x86_64/256.53/README/installdriver.html]("http://uk.download.nvidia.com/XFree86/Linux-x86_64/256.53/README/installdriver.html")
Thanks for Your time, I really appreciate it:>

---

### Post by andrewthomas on 2010-10-08
Glad you got it sorted out.  Could you mark the thread as [SOLVED]?

---

### Post by febro on 2010-10-08
oops, sorry bout that :D
marked it now :D

---

