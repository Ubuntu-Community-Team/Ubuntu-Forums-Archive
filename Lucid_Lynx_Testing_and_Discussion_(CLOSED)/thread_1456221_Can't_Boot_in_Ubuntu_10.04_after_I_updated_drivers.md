---
title: "Can't Boot in Ubuntu 10.04 after I updated drivers!!"
date: 2010-04-16
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by TheNerdAL on 2010-04-16
I updated my video card drivers to the recommended version and it told me that I had to restart and so I did. When it restarted it was just a black screen with a white underscore on the screen. Help! 
 
Thanks,
TheNerdAL

---

### Post by TheNerdAL on 2010-04-16
Also, my caps lock and scroll lock lights on my keyboard blink.

EDIT: I got it to boot up but the splash screen was like all messed up and stuff. Help!

---

### Post by lnxguit on 2010-04-16
> **TheNerdAL said:**
> Also, my caps lock and scroll lock lights on my keyboard blink.

EDIT: I got it to boot up but the splash screen was like all messed up and stuff. Help!
What video card are you using? What drivers did you download (and from where?)

---

### Post by TheNerdAL on 2010-04-16
I think Nvidia Geforce 8400, but I'm not sure and from the Hardware Drivers in Administration.

---

### Post by TheNerdAL on 2010-04-16
I'm scared to reboot, lol.

---

### Post by kansasnoob on 2010-04-17
Well you'll have to reboot! Maybe you can do so by pressing Alt + SysReq + B, or maybe you'll have to use the reset button.

Then if Lucid is the only OS on that machine you'll have to hold down the space bar just after the system/BIOS screen passes. That should bring up the boot menu with a Recovery Mode option.

Boot into Recovery Mode and when it completes you'll see several options:

resume
clean
dpkg
failsafeX
grub
netroot
root

You need to choose "failsafeX" and then amend/reverse your bad decisions!

---

### Post by tokyobadger on 2010-04-17
another alternative is to boot up with the livecd, open a terminal and then:
```
 sudo mount /dev/sdx /mnt ## where /dev/sdx is your ubuntu / partition
sudo mount --bind /dev /mnt/dev
sudo mount --bind /proc /mnt/proc
cd /mnt
sudo chroot /mnt
sudo apt-get update && sudo apt-get upgrade
```
while in the chrooted environment, perform whatever repair tasks you need to then when finished
```
exit
sudo umount /mnt/proc
sudo umount/mnt/dev
sudo umount /mnt
```
reboot, hopefully you're up and running again

---

### Post by TheNerdAL on 2010-04-17
> **tokyobadger said:**
> another alternative is to boot up with the livecd, open a terminal and then:
```
 sudo mount /dev/sdx /mnt ## where /dev/sdx is your ubuntu / partition
sudo mount --bind /dev /mnt/dev
sudo mount --bind /proc /mnt/proc
cd /mnt
sudo chroot /mnt
sudo apt-get update && sudo apt-get upgrade
```
while in the chrooted environment, perform whatever repair tasks you need to then when finished
```
exit
sudo umount /mnt/proc
sudo umount/mnt/dev
sudo umount /mnt
```
reboot, hopefully you're up and running again

Live CD has an iso error. <.< Check my other threads. 

Anyone please help?!

---

### Post by TheNerdAL on 2010-04-17
> **kansasnoob said:**
> Well you'll have to reboot! Maybe you can do so by pressing Alt + SysReq + B, or maybe you'll have to use the reset button.

Then if Lucid is the only OS on that machine you'll have to hold down the space bar just after the system/BIOS screen passes. That should bring up the boot menu with a Recovery Mode option.

Boot into Recovery Mode and when it completes you'll see several options:

resume
clean
dpkg
failsafeX
grub
netroot
root

You need to choose "failsafeX" and then amend/reverse your bad decisions!

Tried it but it doesn't work.

---

### Post by tokyobadger on 2010-04-17
you can use any livecd - doesn't have to be the ubuntu-10.04

---

### Post by TheNerdAL on 2010-04-17
> **tokyobadger said:**
> you can use any livecd - doesn't have to be the ubuntu-10.04

Yeah, but both my cds (9.10 and 10.04 Beta 2) have errors.

---

### Post by TheNerdAL on 2010-04-17
Okay, it boots but with the splash screen like messed up with lines that are red and stuff like that. But this only boots up at random times, like sometimes there is a black screen with a white underscore and sometimes there is a purple screen with a white underscore and sometimes it boots but with a messed up splash screen before booting.

---

### Post by kansasnoob on 2010-04-17
> Live CD has an iso error. <.< **Check my other threads**. 

Oh, really! Do you know what you're asking?

Should we all research everyone's previous posts each and every time?

> Yeah, but both my cds (9.10 and 10.04 Beta 2) have errors. 

If you don't even have decent installation media what do you expect us to do?

---

### Post by TheNerdAL on 2010-04-17
Well first I want to know how to fix why my LiveCD's that I burn don't boot up when I checked the hash and it was the same.

---

### Post by TheNerdAL on 2010-04-17
Anyone? :(

---

### Post by TheNerdAL on 2010-04-17
Lol, I'm not going to update drivers in Beta no more. <.<

---

### Post by geckon on 2010-04-19
Hi! I have got the same problem. I installed 10.04 Beta 2, then aptitude safe-upgrade'd, then installed Nvidia proprietary driver (the recommended version - 190.53, I guess) and rebooted. Now I can't boot anymore. Anytime I try it, I get only black screen and blinking LEDs(no matter if I boot normally or try recovery). Is this driver broken everywhere or just at my (and TheNerdAL's) place? Thanks for any hint. 

EDIT: I installed Kubuntu, if that matters.

EDIT2: There is a [bug]("https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers/+bug/567202") reported on this issue.

---

### Post by geckon on 2010-04-20
There is another reported [bug #548362]("https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers/+bug/548362") (the first one was marked as a duplicate of this one) and it seems that there is a problem with multiple GPUs installed. Using an older kernel (2.6.31) is probably a workaround. Please follow that bug if interested.

---

