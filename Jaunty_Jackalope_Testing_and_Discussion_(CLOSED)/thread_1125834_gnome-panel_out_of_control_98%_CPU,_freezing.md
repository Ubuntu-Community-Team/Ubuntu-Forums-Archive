---
title: "gnome-panel out of control 98% CPU, freezing"
date: 2009-04-14
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by RabidChipmunk on 2009-04-14
Anyone else having issues with gnome-panel sucking up all of your cpu? 

I've had to stop using gnome. 

Fresh 9.04 install but with an 8.10 user config. 

Panels freeze auto-hidden and you can't unhide them.

I had to kill gnome-panel and then it would restart and you could get to it, but then eventually it freezes again. 

Have switched back to e17.

Version 1:2.26.0-0ubunutu6
[Anyone else annoyed that Synaptic won't let you highlight the version? Yes, I know an xterm will.]

-sh

---

### Post by m2.g5ru6y7s on 2009-04-15
Yes it occurs after a random time.
Very annoying.
When it happens I have a very clumsy solution for it:
CTRL-ALT-F1(or F2, F3,....)
login as root
pkill gnome-panel
And then CTRL-ALT F7 or CTRL-ALT F9 (depending where the graphical X session is)
Then you have a working desktop again.
$ lsb_release -a
No LSB modules are available.
Distributor ID: Ubuntu
Description:    Ubuntu 9.04
Release:        9.04
Codename:       jaunty

uname -a
Linux 2.6.28-11-generic #41-Ubuntu SMP Wed Apr 8 04:38:53 UTC 2009 i686 GNU/Linux
$ apt-cache showpkg gnome-panel
Package: gnome-panel
Versions:
1:2.26.0-0ubuntu6 (/var/lib/apt/lists/nl.archive.ubuntu.com_ubuntu_dists_jaunty_
main_binary-i386_Packages) (/var/lib/dpkg/status)
 Description Language:
                 File: /var/lib/apt/lists/nl.archive.ubuntu.com_ubuntu_dists_jau
nty_main_binary-i386_Packages
                  MD5: 02085226815ba9e6a5733ab8ea00c173

---

### Post by m2.g5ru6y7s on 2009-04-15
But it seems the bug is reported already
[https://bugs.launchpad.net/ubuntu/+source/gnome-panel/+bug/332563](https://bugs.launchpad.net/ubuntu/+source/gnome-panel/+bug/332563)

Hope someone ever finds this bug.
Seems a nasty one very, very, very hard to find one.......
:-(

Good luck to all the programmers.

---

### Post by chrisccoulson on 2009-04-15
That bug won't be solved until somebody experiencing it provides a backtrace, as asked for.

---

### Post by m2.g5ru6y7s on 2009-04-15
> **chrisccoulson said:**
> That bug won't be solved until somebody experiencing it provides a backtrace, as asked for.

true. but the backtrace (for me) is very hard to generate, because the problem occurs randomly. 
And even when it occurs, no visible errors occur except a nearly frozen system.

---

### Post by alastair on 2009-04-15
> **chrisccoulson said:**
> That bug won't be solved until somebody experiencing it provides a backtrace, as asked for.

I tried using the -dbgsym version of gnome-panel a week ago, but could not get the backtrace. However, this was using the Live CDROM, a bit painful to work through, and I have now installed. I will try again.

Question :

If I install the -dbgsym version of gnome-panel, this will be the version running inside Gnome automatically?

Issue for me is/was - the **first** time any gnome-panel layout change was made (e.g. theme change, font etc.), the panel crashes/hangs. If I restart the panel (killall `pidof gnome-panel`), I can change the theme, font etc. without a problem.

---

### Post by chrisccoulson on 2009-04-15
> **alastair said:**
> I tried using the -dbgsym version of gnome-panel a week ago, but could not get the backtrace. However, this was using the Live CDROM, a bit painful to work through, and I have now installed. I will try again.

Question :

If I install the -dbgsym version of gnome-panel, this will be the version running inside Gnome automatically?

All the -dbgsym package contains is some debug symbols shipped in /usr/lib/debug, so that you can get symbolic backtraces with GDB. There are no binaries in the -dbgsym packages.

---

### Post by chrisccoulson on 2009-04-15
> **m2.g5ru6y7s said:**
> true. but the backtrace (for me) is very hard to generate, because the problem occurs randomly. 
And even when it occurs, no visible errors occur except a nearly frozen system.

You can just attach gdb to the problem gnome-panel process when the issue occurs.

---

### Post by plun on 2009-04-15
> **chrisccoulson said:**
> You can just attach gdb to the problem gnome-panel process when the issue occurs.

Can you please explain how.....???   with "human language".

My panel drops stone dead with kernel 2.6.30.

---

### Post by m2.g5ru6y7s on 2009-04-15
1) boot Ubuntu
2) please print the instructions of [https://wiki.edubuntu.org/Backtrace](https://wiki.edubuntu.org/Backtrace)
3) after booting and you are in the Desktop environment, press CTRL-ALT F1.

You come now in a terminal,
  (if this not occurs and the system is flipping back in the     graphical Desktop, please repeat step 3 quickly a couple of times)
Use the same login name and password as in your desktop session.

4) Follow the instructions of the topic 'Already running programs' of the printed document of step 2.
You have to find the process id of gnome-panel so you type :
pidof gnome-panel. Please use this number as the process id to debug.

Don't forget step 4 of the printed document (gdb) continue.

5) Go back into your Desktop environment by pressing ALT-F7 or ALT F9 (Sometimes the Desktop session is under ALT f9)

In your  Desktop environment please do all the things you normal do.

When the bug occurs, please press CTRL ALT F1 again to go back to your terminal.
press ctrl+c
Please follow now the steps 6 and beyond of the printed document to create the backtrace log.

---

### Post by plun on 2009-04-16
OK thanks...!

My tty is broken again...](*,)


I can see this with gdb running 
> 
Hangup detected on fd 0
Error detected on fd 0
error detected on stdin


It might also be a Kerneloops bug in my case. I am getting it with kernel 2.6.30-RC2.

EdIT

Putty...  ;)

---

### Post by m2.g5ru6y7s on 2009-04-16
You can recreate the TTY's:
su
[you are now root]
#/sbin/getty 38400 tty1&

[tty1 is created]

repeat for other missing tty's (up to 6 i believe)

---

### Post by plun on 2009-04-16
OK.. Putty is easier. ;)

but it seems to be empty

[http://paste.ubuntu.com/151992/](http://paste.ubuntu.com/151992/)

:confused:

---

### Post by m2.g5ru6y7s on 2009-04-16
Well, unfortunately I'm not technical enough to see if the output is useful or not.

The strange thing of this gnome-panel bug for me is, that since I attached the gdb debugger to the gnome-panel process, the bug does not occur anymore ... I have also noticed Sebastien Bacher of this [https://bugs.launchpad.net/ubuntu/+source/gnome-panel/+bug/332563](https://bugs.launchpad.net/ubuntu/+source/gnome-panel/+bug/332563) ). You can send the output you have to launcpad and ask if it's useful or not. Good luck!

---

