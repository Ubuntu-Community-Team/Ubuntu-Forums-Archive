---
title: "No tty consoles in Kubuntu Lucid alpha3"
date: 2010-03-10
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by pschuel on 2010-03-10
Hi everyone,

I am currently testing Kubuntu 10.04 alpha3, and everything works OK except that there is no splash screen on startup (just a black screen) and - more importantly - that the tty consoles do not work (Ctrl-Alt-F1 and the like). There is simply no response to the Ctrl-Alt-F1 (...F6) keys, i.e. the GUI stays on the screen and nothing changes. The getty processes are running for tty1 to tty6. plymouth is installed (even tried to reinstall).

System information:
OS: Ubuntu lucid (dev) · Kernel: 2.6.32-16-generic · KDE: 4.4.1 (KDE 4.4.1)
CPU: AMD Turion(tm) Dual-Core Mobile ZM-82 · RAM: 2032592kB/3799764kB
VGA: ATI RS780M/RS780MN [Radeon HD 3200] / ATI Mobility Radeon HD 3400

I don't know which graphics driver is installed. Apparently, Lucid has a package "xserver-xorg-video-all", which installs all video drivers, and no xorg.conf. Presumably it is xserver-xorg-video-ati or xserver-xorg-video-radeon.

Does anyone know how to get the consoles back? Or, if I want to report a bug, which package should it be reported against?

Patrick

---

### Post by Tourdog on 2010-03-10
Patrick,
I have a very similar situation.  10.04 "daily build" (8 mar 2010) and after a few seconds the large grey scale Ubuntu image screen appears.................. then nothing but black.  Bios or grub don't show on screen.  (I am dual booting for now).

I think it may be my Nvidia graphics card  (works very well 185 driver for Karmic though).  I just made a post a few minutes ago.

I'll be watching any postings to your Q also!

---

### Post by pschuel on 2010-03-10
Tourdog,

I think your problem is a different one. Since you do not see BIOS messages nor GRUB, it may be a general problem with your graphics card.

I have normal BIOS messages and GRUB screen. Only after choosing a GRUB option, the screen goes blank until KDM comes up with the graphical login. Also, as I stated, the tty consoles are dead.

Also this thread should have been marked [all versions] instead of [kubuntu] since on second thought I don't think that KDE has much to do with it (should check with Gnome to be sure).

Patrick

---

### Post by cariboo on 2010-03-10
A bump for the move.

---

