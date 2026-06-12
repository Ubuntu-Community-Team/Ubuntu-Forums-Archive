---
title: "installing nVidia driver"
date: 2006-12-25
forum: Installation &amp; Upgrades
---

### Post by j.miller565 on 2006-12-25
I'm trying to install and enable my nVidia Driver on Ubunutu 6.10 (Edgy Eft), but when i try to enable it, it shows this

> 
sudo nvidia-glx-config enable

Error: unable to load nvidia kernel driver! Be sure to have installed
the nvidia driver for your running kernel.

when I try to find if my 3d accelerator is working it comes up like this
> 
 glxinfo | grep rendering

Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Error: couldn't find RGB GLX visual
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".

I'm not using the legacy driver. I've tried both and none seem to work.

I use a nVidia GeForce FX5200 128 MB card

what do I do if i want to enable it and install it so it works properly. Help would be greatly appreciated.

---

### Post by taurus on 2006-12-25
Did you remember to install "nvidia-glx" first???

---

### Post by j.miller565 on 2006-12-25
yea I have. Here's a screenshot of my nVidia drivers a installed on Ubuntu

---

### Post by j.miller565 on 2006-12-25
btw I've installed all updates for my computer except for the Open Office Update. I can't seem to download it

---

### Post by j.miller565 on 2006-12-25
what should I do now?

---

### Post by spockrock on 2006-12-25
sudo nvidia-xconfig

what happens when you do this?? also do you have the restricted modules installed??

---

### Post by j.miller565 on 2006-12-25
this is what happens:

> sudo nvidia-xconfig

Using X configuration file: "/etc/X11/xorg.conf".
Backed up file '/etc/X11/xorg.conf' as '/etc/X11/xorg.conf.backup'
New X configuration file written to '/etc/X11/xorg.conf'


and what are the restricted modules?

---

### Post by spockrock on 2006-12-26
restricted modules contain binaries that are need for say wireless cards or video cards.

what happens now when you reboot???

---

### Post by j.miller565 on 2006-12-26
it does some X server think but it fails. I'm using GRUB so when I click on Ubunutu 2.7... 386, it loads but then it goes to some X server thing which tells me it's failed. when i click get out of it I can't get into my Ubunutu Desktop. 

On the other hand, when I click on Ubunutu 2.7.......... generic It loads and before the desktop splash screen comes up, a nVidia screen pops up for 2 seconds. then the splash Screen comes up and I can log on to Ubuntu. the only problem is now the sound has gone. can you help me with the other issue and

---

### Post by spockrock on 2006-12-26
ok first the reason why when you boot the 386 image, it fails, is I assume that when you did sudo apt-get install nvidia-glx you were on the generic kernel, it did not install the 386 restricted modules, so you need to install the restricted modules for the 386 kernel.

As per the sound issue, I have no idea why that would happen, but in theory if the nvidia-glx package broke your sound you can try to uninstall them and see if that brings back your sound.

---

### Post by j.miller565 on 2006-12-26
sorry my bad. Sound is working fine now. so how do I get the 386 resticted modules?

---

### Post by spockrock on 2006-12-26
ok odds are if you are using edgy, and its upto day its just

sudo apt-get install linux-restricted-modules-2.6.17-10-386

if not then just do this... uname -r this will spite out your kernel version
I get this: 2.6.17-10-generic, :s so you might have to boot into the 386 kernel to find out but odds are, maybe its the same version as your generic kernel.

Also can I ask why you want to boot the 386 kernel over the generic?  generic should be faster as it sees your cpu and its optimizes for you cpu.

but thats how you should be able to do it.

---

### Post by j.miller565 on 2006-12-27
it works now but when i turn on my computer and go onto Ubunutu generic or 386, after the bar has finished getting Ubuntu ready, the splash screen doesn't come up. 
I have to reboot and then splash screen comes up on the second time. what should i do?

---

### Post by spockrock on 2006-12-27
that I am unsure about is it listed as a bug??

---

