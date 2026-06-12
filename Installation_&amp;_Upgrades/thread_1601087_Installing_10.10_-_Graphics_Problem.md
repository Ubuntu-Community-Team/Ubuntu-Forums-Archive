---
title: "Installing 10.10 - Graphics Problem"
date: 2010-10-19
forum: Installation &amp; Upgrades
---

### Post by chetkgp on 2010-10-19
Hi All,

The live Ubuntu 10.10 cd works fine on my laptop
and is able to detect and configure my graphics card.
But the installation of Ubuntu on my laptop fails to do so.

Is there any way to obtain the same graphics settings from
 the live cd to the installed Ubuntu.

---

### Post by tommcd on 2010-10-19
What graphics card do you have?
If you have a nvidia or ati card, have you installed the proper drivers (system > administration > hardware drivers) for your card?

Did you install Ubuntu inside Windows using Wubi? Or is this a real install to a linux partition on your hard drive?

---

### Post by chetkgp on 2010-10-20
My laptop has Intel's P6100 processor and
my graphics card shows

00:02.0 VGA compatible controller: Intel Corporation Core Processor Integrated Graphics Controller (rev 02)

Does Intel provide a driver for Linux for this chip ?

---

### Post by chetkgp on 2010-10-20
I did a fresh installation of Ubuntu not Wubi

---

### Post by tommcd on 2010-10-20
> **chetkgp said:**
> 
Does Intel provide a driver for Linux for this chip ?
Ubuntu already includes the intel graphics driver.
Are you able to get to the graphical desktop at all after installing Ubuntu 10.10? Or is it a problem with not getting the proper resolution for your monitor? What exactly happens when you boot to the desktop?
If you can not get to the graphical desktop, then boot to recovery mode and choose the option **xfix fix video** (or whatever it says exactly). Then reboot.
If that does not work, then try adding **i915.modeset=1** or **i915.modeset=0** to the kernel line when booting Ubuntu. This will disable the kernel mode setting for intel graphics.

---

### Post by chetkgp on 2010-10-24
After the 10.10 installation when I rebooted the laptop, gdm was unable to start.
I just a got a text mode login window.

I then added an xorg.conf file with a vesa driver and did a startx. This got me
a GUI with a bad resolution. Also it periodically logged me out of the GUI.

I have tried the booting with the  i915.modeset=1 turned on but that fails to 
solve the problem.

---

### Post by tommcd on 2010-10-26
You can also try booting with the boot option **i915.modeset=0**.
Also, instead of trying to start the GUI with **startx**, try running:
```
sudo service gdm start
```
What specific intel graphics chip does your laptop have?

---

### Post by bertiebaggio on 2010-10-26
Edit: never mind, OP was the same person as ([http://ubuntuforums.org/showthread.php?p=10027685]("http://ubuntuforums.org/showthread.php?p=10027685")).

---

### Post by Clodzilla on 2010-10-26
Tommcd,
  I have the same problem and tried the 'sudo service gdm start' and get a black screen and no response.

I cannot find what type of graphics card I have. I looked in the Dell Setup menu, but found nothing. I am going to the Dell service site now to look the information up.

---

### Post by tommcd on 2010-10-26
> **Clodzilla said:**
> 
I have the same problem and tried the 'sudo service gdm start' and get a black screen and no response.
Is this a fresh install of Ubuntu? Or did you do a dist-upgrade from 10.04? How did you install Ubuntu?
> **Clodzilla said:**
> 
I cannot find what type of graphics card I have. ...
To find out what graphics card you have, run **lspci** like this:
```
lspci | grep -i vga
```
And post the output here.

---

### Post by hari_home on 2010-10-27
I have the same problem on ASUS K52f-BBR5
lspci shows
Intel Integrated graphics Rev. 18

CPU is Intel P6100 dual core.

Here is an update:
I tried 10.10 64-bit and finally I tried 10.04 32-bit.
10.04 32-bit worked perfectly. I will stick with this for now
so that I can avoid using Win 7.

I tried everything except HDMI output. That is next.

---

### Post by chetkgp on 2010-10-28
Tommcd,

I've tried the **i915.modeset=0 **and **i915.modeset=1 **kernel options. 
Both fail to give me a GUI. The screen goes blank in both cases.
Even manually starting gdm  from command line also fails.

My graphics controller is
00:02.0 VGA compatible controller: Intel Corporation Core Processor Integrated Graphics Controller (rev 02)

and my processor is Intel P6100.

---

### Post by tommcd on 2010-10-28
The only other thing I can suggest is to try booting with the boot option **xforcevesa**. This should force the use of the vesa driver. See this:
[http://ubuntu-tutorials.com/2010/05/06/ubuntu-10-04-lucid-blank-screen-at-startup-workaround/](http://ubuntu-tutorials.com/2010/05/06/ubuntu-10-04-lucid-blank-screen-at-startup-workaround/)
Note that that tutorial also mentions using i915.modeset=1 or i915.modeset=0, which you have already tried without success.

---

### Post by chetkgp on 2010-10-28
Tommcd,

The vesa display driver works. But it gives me a lower resolution
and also for some reason I  keep getting logged off every minute or so.

---

### Post by tommcd on 2010-10-29
> **chetkgp said:**
> 
The vesa display driver works. But it gives me a lower resolution
and also for some reason I  keep getting logged off every minute or so.
The vesa driver is the fail safe driver for all linux graphics cards. It has limited capabilities though. That may explain the lower resolution.
Are you getting logged out of Ubuntu? Or do you mean the X server is crashing?
I don't know what else you could do to get better graphics at this point.

---

### Post by itchy8me on 2010-11-07
i have been having this problem since changing my monitor from a 21 inch to a 23 inch, i think it has somehting to do with resolutions. and indeed, defaulting to the vesa driver or deleting xorg solves the problem with the side effect of having to live with a lower screen resolution.

---

### Post by itchy8me on 2010-11-08
> **itchy8me said:**
> i have been having this problem since changing my monitor from a 21 inch to a 23 inch, i think it has somehting to do with resolutions. and indeed, defaulting to the vesa driver or deleting xorg solves the problem with the side effect of having to live with a lower screen resolution.


Reconnecting the 21 inch returned the system to a working state (after deleting xorg.conf). I then ran nvidia-xconfig, rebooted and after logging into x i reconnected the 23 inch, i then get a resolution of 1680x1050, slightly higher than 800x600. if i now reboot again then the story starts from the beggining.

i also tried modifying metamodes in xorg.conf, but no dice.

running xconfig with the 23 inch connected, gives a rather bare looking xorg.conf ..strange.

---

### Post by itchy8me on 2010-11-09
well.. i have now disconnected monitor from the DVI cable and connected it via a standard VGA cable it now works with the proprietry drivers at full res.

hope this helps someone.

---

