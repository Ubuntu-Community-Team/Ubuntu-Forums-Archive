---
title: "GUI Problems, Looking for Help!"
date: 2009-12-18
forum: Installation &amp; Upgrades
---

### Post by alexpking on 2009-12-18
I have a bunch of machines I imaged with ubuntu 9.10 and I can turn them go into the recovery console drop to the net root cli run the command ```
startx
``` the GUI comes up from the GUI I can restart the machine and everything is all good, restarts and all. BUT if I power down the machine I have to go back in the recovery console and run the comman all over again.
Please help!

---

### Post by shredder12 on 2009-12-19
If you are dropped to the console when you switch on your system then i think the problem is that X server is probably not set to start at boot.

---

### Post by alexpking on 2009-12-20
Ok, thats what I though, so I looked in initng, and inttab and they are both black ubuntu 9.10 doesnt use inittab anymore correct? And are you sure you think its just not set to start cause I am not getting dropped to the command line Im just getting a blank black screen after the splash screen

---

### Post by shredder12 on 2009-12-20
I am a little confused here..
Are you trying to start the GUI (using startx) by booting into the recovery mode?

---

### Post by joes7 on 2009-12-20
Set XServer to start at boot.

---

### Post by alexpking on 2009-12-20
If the machines gui does not come up automatically, I have to restart go into the recovery console and then run startx restart and its all good if I SHUTDOWN I have to go back into the recovery run startx and then restart. If I shutdown it loads grub loads the splash screen after the splash screen fades it then just goes to a blank black screen.

---

### Post by alexpking on 2009-12-20
Ubuntu 9.10 uses upstart to schedule these events and it should be placed in the inittng file correct?

---

### Post by shredder12 on 2009-12-20
Startx should automatically start the GUI. You don't need to restart the system. If its working then its indeed a weird solution ;).
And its a bit strange because if Xserver is not set to start at boot then you should be dropped into a text-mode login rather than a blank screen..
I am not really sure of the solution right now... but my bet would be on reinstalling the Xserver (but you should wait nd look for some simple fix).

> Ubuntu 9.10 uses upstart to schedule these events and it should be placed in the inittng file correct?

I don't know..

---

### Post by alexpking on 2009-12-20
Thats what makes this the strangest problem I have ever had, follow me on this one.
I turn on the machine it loads I get the splash screen, splash screen fades, and then its just a black screen nothing on it just a black screen, the monitor does NOT go into power save mode, so its recieving a signal that says "show a black screen?"
I restart the machine go into the recovery mode run startx the gui comes up, from the gui I RESTART and that following boot the gui loads up by itself. It seems all good, I can restart again, and again, and again, and its all good. BUT if I SHUTDOWN its all lost.

---

### Post by shredder12 on 2009-12-20
have you tried using ctrl-alt-f1 to go into the text mode when you are at blank screen..
may be you can then try running startx from the login..

And here is another weird solution.. the next time you boot into Ubuntu remove the splash screen.. this way it will boot by printing all the messages and in case this happens again you can tell where exactly things went wrong..

---

### Post by alexpking on 2009-12-20
Ok, ctrl+alt+f1 doesnt seem to get me anywhere...maybe the machine is hanging? And as far as removing the splash screen that would be located inside the /boot/grub/menu.lst folder right? I ask because I dont seem to have a menu.lst folder, is it named something different in 9.10?

---

### Post by shredder12 on 2009-12-20
I think you can manage this using the start up manager...
I don't remember whether its pre-installed or you will need to install it.. 
look in System->administration->Startup manager..

if its not there install it
```
sudo apt-get install startupmanager
```

---

### Post by alexpking on 2009-12-20
Alright! Ok I am not sure which culprit it may be, I am leaving for the day I will be back monday mid-morning but...
I tried to install the startup manager and I was recieveing the E: package not found.....error, since this is an image for a domain install I disabled all the updating for ubuntu. So I went into the softwares sources re-checked all the boxes when back into the terminal installed the startup manage. Used the startup managae to set the time out from 10 seconds to 20 seconds, disabled the splash screen and enabled show text during startup (the splash screen still was there, and the text didnt show up???) but. After a SHUTDOWN the login page actually did come up after the splash screen! Success! I will narrow it down on Monday to which is the exact soloution. My money is riding on the time out, because when I did enable all the updates on the machine, there were none to be loaded, the image I built is super fresh, no updates were installed. And I had read an article about on machines that were underpowered as far as processors and memory were concerned had problems loading X and eventually having it crash on them.
 
Major kudos to shredder12!

---

### Post by shredder12 on 2009-12-20
Well, even I am not sure about the culprit but I will put my money on the non-updated system... Even though I haven't faced or heard this kind of problem but lets hope its solved for now..

> Major kudos to shredder12!
I just love it when people say that.. :D

---

