---
title: "F-Spot error after dist upgrade (amongst others)"
date: 2008-06-30
forum: Installation &amp; Upgrades
---

### Post by cfp on 2008-06-30
A computer I maintain was upgraded to Hardy Heron without my presence, and there are now a number of problems I'm working through. The most concrete one is that F-spot isn't loading and is giving the error:

:~$ f-spot
Starting new FSpot server
Unrecognized deviceID 258a
The program 'f-spot' received an X Window System error.
This probably reflects a bug in the program.
The error was 'BadAlloc (insufficient resources for operation)'.
  (Details: serial 381 error_code 11 request_code 159 minor_code 3)
  (Note to programmers: normally, X errors are reported asynchronously;
   that is, you will receive the error a while after causing it.
   To debug your program, run it with the --sync command line
   option to change this behavior. You can then get a meaningful
   backtrace from your debugger if you break on the gdk_x_error() function.)



Evolution is requiring password entrance on first open to unlock the key-ring, opening Nautilus windows is incredibly slow (even the home folder, though "browsing" using the terminal and ls is fine), and there's bizarre screen corruption across a block of the screen (not a hardware problem as started with the upgrade). The f-spot, key ring and Nautilus problems could perhaps all be explained by messed up file permissions?? though quite what files are missing what permissions I'm not sure.

Any help would be much appreciated,

Thanks in advance,

Tom

---

### Post by cfp on 2008-06-30
Sorted the evolution keyring problem. Resolution here for those finding this thread:

[http://www.uluga.ubuntuforums.org/showthread.php?t=320308&page=2](http://www.uluga.ubuntuforums.org/showthread.php?t=320308&page=2)

No progress on any of the others though. (Have edited the above post to change the F-spot error to the one it gives when started normally.)

---

### Post by cfp on 2008-06-30
The 0.0.0.0s look a bit omminous in the below...

$ f-spot -versions
F-Spot  0.4.3.1 - (c)2003-2008, Novell Inc
Personal photo management for the GNOME Desktop

.NET Version: 2.0.50727.42

Assembly Version Information:
	gconf-sharp (2.20.0.0)
	FSpot.Utils (0.0.0.0)
	gdk-sharp (2.12.0.0)
	gnome-vfs-sharp (2.20.0.0)
	Mono.Addins (0.3.0.0)
	NDesk.DBus.GLib (1.0.0.0)
	NDesk.DBus (1.0.0.0)
	System (2.0.0.0)
	Mono.Posix (2.0.0.0)
	Cms (0.0.0.0)
	FSpot.Core (0.0.0.0)
	atk-sharp (2.12.0.0)
	gtk-sharp (2.12.0.0)
	Mono.Addins.Setup (0.3.0.0)
	gnome-sharp (2.20.0.0)
	glib-sharp (2.12.0.0)
	f-spot (0.4.3.1)
	mscorlib (2.0.0.0)

---

### Post by cfp on 2008-06-30
[duplicate - deleted]

---

### Post by cfp on 2008-06-30
K, I've fixed the nautillus and screen corruption issues by reinstalling/reconfiguring gnome-desktop and xserver-xorg. So it's just this mystery f-spot problem remaining.

---

### Post by cfp on 2008-07-01
OK this is a GL issue. I've created a new thread for it since the original thread title is misleading. See here:

[http://ubuntuforums.org/showthread.php?p=5298654#post5298654](http://ubuntuforums.org/showthread.php?p=5298654#post5298654)

---

