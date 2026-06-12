---
title: "[SOLVED] nVidia Graphics Problem with X"
date: 2007-08-02
forum: Installation &amp; Upgrades
---

### Post by karl_eller on 2007-08-02
**Problem has changed. See [My post below]("http://ubuntuforums.org/showpost.php?p=3129388&postcount=9") for the new proglem.**


[COLOR=gray]Ok, so I've got a fresh install of Ubuntu on a hard-drive, and all was going fine and dandy.
 
Untill, that is, I decided to activate some of the Desktop Effects. It came up with a prompt about activating the nVidia drivers for my card, I clicked OK, and it started downloading some stuff.
 
Once it was downloaded and installed, I rebooted the system. Booted back into Ubuntu, the splash screen with the load bar came up and loaded, but when it would have normally gone to the log-in screen, my monitor went black, then an error came up on the screen, something about X having failed to load, and asked if I wanted to see the output or whatever to try and debug.
 
The gist of the output was that the card nvidia0 (I think that's what it was called) failed to load, and that I should repare and then restart.
 
I figured it was a graphics driver problem, so I downloaded the latest Linux drivers from the nVidia website and installed them, but I'm still getting the same problem.
 
I also used 'apt-get install nvidia-gfx-new', but that didn't fix it either.
 
So what did I do wrong, and how do I fix it?
 
I'm not having great luck getting everything to work properly in Ubuntu so far...
 
*Edit:* My system specs is:
C2D E6300 (OCed to 2.1GHz)
2 gb PC5200 RAM
2x 160 GB SATA2 HDDs (1 has Vista, the other has Ubuntu)
1x 250 GB SATA2 HDD (personal data and games and what-not)
nVidia GeForce 8800GTX
 
Eller[/COLOR]

---

### Post by Pumalite on 2007-08-02
[http://ubuntuforums.org/showthread.php?t=432056&highlight=8800+GTX](http://ubuntuforums.org/showthread.php?t=432056&highlight=8800+GTX)

---

### Post by karl_eller on 2007-08-02
I followed that HowTo, however I was unable to edit the "[SIZE=-1]/usr/share/applications/NVIDIA-Settings.desktop", as I didn't have a GUI, and thus couldn't use gedit.

I restarted the system, and I've still got the same problem: X Server doesn't start properly (says it probably wasn't configured correctly), then I'm stuck with a command line.

Eller
[/SIZE]

---

### Post by Pumalite on 2007-08-02
If you have a command line, things are much better: sudo dpkg-reconfigure xserver-xorg
Say yes to most of defaults, but choose 'vesa' as your driver. That will get you in. Then think about getting a proprietary driver for your card.

---

### Post by karl_eller on 2007-08-02
I tried that, reconfigured the xserver, then restarted my system. Booted into Ubuntu, and then the same error I've been getting came up again.

And by proprietary driver, you mean the nVidia Linux drivers from the nVidia website, yes?

Eller

---

### Post by Pumalite on 2007-08-03
Yes. I think the last one supports your card.

---

### Post by merlinus on 2007-08-03
After reconfiguring the x server and choosing vesa, try this:

```

startx

```

rather than rebooting.

-merlin

---

### Post by Pumalite on 2007-08-03
How could I miss that???

---

### Post by karl_eller on 2007-08-03
**<NEW PROBLEM>**

So I got fed up with trying to fix my driver problem and did a fresh install of Ubuntu.

I then installed the nVidia 100.14.11 drivers from the nVidia website, and everything went fine. All the pretty graphical effects worked, and all was good.

That is, until I downloaded all the updates. After they were downloaded (all 177 mb of them, which took about 2-3 hours :-P), I restarted my system, and BAM! X Server wouldn't load.

The error output from X Server went a little bit like this:
```

Error: API MIssmatch: This nVidia driver has version 100.14.11 but the nVidia Kernel module's version does not match.
Please make sure that the kernel module and all NVIDIA driver components have the same version.

Failed to initialize NVIDIA kernel moduel! Ensure that there is a supported NVIDIA GPU in this system and that the NVIDIA device files have been created properly.

Please consult the NVIDIA Readme for details

Screen(s) found, but none have usable configurations

Fatal server error: No screens found

```

I did the
```

sudo /etc/init.d/gdm stop

```command, reinstalled the nVidia drivers, then started 'gdm' again. This worked again, until I rebooted my comp again, then it came up with the same error again.

I tried
```

sudo dpkg-reconfigure xserver-xorg

```after stoping 'gdm' which reset everything back to default, but I still didn't have any of the effects.

So, logged out, hit ctrl+alt+F1, stopped 'gdm', installed drivers again, started 'gdm', logged back in, everything worked fine again. Rebooted my comp, X Server error came up again.

So basically as long as I don't reboot my computer, I can get the nVidia drivers to work, but every time I reboot, X Server dies.

*Edit:* Updated the error message.

Eller

---

### Post by Pumalite on 2007-08-03
Every time you have a kernel update you have to install your proprietary driver again. It's inevitable. But the thing about rebooting your computer and having the same problem again is very strange. First time I hear of it and I don't know what to tell you or advise you. Hopefully somebody with more experience will jump in.

---

### Post by merlinus on 2007-08-03
Yeah, this can be a real pain.  I have a Matrox P650, so I have to re-compile the driver each time, not simply install it.

-merlin

---

### Post by karl_eller on 2007-08-03
running
```

sudo dpkg-reconfigure xserver-xorg

```
gets me a GUI again, but it won't run the Desktop Effects, and in Restricted Drivers Manager, the nVidia driver is disabled.

> **merlinus said:**
> Yeah, this can be a real pain.  I have a Matrox P650, so I have to re-compile the driver each time, not simply install it.

-merlin

Wouldn't running the NVIDIA-Linux-x86-100.14.11-pkg1.run file again re-compile the driver? Or would I need to first make sure that the driver was un-installed?

Eller

---

### Post by Pumalite on 2007-08-03
In my experience, I dont remove the old drivers because the driver from NVIDIA does that itself upon installation. I've seen people in this forum advising that you do that before installing though. Myself, I've never needed to do that. Take your pick. What you do need is 'build essential'(make,automake'autoconf,latest gcc, kernel-headers matching your kernel)

---

### Post by merlinus on 2007-08-03
> 
Wouldn't running the NVIDIA-Linux-x86-100.14.11-pkg1.run file again re-compile the driver? Or would I need to first make sure that the driver was un-installed?


IIRC, there is an option to overwrite the existing driver.  Also, you will want to make sure it is the latest one for whatever kernel you are using.

-merlin

---

### Post by karl_eller on 2007-08-03
I've tried uninstalling the nVidia drivers, auto-updating the .run file, and installing them again, but no luck. I'm still getting the same error message.

Eller

---

### Post by karl_eller on 2007-08-07
*bump*

So nobody knows how to fix this? I can still use Ubuntu and all, but I really would like having the graphics drivers working properly.

Or am I going to have to wait for nVidia to release new Linux drivers for my card?

Eller

---

### Post by Nkari on 2007-08-08
Have you tried using Envy as of yet? Got around my X Issues.

---

### Post by karl_eller on 2007-08-08
> **Nkari said:**
> Have you tried using Envy as of yet? Got around my X Issues.
Hmm, I just tried that now, installed everything, and it works! Comp has restarted, no problems.

Seems like everything is all good.

Cheers everybody.

Now lets see if I can figure out how to mark a thread as solved...

Eller

---

