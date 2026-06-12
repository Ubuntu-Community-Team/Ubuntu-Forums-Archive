---
title: "Install new ati driver and update kernel (What works for me)"
date: 2007-06-02
forum: Installation &amp; Upgrades
---

### Post by fsando on 2007-06-02
These are the steps I've taken to have my ATI X1600 card working on my laptop under Ubuntu.

UPDATE 2007-06-04:
=== STEP ONE ===
(My guess is that this must always be done so that the connection to the restricted drivers/modules is established once an for all):
After freshly installed feisty (I followed the exact same steps in edgy)
Boot into recovery mode because the screen is unreadable otherwise (sudo is probably not necessary):
```
sudo apt-get update
sudo apt-get install linux-restricted-modules-$(uname -r)
sudo apt-get install xorg-driver-fglrx
sudo depmod -a
sudo aticonfig force --initial
sudo aticonfig --overlay-type=Xv
```
And then edit /etc/X11/xorg.conf (this step can wait till after reboot into normal gui mode)
```
Section "Extensions"
	Option "Composite" "Disable"
EndSection
```
Then a reboot

=== STEP TWO ===
Updating to the latest driver
(I guess this must be done every time a new kernel or a new driver is installed)
1) Download driver from amd/ati web-site
2) boot into recovery mode, browse to folder where atidriver is downloaded
(perhaps the easiest is to download to 'home')
If downloaded in home, browsing is:
```
cd /home/<your login name>
```
3) Install the driver (I believe this step prepares more than actually installs). Run command, follow instructions (important part is './' the rest should be name of latest download)
```
 ./ati-driver-installer-8.37.6-x86.x86_64.run
``` 

4) rebuild driver/kernel modules (? not sure exactly what this does). These steps were also taken after the last kernel update. So they appear to be necessary both for kernel update and for driver update.
```
module-assistant prepare
module-assistant update
module-assistant build fglrx

```
5) configure the driver/card
```
aticonfig --initial
aticonfig --overlay-type=Xv

```
6) Reboot
```
shutdown now -r
```

---

### Post by Nikos.Alexandris on 2007-06-03
I followed the official ATI installation instructions... and it worked!

(Samsung R20 laptop with ATI 1250 IGP)

[https://a248.e.akamai.net/f/674/9206/0/www2.ati.com/drivers/linux/linux_8.37.6-inst.html](https://a248.e.akamai.net/f/674/9206/0/www2.ati.com/drivers/linux/linux_8.37.6-inst.html)

...following the automatic installation option.

P.S. Beryl does not work correctly of course... (no window titlebars!) :(

---

### Post by Nikos.Alexandris on 2007-06-03
And again... it doesn't work anymore!!! I didn't really touch anything.

GDM starts but crashes and brings me back again into the login screen...

What is up?

---

### Post by fsando on 2007-06-04
> **Nikos.Alexandris said:**
> And again... it doesn't work anymore!!! I didn't really touch anything.

GDM starts but crashes and brings me back again into the login screen...

What is up?

Hi Nikos - I'm sorry I don't know. But there may be more then one issue (there often are). 

One: you may need to do the module update part (see above), or the kernel you use may not be supported - as an example: I use the 'low-latency' kernel that comes with feisty - I had to do the module update to use it.  I would like to use the 'real-time' kernel instead, though. So I installed it and tried to boot into it, I don't recall the exact result except that I dropped it immediately - it either gave me an unreadable screen or a very slow performance. 

There have been a lot of issues with the kernels in Feisty - you may be a victim of one of those issues.

You may need to update your bios (I had to with my old laptop).

Yet another issue is with Beryl: On the beryl site they explicitly advice against the version that comes with feisty and advice you to use rc3 from their site (repositories) instead.

Lastly you may have 'fiddled with the wrong things' - it may be easier to do a complete reinstall. I had to go through a few reinstall cycles myself before my system began to 'behave'. That has actually been the same experience I have had with every new version of windows (used it since 1994) - you do quite a few cycles before you begin to know the process. Good thing is that an Ubuntu install takes about an hour, a window install takes the better part of a week (drivers and software included)

---

### Post by Nikos.Alexandris on 2007-06-04
Thank you for your reply.

Jet2230 re-installed also feisty and has no problem any more (...he owns also a 1250 IGP graphic card I think) (>>>look here [http://ubuntuforums.org/showthread.php?p=2780078#post2780078](http://ubuntuforums.org/showthread.php?p=2780078#post2780078)).


I just want to try again to re-install manually the driver or remove beryl completely or... ?

After that I will give it a shot.

---

