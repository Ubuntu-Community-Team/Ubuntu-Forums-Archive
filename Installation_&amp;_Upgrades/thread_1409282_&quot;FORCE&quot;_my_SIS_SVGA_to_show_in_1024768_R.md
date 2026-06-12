---
title: "&quot;FORCE&quot; my SIS SVGA to show in 1024*768 Resolution"
date: 2010-02-17
forum: Installation &amp; Upgrades
---

### Post by paulbuk on 2010-02-17
I need to FORCE my SIS onboard VGA controller to ALWAYS load in 1024*768 resolution, NOT 600*800.

Problem/Background:
I am running currently 2 comps: 1) - my main Ubuntu box (here) and 2)  - an old winXP box which I use for my old CCTV. Until I upgrade I am using a KVM (Keyboard, Video, Mouse) switcher as the cctv is on 24/7.
Monitor used: Acer AC713 17" CRT monitor. (The cctv will stay on the winXP box until I buy a further dedicated unit to run a linux based cctv).

The Ubuntu "Display" function in "System-> Prefs" works fine when the monitor is connected direct and show the 1024*768 option, but when I connect it via the KVM switch, it ONLY detects VGA 800*600, which is crap.
System->Admin->System testing produces no positive results.

- I have not installed Chrome 9 as yet (if I need to?).

- I have read: [https://help.ubuntu.com/community/Video#Sis](https://help.ubuntu.com/community/Video#Sis)

- the "/etc/X11/xorg.conf" shows blank: 0 lines, 0 characters
I've tried all the online ideas and probably missing a small point?



lspci | grep VGA:

VGA info:
01:00.0 VGA compatible controller: VIA Technologies, Inc. K8M890CE/K8N890CE [Chrome 9] (rev 11)

This posting is a follow on the one posted 2 weeks past, no replies to that.


PLEASE HELP!
Any simple solution and help would be greatly appreciated as I am tired of having to switch off the nixbox, undo all VGA cables to reconnect the winXp box to edited the cctv files every day and then re-connect the nixbox backup again to see in SVGA!!

After 2 weeks, Ubuntu is great and I've 'moved 'away from MS Windros "Vesta" (does sound like an old UK '70's curry brand!!) as Ubuntu does everything. Can't wait to get my new comp in the summer with a new 20" TFT.
I tell all my IT students now to 'move' over to Ubuntu!!
(-:


PB
old/new learner
but.... "Flying the flag for Ubuntu"
:D

---

