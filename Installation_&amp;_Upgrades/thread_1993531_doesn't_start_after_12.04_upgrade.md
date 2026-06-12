---
title: "doesn't start after 12.04 upgrade"
date: 2012-06-02
forum: Installation &amp; Upgrades
---

### Post by voyy on 2012-06-02
Hi, to start I'll say I googled and I know this is graphics issue. 
vga: ATI Radeon HD Series 4800

I did reinstall fglrx*, I also tried drivers from ATI website, I also purged fglrx* hoping that without drivers ubuntu will rebuild to some basic driver but this changed nothing.

I figured I'll burn 12.04 install and try recovering from live install. Doesn't start, not live system, not installation, I get:
> 
[145.72854] SQUASHFS error: Unable to read page, block 376ab47, sizef960
[148.51534] end_request: I/O error, dev sr0, sector 114624
and that's the end of cd booting... I run disc check and there were no errors.
I installed 12.04 under win7 virtualbox and it worked fine so cd allright.

Scary thing is that safe graphic mode from recovery mode doesn't start also, I do have networking in console so I was able to reinstall X, reconfigure xorg.conf, delete unity and install gnome-session-fallback with gdm instead of lightdm but nothing changed. At this point I'm taped and in need of help.

---

### Post by darkod on 2012-06-02
Have you tried to boot it with something like radeon.modeset=1?

Not sure if it will help, but worth a shot. When you are at the grub2 boot menu and with the ubuntu entry highlighted you can hit 'e' for editing the boot lines. Add that parameter in the line starting with linux, instead of the 'quiet splash'.

---

### Post by Gyokuro on 2012-06-02
Hi

The error means that your CD is broken - use a new one and it should work.

---

### Post by voyy on 2012-06-02
> **darkod said:**
> Have you tried to boot it with something like radeon.modeset=1?

Not sure if it will help, but worth a shot. When you are at the grub2 boot menu and with the ubuntu entry highlighted you can hit 'e' for editing the boot lines. Add that parameter in the line starting with linux, instead of the 'quiet splash'.

It didn't 
Screen goes black and looks like computer crashes, no console is available, doesn't respond to nothing but hard restart.

edit: now it won't load even to console in normal boot mode, I reverted that change but no effect, it crashes before I can see anything loading. So I'm left with recovery mode console only, looks like I managed to ****** it up totally just by reinstalling gfx drivers ;)

---

### Post by voyy on 2012-06-02
> **Gyokuro said:**
> Hi

The error means that your CD is broken - use a new one and it should work.

I did install successfully from that cd under windows 7 virtual machine. Maybe that's win7 drivers, off to store now for new dvd and will try again.

Still would like to know what got messed up though and how to fix it.

---

