---
title: "Installation error but with no Error"
date: 2005-03-31
forum: Installation &amp; Upgrades
---

### Post by xKevin on 2005-03-31
I'm on a quest to find a nice distro to run on an old Thinkpad 600X. I've had no problems with Fedora or Vector but ubuntu seems very picky. I installed it early this afternoon without a problem, however I could never get passed the login screen. It would ask for user name, then password, then the screen would go to a blank brown showing only the mouse. What scared me a little was the laptop made a weird sound, almost as if the hdd was clicking. I restarted the system and tried again, with the same results. I ended up removing ubuntu and installing Vector to see if the hdd crapped out or not. Fortunately Vector installed successfully with no problems. 

Here's the kicker, while I was installing Vector, I downloaded Ubuntu Live since a friend of mine kept telling me how much he liked it. I popped it into the laptop and the damn thing wouldn't load! Almost the same exact problem except Live lacks a login screen. All that is available is a brown screen and a moveable mouse cursor. Thinking the CD was bad, I popped it into my desktop and BAM, it worked flawlessly. 

I've tried searching (probably not hard enough) for a solution but wasn't able to find any. The only thing I can think of that may pose a problem is the absence of a working battery. (Old laptop + original battery = you're nuts if you think its still alive ;) ) 

Any ideas?

---

### Post by xKevin on 2005-04-01
Update:

The clicking noise isn't the hdd, it comes from the speaker (which is above the hdd bay). Unfortunately nothing seams to work. The login screen shows perfectly, but after that, nothing, it just hangs.

---

### Post by xKevin on 2005-04-02
PROBLEM RESOLVED

I had to disable acpi? during the install and everything worked perfect.

Thanks to those that alteast read my thread... ;)

---

### Post by jolla on 2005-04-09
[QUOTE=xKevin]PROBLEM RESOLVED

I had to disable acpi? during the install and everything worked perfect.

Thanks to those that alteast read my thread... ;)[/QUOTE]
 Hi!
Exactly the same problem, both the  live CD and the install version won´t work.   though in my case it did´nt helped to disable acpi...

could it be my nvidia GeForce 6800LE?
I also have trouble with my wireless keybord (microsoft...) its a swedish keyboard (some special keys?),  in teminal mode ubuntu complains about me have to "set keycode"

so, please help me? I hate my Windows-XP and want do do the switch to Linux!

Amd64
asus K8N

---

### Post by Oam on 2005-04-10
[QUOTE=xKevin]PROBLEM RESOLVED

I had to disable acpi? during the install and everything worked perfect.

Thanks to those that alteast read my thread... ;)[/QUOTE]

How/where did you disable acpi? In linux boot or in BIOS?

---

### Post by xKevin on 2005-04-10
[QUOTE=Oam]How/where did you disable acpi? In linux boot or in BIOS?[/QUOTE]
 Its one of the boot parameters. When you get to the boot screen, go into help and its listed as an option. I think it was in the screen that pops up when F5 is pressed...

---

### Post by Oam on 2005-04-10
[QUOTE=xKevin]Its one of the boot parameters. When you get to the boot screen, go into help and its listed as an option. I think it was in the screen that pops up when F5 is pressed...[/QUOTE]
 Ok, I tried the pci=noacpi kernel parameter too but it didn't help :( I hope I don't have to reinstall becuase of this. I already installed a 686 kernel from safe mode and some other apps :) 

Related to this problem: the system seems to stall if I choose either of the Language or Session options in the logon screen. They both produce a white box with no text in them. After that nothing responds anymore, except mouse. Could it be gfx driver issue? Or then just acpi...

---

### Post by jolla on 2005-04-11
[QUOTE=Oam]Ok, I tried the pci=noacpi kernel parameter too but it didn't help :( I hope I don't have to reinstall becuase of this. I already installed a 686 kernel from safe mode and some other apps :) 

Related to this problem: the system seems to stall if I choose either of the Language or Session options in the logon screen. They both produce a white box with no text in them. After that nothing responds anymore, except mouse. Could it be gfx driver issue? Or then just acpi...[/QUOTE]
 Oam, I tried the same thing with the same result.  :-(
We need HELP!!

---

### Post by Oam on 2005-04-11
Hi! I found a solution for me. It is in this thread:
[http://ubuntuforums.org/showthread.php?t=25487](http://ubuntuforums.org/showthread.php?t=25487)

But basically: it was the nvidia display driver and xorg.conf settings. There is a huge thread down at nvidia's forums about this bug too. More here:
[http://ubuntuforums.org/archive/index.php/t-24703.html](http://ubuntuforums.org/archive/index.php/t-24703.html)

---

