---
title: "Kernel Versions"
date: 2006-11-03
forum: Installation &amp; Upgrades
---

### Post by rionoco on 2006-11-03
hello,

i can´t make Ubuntu work in my computer.
my problem is the ATI Radeon X700.
am i supposed to download any kernel source?

i was trying to find the kernel version of my ATI by typing:

cat/proc/version (no response)

so i can finish the command in:
sudo apt-get install linux-headers-version-(of my kernel)

then..when i type:
sudo apt-get install xserver-xorg-video-ati

says that it can´t find any candidate

i think i need to download drivers for the ATI but..i´m afraid that if i do download the driver and the kernel source i will be without operational system

what should i do?

thnx
](*,)

---

### Post by boban on 2006-11-03
Whoa! What exacly is your problem? Your ubuntu dosn't start at all, or you just don't have hardware accelerecation?

If its about ati drivers, then try: 
[http://wiki.cchtml.com/index.php/Ubuntu_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Installation_Guide)

---

### Post by rionoco on 2006-11-03
i don´t really know whats going on.
my failure is this:

Failed to start the X server (your graphical interface).
It is likely that it is not set up correctly.

X Windows system version 7.0.0
Release Date 21 December 2005
X Protocol Version 11, Revision 0, Release 7.0

Build Operating System: Linux ubuntu 2.6.15-23-386 #1 PREEMPT Tue
May 23 13:49:40 UTC 2006 i686

Fatal server error:
no screen found
XIO: fatal I0 error 104 (connection reset by peer) on X server ":0.0"
after 0 request (0 known processed with 0 events remaining)

i tryed to reconfigure with:

sudo dpkg-reconfigure xserver-xorg
with many types of configuration but nothing seems to work:-?

---

### Post by boban on 2006-11-03
> **rionoco said:**
> i don´t really know whats going on.
my failure is this:


Hmmm... Two more questions: are you booting live cd or does it crash after installation? What version of Ubuntu are you using?

---

### Post by hda on 2006-11-03
> **rionoco said:**
> i don´t really know whats going on.
my failure is this:

Failed to start the X server (your graphical interface).
It is likely that it is not set up correctly.

X Windows system version 7.0.0
Release Date 21 December 2005
X Protocol Version 11, Revision 0, Release 7.0

Build Operating System: Linux ubuntu 2.6.15-23-386 #1 PREEMPT Tue
May 23 13:49:40 UTC 2006 i686

Fatal server error:
no screen found
XIO: fatal I0 error 104 (connection reset by peer) on X server ":0.0"
after 0 request (0 known processed with 0 events remaining)

i tryed to reconfigure with:

sudo dpkg-reconfigure xserver-xorg
with many types of configuration but nothing seems to work:-?

Had the same problems with ATI video cards. There seem to be two options:

1) replace "ati" by "radeon" in your xorg.conf
2) install the "fglrx" driver

hth

---

