---
title: "[SOLVED] XServer problems after last nights update (8.10 beta)"
date: 2008-10-15
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by DSn0wMan on 2008-10-15
After the updates I got from last night (8.10 Beta) I am having some weird Xserver problems.

When I log in, everything works just fine. However when my wife logs in her desktop never loads. It just sits on a blank brown screen.

If I try to log her in from the fast user switching applet I get the following error

The X server failed to finish starting.
3 X failed

---

### Post by dhtseany on 2008-10-15
Did you try Alt+Ctrl+F1 and see if you can get to a command prompt? If so try running xconfig and see if that will get you anywhere. My guess is maybe it's something to do with her profile settings but I'm not sure if that will change individual profile stuff or overall settings. That is weird though how it only seems to be her profile.

Peace
Sean

---

### Post by DSn0wMan on 2008-10-15
The thing that is strange is that it is different for a different user. I was under the impression that xserver settings were system wide.

---

### Post by dhtseany on 2008-10-15
Yeah that's what I meant. I was just tossing out ideas :)

Peace
Sean

---

### Post by caryb on 2008-10-16
Are you using Ubuntu or Kubuntu? 


Cary

---

### Post by DSn0wMan on 2008-10-16
I am using Ubuntu

---

### Post by DSn0wMan on 2008-10-16
It is working now. All I had to do is select gnome for her on the login page. Somehow the update messed up her default login choice.

I got the hint from this thread

[http://ubuntuforums.org/showthread.php?t=949099](http://ubuntuforums.org/showthread.php?t=949099)

---

### Post by soho2014 on 2008-10-28
> **DSn0wMan said:**
> After the updates I got from last night (8.10 Beta) I am having some weird Xserver problems.

When I log in, everything works just fine. However when my wife logs in her desktop never loads. It just sits on a blank brown screen.

If I try to log her in from the fast user switching applet I get the following error

The X server failed to finish starting.
3 X failed

I am having the same problems, but I can't see anything in the settings that I can change that will allow me to solve this problem.

---

