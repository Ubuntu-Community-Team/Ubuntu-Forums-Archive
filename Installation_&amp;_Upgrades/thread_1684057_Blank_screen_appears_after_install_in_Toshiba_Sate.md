---
title: "Blank screen appears after install in Toshiba Satellite L655"
date: 2011-02-08
forum: Installation &amp; Upgrades
---

### Post by nalakau on 2011-02-08
I've installed ubuntu 10.10 in my Laptop alongside with windows 7. When the time of restarting I got a black screen after Grub. It was great when I tried with live CD. Following are my configuration;

Toshiba Satellite L655
Intel i5
3GB RAM
ATI Graphics card.

---

### Post by sikander3786 on 2011-02-08
Is this a proper dual boot or Ubuntu is installed inside Windows using Wubi?

When you see the Grub menu, highlight the Ubuntu entry and press 'e' to edit it. Using arrow keys, navigate to words "quite splash", delete them and type "nomodeset" in their place (without quotes). Press Ctrl + X to continue boot. Can you see the desktop now?

If that doesn't help, reboot and repeat the process. Just replace nomodeset with radeon.modeset=0 and see if that helps.

[http://ubuntu4beginners.blogspot.com/2011/01/ubuntumaverick-blank-screen-problem.html](http://ubuntu4beginners.blogspot.com/2011/01/ubuntumaverick-blank-screen-problem.html)

---

### Post by nalakau on 2011-02-08
This is a proper dual boot. I replace the "quite splash" with "nomodeset" now it is appeared in DOS mood as nalaka@karmickoala:~$

---

### Post by SleyFu on 2011-02-08
I'm guessing you logged in with your username and password, so all you should have do to now is type in "startx" and hit enter to reboot.

In the upper-right of the desktop, click the Additional Driver's icon (looks look a pci card) and update the graphics card driver.  Or, in upper-left of desktop, click on System > Administration > Additional Drivers and update the graphics card driver.

Hope that helps.

---

### Post by nalakau on 2011-02-08
still no chance of seeing the desktop. with various other informations it says;

(= =) Log file: "/var/log/Xorg.0.log"
(= =) Using config file: "/etc/x11/xorg.conf"
(= = ) Using system config directory "/usr/share/x11/xorg.conf.d"
(EE) Failed to load module "fglrx" (module does not exist, 0)
(EE) No drivers available

Fatal server error:
no screens found



xinit: No such file or directory (errno 2): unable to conect to X server
xinit: No such process (errno 3): Server error

---

### Post by nalakau on 2011-02-09
I have tried again running with live CD & in additional drivers I found that 
ATI/AMD proprietary FGLRX graphics driver

Any chance of getting my laptop up & running?

---

### Post by heath_r on 2011-02-09
I had a similar issue with L655-S5155 and 10.10 64 bit. 
After apparent successful install, no X - blank screen or cui. 
Solution: 
Reboot
hold shift key
choose recovery mode in GRUB
Go to update manager and update
Reboot
X should now be good.

---

### Post by nalakau on 2011-02-09
In Recovery Menu there are;

Resume normal boot
Try to make free space
Repair broken packages
Run in failsafe graphic mode
update grub boot loader
Drop to root shell prompt with networking
Drop to root shell prompt

from this menu which one I have to select. I have tried the following;

Run in failsafe graphic mode
Update grub boot loader
Repair broken packages

but so far no chance. Further after all these things in command promt always appear as
nalaka@karmickoala:~$ 	

What I should do to go out from this. what I usually do is press the restart button & restart the machine.

---

### Post by amsterdamharu on 2011-02-10
When you boot as normal and end up with the command line you could try to update there. This usually works when you have cabled internet as wireless takes some tweaking to work without gnome.

Try the following commands:

```
sudo apt-get update
sudo apt-get upgrade
```

update gets the newest available packages and upgrade updates all the packages.

If that's finished you can try the following command:

```
sudo jockey-text
```

That might detect and install drivers for your card.

---

### Post by nalakau on 2011-02-10
I have done everything so far no chance it says;

GtkWarning: could not open display

---

### Post by amsterdamharu on 2011-02-10
> GtkWarning: could not open display

That's the first time I see jocky-text and apt-get give output like that. Are you sure you typed the right command?

---

### Post by nalakau on 2011-04-18
Hi, Sorry for taking solong time to reply. Yes I typed it correctly but no chance of seeing. Anyway I installed as wubi & it's working perfectly.

---

