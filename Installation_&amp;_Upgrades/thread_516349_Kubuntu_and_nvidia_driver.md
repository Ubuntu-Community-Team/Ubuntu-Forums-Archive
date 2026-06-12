---
title: "Kubuntu and nvidia driver"
date: 2007-08-03
forum: Installation &amp; Upgrades
---

### Post by Rumpty on 2007-08-03
Trying Kubuntu Feisty. AMD64 version.

How are you Kubuntu people managing to install the Nvidia driver? When I try to stop x, prior to installing the driver, with "sudo /etc/init.d/kdm stop", the Kubuntu logo appears on the screen for 30secs or so, then the screen goes black, with a flashing cursor, and that is all. No bash prompt.

I'm stumped at this stage. Any thoughts please?

---

### Post by dreadlord_chris on 2007-08-03
you need to switch to a different tty (virtual console) before stopping kdm:
Control-Alt-F1 thru F6 will switch you to tty1-tty6 - these are text-based (console) log ins
Control-Alt-F7 is reserved for X and is where kdm runs.
So,
Crtl-Alt-F1 to get to tty1
log in
```

sudo /etc/init.d/kdm stop

```
Now you can safely install the drivers

---

### Post by dabl on 2007-08-03
> **Rumpty said:**
> 
I'm stumped at this stage. Any thoughts please?


Yep --- Alt-F1.

Here's more: [http://kubuntuforums.net/forums/index.php?topic=3085112.0](http://kubuntuforums.net/forums/index.php?topic=3085112.0)

:guitar:

---

### Post by buzzmandt on 2007-08-03
here's how i do it, and i run kubuntu

```
sudo apt-get install nvidia-glx-new
```
```
sudo kedit /etc/X11/xorg.conf
```
if you don't have kedit sudo apt-get kedit
change driver "nv" to "nvidia"

done

---

### Post by dabl on 2007-08-03
If you have one of the new 8000-series cards, nvidia-glx-new does not have a driver new enough to run it.  In that case (if your card is 8xxx) you will need to either download and install the proprietary driver yourself, or download the Envy script installer and let it do the dirty work.  :)

---

### Post by Rumpty on 2007-08-03
> **dreadlord_chris said:**
> you need to switch to a different tty (virtual console) before stopping kdm:
Control-Alt-F1 thru F6 will switch you to tty1-tty6 - these are text-based (console) log ins
Control-Alt-F7 is reserved for X and is where kdm runs.
So,
Crtl-Alt-F1 to get to tty1
log in
```

sudo /etc/init.d/kdm stop

```
Now you can safely install the drivers

I did go through the Ctrl-Alt-F1 step, and then tried sudo /etc/init.d/kdm stop, but didn't "login". I will try that.

In any event, my procedure ended up with me booting into the "rescue" mode, and installing the downloaded driver from there. That was after installing "build-essential" and "lib6c-devel", after checking that make, gcc, linux-headers, pkg-config and xserver-xorg-devel were installed.

From what i have read on the forum, Envy doesn't go well with Kubuntu? 

Also, is nvidia-glx an alternative to the driver I downloaded and installed?

Thanks for your help everyone.

---

### Post by Pumalite on 2007-08-03
You did well for yourself, but I'm puzzled that your 'stop' command didn't leave you at the command line.???

---

### Post by dabl on 2007-08-03
> **Rumpty said:**
> 

From what i have read on the forum, Envy doesn't go well with Kubuntu? 

Also, is nvidia-glx an alternative to the driver I downloaded and installed?


No, Envy works great with Kubuntu.

nvidia-glx has one of the older driver versions -- I think it is -9631.

nvidia-glx-new has the next-to-last driver --- -9755

But you need Envy or the downloaded proprietary driver to get the latest 100.14.11, which is required for the 8000-series cards.

---

### Post by Rumpty on 2007-08-06
> **dabl said:**
> No, Envy works great with Kubuntu.

nvidia-glx has one of the older driver versions -- I think it is -9631.

nvidia-glx-new has the next-to-last driver --- -9755

But you need Envy or the downloaded proprietary driver to get the latest 100.14.11, which is required for the 8000-series cards.

After another install, and since I don't need the latest 100.14.11 driver, I used the nvidia-glx-new one. Much simpler. Some thrashing around in xorg to get a decent refresh rate (75Hz) but all is going well now.

And as you said earlier dabl, Alt-F1 was the final step I didn't take in the first place!

Thanks.

---

