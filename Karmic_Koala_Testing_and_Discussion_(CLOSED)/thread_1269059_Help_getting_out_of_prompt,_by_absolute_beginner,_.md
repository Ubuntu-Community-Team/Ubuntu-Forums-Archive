---
title: "Help getting out of prompt, by absolute beginner, i mean ABSOLUTE beginner. :)"
date: 2009-09-17
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by ikitson on 2009-09-17
So, I just began college and i'm starting to learn Linux redhat 8.0 and how it all works, i'd imagine ubuntu commands to be the same, although I am not far in the course enough to know how to get into the OS, graphic wise.

So here's some info:

I'm booting up Ubuntu karmic 9.10 Alpha 5.
 AMD Phenom quadcore 9950       x86 (I'm pretty sure I have the right version of ubuntu)
I formatted successfuly and Ubuntu boots up in prompt

I'm afraid to say I am absolutely clueless on what to do from this point on, i'd appreciate all the help i can get. :) TY

---

### Post by scragar on 2009-09-17
Try:
```
startx
```

---

### Post by ikitson on 2009-09-17
> **scragar said:**
> Try:
```
startx
```

So here's what it gives me:

X: Cannot stat /tmp/.X11-unix (no such file or directory) aborting.


Ty for the reply, btw. :)

---

### Post by scragar on 2009-09-17
OK, let's try a simple fix first:
```
sudo rm -rf /tmp
sudo mkdir -m 777 /tmp
```
This will remove the current temp directory then recreate it, after that try starting X again to see if the problem persists.
```
startx
```

---

### Post by ikitson on 2009-09-17
alright so the first command does not delete tmp, it says its a read only file, while the other command says that tmp already exists. :O

Note: im typing after the ~$ characters

---

### Post by ankspo71 on 2009-09-17
Hi,
X: Cannot stat /tmp/.X11-unix (no such file or directory) aborting.

I don't know what that means, but I believe startx is part of a package called xinit in Ubuntu (9.04), and might be the same way in Redhat. (just guessing)

Try typing xinit to see what happens. It might tell you it is not installed or something. it might not be if you are using a server distro.

---

### Post by ikitson on 2009-09-17
> **ankspo71 said:**
> Hi,
Try typing xinit to see what happens. It might tell you it is not installed or something. it might not be if you are using a server distro.

xinit gives me the same message :(

---

### Post by scragar on 2009-09-17
> **ikitson said:**
> alright so the first command does not delete tmp, it says its a read only file
OK, now the question is why your file system is read only.


```
sudo mount -o remount,rw /
```Try that, see if it can remount the file system.

EDIT: sorry to hear your first real experience is this bad, normally the gui should load first time, there's clearly something wrong for it not to work.

---

### Post by ikitson on 2009-09-17
> **scragar said:**
> 
EDIT: sorry to hear your first real experience is this bad, normally the gui should load first time, there's clearly something wrong for it not to work.

Woohoo, ok so it worked, i then put in startx and the text went away and then my cursor showed up, unable to move it i sat there waiting, then it turned into the small white loading ball, then a few seconds after, the pc froze. ACK!

---

### Post by issih on 2009-09-17
Unless there is a VERY good reason for it there is no way you should be running alpha code as an absolute beginner.

Go download the jaunty iso, and make sure it is the desktop iso not the server, and give that a whirl instead.

Hope that helps

---

### Post by ikitson on 2009-09-17
> **issih said:**
> Unless there is a VERY good reason for it there is no way you should be running alpha code as an absolute beginner.

Go download the jaunty iso, and make sure it is the desktop iso not the server, and give that a whirl instead.

Hope that helps

I agree and will do that, but i'm at the next step now, i rebooted and linux fixed the errors from the unclean shut down, rebooted again and went to the login screen, where entering my password does not login to the OS.

---

### Post by issih on 2009-09-17
I repeat...stop playing with development code!...It is almost certainly broken! (that is an exaggeration, but it is just not worth you spending time trying to get a buggy codebase to function when you don't even know the basics of the OS, cut your losses and reinstall)

---

### Post by ikitson on 2009-09-17
Clicking on my profile then switching gnome to xtern made a white prompt popup in the top left corner after loging in, am i doing it right?

---

### Post by scragar on 2009-09-17
> **ikitson said:**
> I agree and will do that, but i'm at the next step now, i rebooted and linux fixed the errors from the unclean shut down, rebooted again and went to the login screen, where entering my password does not login to the OS.

That's sort of the problem with pre-releases, they tend to be for testing things on a range of hardware before people start using it in bulk, they often have lot's of errors and bugs.

If you hold ctrl+alt and press F1 you will get a terminal, log into it and use```
dmsg|tail
```to see what messages that returns, you might also try:
```
tail /var/log/Xorg.0.log
```To see what the graphical interface has to say about any errors it may encounter.

---

### Post by overdrank on 2009-09-17
Moved to  Karmic Koala Testing and Discussion

---

### Post by psyke83 on 2009-09-17
> **ikitson said:**
> So, I just began college and i'm starting to learn Linux redhat 8.0 and how it all works, i'd imagine ubuntu commands to be the same, although I am not far in the course enough to know how to get into the OS, graphic wise.

So here's some info:

I'm booting up Ubuntu karmic 9.10 Alpha 5.
 AMD Phenom quadcore 9950       x86 (I'm pretty sure I have the right version of ubuntu)
I formatted successfuly and Ubuntu boots up in prompt

I'm afraid to say I am absolutely clueless on what to do from this point on, i'd appreciate all the help i can get. :) TY

You will get a lot more enjoyment from a stable release (Jaunty) if you are new to Linux. You are putting already putting yourself in unfamiliar territory; why spoil the initial experience by fighting buggy software?

If you insist on running the development release, I would suggest that you at least skims the threads in the "Karmic Koala Testing & Discussion" forum (where your post was moved) to get a lay of the land.

---

### Post by ikitson on 2009-09-17
> **psyke83 said:**
> You will get a lot more enjoyment from a stable release (Jaunty) if you are new to Linux. You are putting already putting yourself in unfamiliar territory; why spoil the initial experience by fighting buggy software?

If you insist on running the development release, I would suggest that you at least skims the threads in the "Karmic Koala Testing & Discussion" forum (where your post was moved) to get a lay of the land.
  
thanks.

---

### Post by VMC on 2009-09-17
ikitson, karmic isn't the latest Ubuntu. Jaunty is. karmic is testing, and you started off at the worse possible time trying to both learn Linux on a very buggy testing alpha Linux.

Please do yourself a favor and do as was suggested and download Jaunty. You will thank yourself for doing so.

Also google around a bit about "learning linux" or "beginning linux". Something along those lines. Hundreds of hit will appear. They will walk you through each command and explain much better than we could.

---

### Post by ranch hand on 2009-09-18
> **issih said:**
> Unless there is a VERY good reason for it there is no way you should be running alpha code as an absolute beginner.

Go download the jaunty iso, and make sure it is the desktop iso not the server, and give that a whirl instead.

Hope that helps
Do this.

Jaunty is the current Ubuntu and it works.

9.10 is so named because it is supposed to come out in 2009 in October (27th).

It is pretty badly broken right now on a lot of machines, if you got the A6 Live CD to work you were lucky.

There will be more breaks in the system weekly, if not daily.

Get Jaunty.

---

