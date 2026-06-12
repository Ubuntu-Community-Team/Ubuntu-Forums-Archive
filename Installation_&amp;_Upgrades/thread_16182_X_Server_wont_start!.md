---
title: "X Server wont start!"
date: 2005-02-19
forum: Installation &amp; Upgrades
---

### Post by cdhotfire on 2005-02-19
I finished installing Ubuntu, after that it starts to go in, and it says X server crashed.  I have a ATI Radeon 9200 Video Card.  I was able to set it up, by doing a:
```

dpkg-reconfigure xserver-xfree86

```
then i try:
```

startx 

```
and it keeps saying theres an error. Any ideas?

any help will be appreciated.

---

### Post by grj on 2005-02-19
Does it give a specific error or just the error in your title? Look in /var/log and you will see log files for X. Check them for more details and post them here if you do not figure it our on your own.

---

### Post by cdhotfire on 2005-02-19
how do i do that?
i cant log into my computer, because of this.
I guess is kind of like this one
[http://www.ubuntuforums.org/showthread.php?t=15556](http://www.ubuntuforums.org/showthread.php?t=15556)
but i already have the latest x-window-system-core.

---

### Post by spartas on 2005-02-20
After it gives you the error, press Ctrl+Alt+F1 to switch to a text console then log-in there. You won't have your graphics subsystem up (because of the error), but you will be able to use the shell to browse to /var and check out the logs.  I don't know how well you know linux commands/progams, but you can use cat from the shell and view the log.

---

### Post by Cyhatch on 2005-02-20
[QUOTE=cdhotfire]Any ideas?[/QUOTE]
I suggest you copy the */etc/X11/XF86Config-4* file from the LiveCD (if you have one) to your HD version of it. Restart.

=====

In my case (ATI Radeon 9800 Pro), this didn't help much (got 60Hz in any case). This is what I did.

From the shell (as *spartas* suggested):

Switch to */etc/X11/*: ```
cd /etc/X11/
```
**Back up**: ```
sudo cp XF86Config-4 XF86Config-4.bak
```
Edit the config: ```
sudo vi XF86Config-4
```

In vi, *INSERT* to switch modes, *CTRL+C* to exit editing mode, *:save XF86Config-4* to save, *:quit* to quit ;-).

So, in the config, I changed the *vesa* driver in the videocard section to *radeon*. (Kind of weird that *radeon* wasn't listed in that X-configuration thingy.) Changing the driver to *ati* didn't help me, but it might help you.

---

### Post by cdhotfire on 2005-02-20
i already configure the ati video card, like i said.  One thing i can say is that the error said, that there was no screen found:

No device recognized
(EE) No screen found

Something like that.

---

### Post by Cyhatch on 2005-02-20
Well, there was something [here](http://ubuntuforums.org/showthread.php?t=13219).

---

### Post by cdhotfire on 2005-02-20
i think mouse is okay, the only error, i found was the screen one. Which would mean its not recognizing something about my video card.

---

### Post by cdhotfire on 2005-02-20
also, about the alt-f1 stuff, i have a wireless keyboard and my "f" keys dont work.

---

### Post by p!=f on 2005-02-20
It's CTRL+ALT+F1 if you want from GUI to the console.
When you start startx, paste the errors you get here. Also, check for appropriate packages installed:
* xorg-driver-fglrx - Video driver for ATI graphics accelerators
* fglrx-control - Control panel for the ATI graphics accelerators
* linux-restricted-modules-k7 (replace k7 with your architecture, i686, i386, ...)

Place your XFree86 conf and lspci output here (put within [ code ] and [ /code ] so it's easily readable).

---

### Post by cdhotfire on 2005-02-20
seems, ubuntu is down, so this is gonna have 2 wait. :-|

---

### Post by cdhotfire on 2005-02-20
looks like Ubuntu is back on.  So, i just entered with vesa, but i still need to configure my Radeon, because whats the use of having it if im not gonna use it :-s . Any instructions out there to configure it?

---

### Post by cdhotfire on 2005-02-21
Can anyone tell me where to find instructions on how to configure my ATI Radeon 9200?

---

### Post by BiGBuG on 2005-02-21
I had similar issue and I've solved it.

I've installed with apt-get 

- XOrg server 
- xorg-driver-fglrx
- xorg-driver-fglrx-dev

I've launched 

fglrxconfig 

and after

dpkg-reconfigure xserver-xorg 

finally I've installed Xorg fonts and launched startx command

I'm a newbie and this is my first experience with linux, but I hope this will be usefull for you

---

### Post by cdhotfire on 2005-02-21
i forgot to mention im using warty, not hoarty, srry. But thanks for trying to help though. :grin:

---

### Post by poofyhairguy on 2005-02-21
[QUOTE=cdhotfire]Can anyone tell me where to find instructions on how to configure my ATI Radeon 9200?[/QUOTE]

[http://dri.freedesktop.org/wiki/DRI](http://dri.freedesktop.org/wiki/DRI)

I pretty sure your card works out of the box. Installing the "official" ATI drivers will screw you. Your card is the last ATI card to have GPL drivers. Use them instead.

---

### Post by BiGBuG on 2005-02-21
[QUOTE=cdhotfire]i forgot to mention im using warty, not hoarty, srry. But thanks for trying to help though. :grin:[/QUOTE]
I'm using hoary  :-|

---

### Post by cdhotfire on 2005-02-21
poofyhairguy, i configured it like i said before, it looked like it recognized it, but then after i finished configuring it, and put startx.  It says no device recognized, (EE) No screen.  So i had to start with vesa for the mean, time.

---

