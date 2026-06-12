---
title: "Ubuntu 12.10 Wubi installation problem"
date: 2013-01-01
forum: Installation &amp; Upgrades
---

### Post by javacookies on 2013-01-01
Hi,

I really want to try the latest version of Ubuntu on my new Rig. I'm installing it through Wubi coz it's the easiest way. The problem is it won't continue installing. It always stops to a certain process while installing. It's something like Kernel_thread_helper and my video card's fan spins a bit faster than it should be since I'm just installing. I even tried to set iGPU as my default display and I smiled when I saw progress saying "Almost finish copying files"...something like that. Unfortunately, it still won't continue. 
Here's my specs: 
intel i5 3570k@3.4Ghz 
Asus V-LK
Asus HD 7870 
8GB RAM

Thanks for any help :D

---

### Post by Frogs Hair on 2013-01-01
Does the installation get past the point were it is done expanding ? Sorry, I don't remember the order. I know it is possible to finish an installation that pauses while the files are being configured.

---

### Post by javacookies on 2013-01-01
What do you mean expanding? It stops in about 80% of the loading bar. It takes too long so I tried opening something from the menu like System Settings and that's where my PC hangs completely. Or could t just be me being impatient? It stays in the spot of the loading bar for about 10 minutes or more.

EDIT: it's about 70-75% not 80% :D

EDIT2: I tried all alternatives such as graphic-fail mode and acpi workaround. The only difference is it shows "Almost finished copying files". However I found these lines which I think the ones delaying the installation.
-jbd2/loop2-B:9340 blocked for more than 120 seconds
-Ext4lazyinit:9342 blocked for more than 120 seconds

From my observation, those two repeat multiple times with some more lines of commands after each.

---

### Post by Frogs Hair on 2013-01-01
After the installer is finished downloading  there is a restart prompt and the files expand and I think the next step is copy. There is a message that tells you the the files are expanding.

When you say progress bar I assume you are describing the one that appears after booting into Ubuntu and not the Wubi .exe download progress bar.

---

### Post by presence1960 on 2013-01-01
hopefully you aren't trying to install wubi on windows 8 booting from UEFI mode. It won't work, at least last time I checked it didn't work.

---

### Post by javacookies on 2013-01-01
Yup, it's after the reboot already. It's during the actual installation.
BTW, I have Windows 7 SP1 64-bit. I tried the demo mode and it worked. Please help me I really want to try it :D

---

### Post by Frogs Hair on 2013-01-02
If you can get into TTY Ctrl + Alt + F1  you can try the following after entering the user name and password.  
```
sudo apt-get -f install

```

The command once helped me during a paused installation. Ctrl + Alt + F7 will return you to the GUI environment. Pay attention to any messages in the TTY after the command has been run.

---

### Post by javacookies on 2013-01-04
I tried your that command but it did nothing. It still won't continue :(
Maybe I have no choice but to install it in a dedicated partition...

---

### Post by presence1960 on 2013-01-21
> **javacookies said:**
> I tried your that command but it did nothing. It still won't continue :(
Maybe I have no choice but to install it in a dedicated partition...

wubi is not meant to be a permanent installation, but rather only a test drive to see if you like Ubuntu. I know a lot of people who try wubi intend on making it a permanent installation, until it messes up as it does frequently. Then they want miracles to fix their wubi install. Install to a dedicated partition and don't put off the inevitable is your best bet IMHO.

Here is a quote from an interview:

Sean: What do you think the impact has been of having something like Wubi available to Ubuntu? It’s somewhat unique, although there are obviously live CDs, and you can put a Linux distribution on a USB key. All of these things can accelerate early tryout and early adoption without requiring people to re-partition their drive.

On the other hand, particularly for users new to Linux, this might be a way for them to try it out for an extended period of time, whereas a live CD, as cool as that is, is inherently a temporary experience.

With Wubi, you could continue to use your files and access things in a Windows partition, in a way that’s analogous to Bootcamp on the Mac.

Agostino: Wubi actually wasn’t designed to do long-term installations. The main aim was really to let people try out Ubuntu with confidence. Normally, users that start with Wubi tend to upgrade to a full installation to a dedicated partition at the next release cycle.

To read the whole interview go here: [http://howsoftwareisbuilt.com/2009/03/12/interview-with-agostino-russo-wubi-ubuntu/](http://howsoftwareisbuilt.com/2009/03/12/interview-with-agostino-russo-wubi-ubuntu/)

---

