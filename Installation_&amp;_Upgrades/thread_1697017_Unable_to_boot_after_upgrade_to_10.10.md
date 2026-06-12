---
title: "Unable to boot after upgrade to 10.10"
date: 2011-02-28
forum: Installation &amp; Upgrades
---

### Post by Mrs Twaddle on 2011-02-28
I updated my pc today, all went well no errors during upgrade. But I am unable to boot.
I get the splash screen with Ubuntu and 4 coloured dots, then it goes and i get a page of txt. 
*starting apparmor profiles
skipping profile in /etc/apparmor.d/disable: usr.bin.firefox
plymouthd: ply-keyboard.c:384: ply_keyboard_watch_for_input: Assertion `keyboard != ((void*)0)' failed.
*Setting sensors limits
rather than invoking int scripts through /etc/init.d, use the service (8)
utility, e.g service s20plymouth-splash start
Since the script you are attempting to invoke has been converted to an upstart job. you may also use the start (8) utility, eg. start s20plymouth-splash
Start: uknown job S20plymouth splash

If i leave it the screen just goes black


I can get to ttyl by using ctrl&alt&f7 and log in.
but thats about it
startx just tells me no screens found I expect because xorg isn't used.


If i go into recovery mode, failsafe graphics won't load either.
So i select netroot and the enter startx which will give me a root desktop.
I tried reinstalling grub, but no change.
Not sure where to go from here

i suspect it is something to do with plymouth? but i am no expert even tho i've been a user for 4 years

---

### Post by Mrs Twaddle on 2011-02-28
Added...
when i get on to root desktop it works well graphically, i can even get the effects working.
So i know my onboard graphics work fine.  
Tried reinstalling xorg-video-intel and it still won't boot.
when i boot to failsafe graphics, the screen doesn't just go black, it turns off.

---

### Post by Mrs Twaddle on 2011-02-28
[https://bugs.launchpad.net/ubuntu/+source/plymouth/+bug/619021](https://bugs.launchpad.net/ubuntu/+source/plymouth/+bug/619021)
appears to be a bug report for the ply_keyboard_watch_for_input: Assertion `keyboard != ((void*)0) error i have

I don't know if i can remove plymouth?

---

### Post by Mrs Twaddle on 2011-02-28
OK i editted grub to skip Pylmouth
Not a wise move from what i can gather. But It did confirm that is where my problem is

I editted these lines ```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash nomodeset video=uvesafb:mode_option=1024x768-24,mtrr=3,scroll=ywrap"
GRUB_CMDLINE_LINUX="vga=792 splash"
```
to
```
GRUB_CMDLINE_LINUX_DEFAULT=""
GRUB_CMDLINE_LINUX=""
```

I would like to have a splash instead of the txt i now get, so what can i do?

---

