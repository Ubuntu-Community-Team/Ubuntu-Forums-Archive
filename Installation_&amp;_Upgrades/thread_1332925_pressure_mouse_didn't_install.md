---
title: "pressure mouse didn't install"
date: 2009-11-20
forum: Installation &amp; Upgrades
---

### Post by edkwok on 2009-11-20
hi,
  I am trying to install Kubuntu 9.04 on a samsung 1Q ultra tablet, this unit has a pressure mouse, one of those you put your finger on the button and push it around.
  Anyway, I put the kubuntu 9.04 and boot off the CD. The initial boot up, Kubuntu see the pressure mouse and I could use it to select Kubuntu install to hard drive. Kubuntu than check for hardware and drivers need to install. After awhile, Kubuntu came back ask for language and time zone to install, at this point, I lost the mouse, I can not move the ptr to make my selection.  If I plug in a USB mouse than it work fine.
  Can someone tell me if there is a particular driver need for these kind of mouse?  Seem like a mouse is not a mouse, or not all mouse are created equal!!!!

---

### Post by Favux on 2009-11-21
Hi edkwok,

Looks like a cool device!

I would have guessed it uses the evdev evtouch driver (available in Synaptic Package Manager).  But it has a stylus so I'm not sure.  Let's see if it will tell us anything.

In a terminal enter (copy and paste):
```
xinput --list
```
```
more /proc/bus/input/devices
(and/or)
grep -i name /proc/bus/input/devices
```
```
ls -la /dev/tablet-event
```
```
lshal>edkwok_lshal-1.txt
```

---

### Post by edkwok on 2009-11-28
Thanks for replying, it is a cool device only if I can get Ubuntu on it.... 

see attached files as requested.

I hope the attached file did attached to this reply, let see.

---

