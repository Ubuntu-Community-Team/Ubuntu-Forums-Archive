---
title: "configure: error: Cannot find ltdl.h -- libtool-devel (or libtool-ltdl-devel) no t in"
date: 2006-02-23
forum: Installation &amp; Upgrades
---

### Post by sdb2028 on 2006-02-23
How do you fix this error:?
configure: error: Cannot find ltdl.h -- libtool-devel (or libtool-ltdl-devel) no t installed?
[ATTACH]6371[/ATTACH]

[ATTACH]6372[/ATTACH]

---

### Post by Greg2 on 2006-02-23
[QUOTE=sdb2028]
configure: error: Cannot find ltdl.h -- libtool-devel (or libtool-ltdl-devel) no t installed?[/QUOTE]
Are you still trying to compile gnucash?

To fix your error use the synaptic package manager to install libltdl3-dev and automake1.8 or 1.9 ‘with’ the libtool and libltdl3 that you already have installed.

---

### Post by sdb2028 on 2006-02-23
Thanks Greg,
I got Gnucash installed from synaptic (finally1), but seem to run into that error most times when I try to configure any app from the terminal. So I wanted to know how to fix it before I needed it again.

While I have your attention: my internet connection only comes up once in a while. I have to keep rebooting untill it comes up. I am running Toshiba Laptop dual boot system (WindowsXP Home, and Ubuntu) with an Intell Centrino 2200 wireless through a Linksys router to a motorola broadband cable modem. Windows accesses the internet fine. I have gone through the steps outlined in the threads for simular problems. I have a good connection to the router, the router just doesn't seem to connect ubuntu to the internet every time.

I also have a desktop machine with Windows ME, Fedora Core4, and Ubuntu wired direct to the router, all of which access the internet with no problems.

Any help you can offer will be greatly appreciated.
Thanks,
Steve

---

### Post by Greg2 on 2006-02-23
I’m going to give you some links for info... that you may or may not already know. This is a good one for ‘using the command line’ (so you won’t have to reboot) to start your wireless network:
[https://wiki.ubuntu.com/WiFiHowto](https://wiki.ubuntu.com/WiFiHowto)
This is for the gui:
[https://wiki.ubuntu.com/WirelessNetworking](https://wiki.ubuntu.com/WirelessNetworking)
This is for using if it ‘still’ doesn’t work properly:
[https://wiki.ubuntu.com/WirelessTroubleshootingGuide](https://wiki.ubuntu.com/WirelessTroubleshootingGuide)
Let us know if you still have any problems.

---

### Post by sdb2028 on 2006-02-23
Thanks,
Went through all that---- but can't hurt to do it again, in case I made in error.
I'll let you know how it works out.


About the earlier matter of trying to configure Gnucash--- I was trying to configure the new release gnucash1.91. (unstable), to see how it works. I keep getting closer however now I get the message:

checking for GLIB - version >= 2.4.0... no
*** Could not run GLIB test program, checking why...
*** The test program failed to compile or link. See the file config.log for the
*** exact error that occured. This usually means GLIB is incorrectly installed.
configure: error:
*** GLIB >= 2.4 is required to build Gnucash; please make sure you have the
*** development headers installed. The latest version of GLIB is
*** always available at [ftp://ftp.gnome.org/pub/gnome/sources/glib/](ftp://ftp.gnome.org/pub/gnome/sources/glib/).

I went to the ftp site-- downloaded and installed like it said--- still the same error as above.

---

### Post by Greg2 on 2006-02-25
> **sdb2028]
checking for GLIB - version >= 2.4.0... no
*** Could not run GLIB test program, checking why...
*** The test program failed to compile or link. See the file config.log for the
*** exact error that occured. This usually means GLIB is incorrectly installed.
configure: error:
*** GLIB >= 2.4 is required to build Gnucash said:**
> ftp://ftp.gnome.org/pub/gnome/sources/glib/[/url].

I went to the ftp site-- downloaded and installed like it said--- still the same error as above.
Sorry, I missed this post yesterday.

Install the libglib2.8.3-0ubuntu1, libglib-data and libglib-dev (same version) with your synaptic package manager.

---

