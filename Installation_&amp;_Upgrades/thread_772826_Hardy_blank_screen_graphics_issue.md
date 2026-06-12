---
title: "Hardy blank screen graphics issue"
date: 2008-04-28
forum: Installation &amp; Upgrades
---

### Post by JoCoProductions on 2008-04-28
Hey guys just installed Hardy here, I had troubles with the live cd install because the screen would go black constantly so I used the alternate cd and it worked flawlessly. But when I boot up my linux partition for the first time it goes to the Ubunutu loading splash screen, then the screen goes black except for a short row of pixels at the top of the screen?

Any fixes to this?

---

### Post by 00arthuryu on 2008-04-28
what kind of graphics card/adaptor have you got?
and can you print the output of your /etc/X11/xorg.conf file?

---

### Post by JoCoProductions on 2008-04-28
I have a very basic Nvidia Geforce 6800 which I would assune many people own and can run ubuntu. I have no clue how to print out the output of my Xorg.conf, if you showed me how I'm sure I could.

---

### Post by JoCoProductions on 2008-04-28
Soooooooo confused....

---

### Post by Rocket2DMn on 2008-04-29
Assuming you can get into the GUI at all, have you tried installing the restricted drivers with EnvyNG - [http://albertomilone.com/envyngfaq.html#A](http://albertomilone.com/envyngfaq.html#A)

---

### Post by JoCoProductions on 2008-04-29
> **Rocket2DMn said:**
> Assuming you can get into the GUI at all, have you tried installing the restricted drivers with EnvyNG - [http://albertomilone.com/envyngfaq.html#A](http://albertomilone.com/envyngfaq.html#A)

I can't get into the GUI at all is the problem. I know it is somthing with my Nvidia drivers, but the problem occurs just as the login screen comes up (I know because when I type my username hit enter then password and hit enter the ubuntu boot sound rings in my speakers). Is there some sort of safe boot I can do where the graphics are restricted so I can install EnvyNG?

---

### Post by Rocket2DMn on 2008-04-29
OK, reboot into the recovery mode kernel from GRUB, it's the second option.  That will drop you at a root terminal.  Run
```
dpkg-reconfigure xserver-xorg -phigh
nano /etc/X11/xorg.conf
```
Now you are in a text editor, use the arrows to move around and change the part that says
```
Section "Device"
     Identifier "Configured Video Device"
EndSection
```
to
```
Section "Device"
     Identifier "Configured Video Device"
     Driver "vesa"
EndSection
```
All I did was add the Driver line - this should force X (the GUI software) to load in safe graphics mode.  Do CTRL+X to get out and accept saving changes to the file.  Now run
```
reboot
``` and let it load up normally.  You should be able to login now, at which point you can download EnvyNG and install the restricted drivers based on the link I posted above.

---

### Post by JoCoProductions on 2008-05-01
Thanks SOOOO much, finally got into the GUI but in a low resolution mode (800x600) and no graphics quite yet.

The next problem Im having is with EnvyNG when I auto detect my Nvidia driver to download it outputs this for me:
```
objects.nvidiainstallg(data1)
  File "/usr/lib/python2.5/site-packages/Envy/objects.py", line 84, in nvidiainstallg
    task.nvidiaInstall()
  File "/usr/lib/python2.5/site-packages/Envy/classes.py", line 1076, in nvidiaInstall
    check.checkntry(packages)
  File "/usr/lib/python2.5/site-packages/Envy/classes.py", line 306, in checkntry
    raise Exception(error)
Exception: ('\nEnvyNG ERROR: The following packages cannot be installed:',)
```

I have no clue what to do.....

---

### Post by JoCoProductions on 2008-05-01
This also...


```
/usr/lib/python2.5/site-packages/apt/__init__.py:18: FutureWarning: apt API not stable yet
  warnings.warn("apt API not stable yet", FutureWarning)

```

---

### Post by Rocket2DMn on 2008-05-01
I have no idea what that means either.  Sounds like something may be wrong with EnvyNG or your python (though unlikely).  I would try reinstalling EnvyNG, otherwise can you enabled restricted drivers from System->Administration->Hardware Drivers?

---

### Post by JoCoProductions on 2008-05-01
It says it is enabled, and that is before I did anything to it. But it also says that it is not in use and has a red sphere next to it.

---

### Post by harecanada on 2008-05-01
Hi.
I did this

sudo aptitude install kubuntu-desktop

 and Ubuntu came up after a long download and then a reboot. It is working great. Only problem is I wanted Kubuntu
Now I'm trying to switch to Kubuntu.

---

### Post by JoCoProductions on 2008-05-01
> **harecanada said:**
> Hi.
I did this

sudo aptitude install kubuntu-desktop

 and Ubuntu came up after a long download and then a reboot. It is working great. Only problem is I wanted Kubuntu
Now I'm trying to switch to Kubuntu.

Why would I download Kubuntu??? Do you have any idea of what your talking about?

---

