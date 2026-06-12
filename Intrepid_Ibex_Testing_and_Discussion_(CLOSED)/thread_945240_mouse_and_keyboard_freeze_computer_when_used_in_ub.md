---
title: "mouse and keyboard freeze computer when used in ubuntu 8.10"
date: 2008-10-12
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by noogs on 2008-10-12
First of all, I have checked other threads regarding the mouse/keyboard freezing issue but they all successfully upgraded to the new version before the problem occured. I could not even get that far.

I booted from the live CD and tried to install but the moment I touched the keyboard or mouse the computer froze. I tried to just try ubuntu with no change to my computer (the top function on the menu - I forget what it is called :P) and the same thing happens: It will load the desktop, I just cannot communicate with it. I also tried safe graphics mode but to no avail.

- CPU: AMD Athlon(tm) 64 X2 Dual Core Processor 3800+
- Video card: ATI Radeon X1650 Pro

Hardy Heron works fine (bar a few issues I am too lazy to research).

---

### Post by kaffelars on 2008-10-12
Maybe this applies to you?

[http://ubuntuforums.org/showthread.php?t=944201]("http://ubuntuforums.org/showthread.php?t=944201")

---

### Post by noogs on 2008-10-12
Thank you but no that doesn't apply to me. They upgraded from 8.04 and I am doing a fresh install and the live cd or installation just freezes.

---

### Post by noogs on 2008-10-12
Any ideas will help I really want to do a fresh install of ibex because there are many problems with my current installation.

---

### Post by incubus on 2008-10-12
noogs,

Unfortunately it's hard to guess what's going on without more debugging details -- and of course it's hard to get them if you can't type anything.  So I can think of the following:

1. Get a more up-to-date installation image:

[http://cdimage.ubuntu.com/](http://cdimage.ubuntu.com/)

Perhaps (and I repeat, perhaps) your bug may have been fixed by now.


2. Use the alternate install CD instead

This should give you a system to start with, then even if X continues to crash you can get some debugging information from /var/log/Xorg.0.log


I don't have much experience with the live CDs, so somebody else may have a better idea of how to get around this.

incubus

---

### Post by noogs on 2008-10-12
FIXED

I reinstalled hardy heron and then updated to Ibex. The same problem persisted so I removed the network manager (while in root recovery mode, type sudo update-rc.d networkmanager remove) and rebooted. Now everything works fine except the mouse gets a little jumpy. Thank you.



**update**
It still freezes when I touch the mouse or hit a key most of the time. Occasionally it doesn't freeze and I am able to login. I've tried removing network manager. When I look in the system logs it says that gnome-wm.desktop isn't being registered or something. I'm not sure if that is part of the problem.

---

### Post by incubus on 2008-10-12
Bummer.  And you're not alone, there have been many reports of inputs stopping to work with Intrepid -- although in your case the whole system freezes.  The developers are working hard to fix these bugs.  If you don't get a useful answer here, I suggest you head over to launchpad.

Can you at least go to one of the terminals (ctl+alt+f1) and type from there?  Can you get some log files?

---

### Post by noogs on 2008-10-13
Ok here is my update so far I have been able to do a fresh install of 8.04 then upgrade to 8.10 then I got everything installed and everything works great except for the fact that many times when I boot up it freezes right when I go to login, which is kind of a problem :P. When this happens I do a hard boot and it will still do it so I repeat my hard boot many times (I don't keep track) and eventually I am able to login and everything works fine. Any ideas would help it may just be a bug that I'll have to deal with until something comes out to fix it but I hope not. With my old installation I had to login twice because of problems and I thought that was annoying.

**update**
I did a reboot and it booted fine so I guess it was just little odds and ends that I ended up fixing whenever something failed at boot.
Thanks for everyone's help.

---

### Post by incubus on 2008-10-14
> **noogs said:**
> Ok here is my update so far I have been able to do a fresh install of 8.04 then upgrade to 8.10 then I got everything installed and everything works great except for the fact that many times when I boot up it freezes right when I go to login, which is kind of a problem :P. When this happens I do a hard boot and it will still do it so I repeat my hard boot many times (I don't keep track) and eventually I am able to login and everything works fine. Any ideas would help it may just be a bug that I'll have to deal with until something comes out to fix it but I hope not. With my old installation I had to login twice because of problems and I thought that was annoying.

**update**
I did a reboot and it booted fine so I guess it was just little odds and ends that I ended up fixing whenever something failed at boot.
Thanks for everyone's help.

It could be a hardware issue too, you know.  Did you check your logs and dmesg?  What if you use a regular vesa driver for your graphics card?  Have you tried all this with a different mouse & keyboard?

---

### Post by noogs on 2008-10-14
No I haven't tried any of these but so far it works so I'm not worrying about it.

---

### Post by jthill on 2008-10-26
I'm having what looks like the same problem: boot works, gdm comes up, I can log in, then a complete freeze requiring the 5-second salute.

Safe-mode gnome does the same thing.

TWM works.

This from update-manager -d about an hour ago, upgraded from the heron.

---

### Post by markba on 2008-10-27
It's happening to me also, the machine freezes after or during login. I tried several options (noapic, nolapic, nohz=off, highres=off, hpet=disabled), single or in combination, no go. Tried fresh install from Intrepid and upgrades from Hardy. Very frustrating, especially because the PC was running OK with Hardy.

I cannot find an bug entry in Launcpad. Either the bug has not been posted, or I'm searching with the wrong arguments (intrepid freeze boot).

---

