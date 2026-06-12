---
title: "Joystick issues in version 10.4"
date: 2010-03-26
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by H13N.H3N on 2010-03-26
short history, i updated from 9.10 to 10.4 and everything looks and works sweet, but i can't use my joystick controller *properly*, i found a bug report confirmed regarding this problem, while running command 
```
jstest --normal / dev/input/js0
```
makes the controller work (some times with strange behavior like taking the control of the/ as a mouse pointer) i can't find a way to make it work from the start without having to mess directly with '/dev' files, i know that it's provably i will have to. here is the bug report [https://bugs.launchpad.net/ubuntu/+source/joystick/+bug/448446](https://bugs.launchpad.net/ubuntu/+source/joystick/+bug/448446)

ah, my.. i ran a second command to make sure my joypad is actually detected even if not possibly available for playing, aaaand i got this result:

```
Driver version is 0.8.0.
jstest is not fully compatible with your kernel. Unable to retrieve button map!
Joystick (Unknown) has 2 axes and 2 buttons.
Testing ... (interrupt to exit)
```

well, this is getting weird, really really weird, my controller now is *working*, but now it controls the mouse pointer every time, not just *some* times, i can even click with buttons and things, this would be very interesting if i chose to install that option, let's say package 'Joy2Key', but the thing is that i did not install such thing.

---

### Post by overdrank on 2010-03-26
Moved to Lucid Lynx Testing and Discussion :)

---

### Post by H13N.H3N on 2010-03-26
> **overdrank said:**
> Moved to Lucid Lynx Testing and Discussion :)

thank you, i hope this can be solved soon =)

the junk on this, what's the point in reporting something that will no be threated anyway? nevermind on this anyway... thnks for the  post moved

---

