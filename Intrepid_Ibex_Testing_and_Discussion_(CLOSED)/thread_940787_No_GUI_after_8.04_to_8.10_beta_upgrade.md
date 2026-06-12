---
title: "No GUI after 8.04 to 8.10 beta upgrade"
date: 2008-10-07
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by JohnsonMR on 2008-10-07
I've upgraded a laptop to 8.10 beta.  When I boot the boot process is not completing and stops at the text mode login.  

The text screen looks like this:

[I]Starting up ...
Loading, please wait...

Ubuntu intrepid (development branch) Mars tty1

Mars login:   * Starting NTP server ntpd[/I]

At this point it hangs, though I can hit a return and log in.  Where do I go from here?

---

### Post by yellowaeroplane on 2008-10-07
hey there, try running the command 
```
sudo /etc/init.d/gdm start
```
this will force the gui to start

If for some reason the window system never installed (like the server version) run this command to install it and then run the above command again to start it
```
sudo apt-get install x-window-system-core gnome-core
```

good luck!

---

### Post by spenny on 2008-10-20
I've tried this, but on doing the sudo apt-get part I get an "Inconsistency detected by ld.so: dl-fini.c: 195: _dl_fini: Assertion `ms !=0 || == nloaded' failed!" message and still no GUI, therefore.

---

### Post by jenamiles on 2008-10-23
I have a similar problem but with no errors showing.  I followed the suggested sudo apt-get install x-window-system-core gnome-core after the gdm start fails to work.  It all appears to work with no errors; however, after starting gdm, the system comes back "Starting GNOME Display Manager     [OK] but then goes to a command prompt.  The screen flickers once but no other visible signs of changes.  Ideas?  I'm still brand new to Ubuntu (Linux in general) and have a tx2500z.  I started going through the process of udpating all the drivers with the guides provided here and was having little success.  The post commented that many of the drivers packaged in 8.10 so I thought "Why not?!"  Silly me!  Any help would be appreciated.

Edited to add: further searching prompted me to check results from a sudo startx and then I get a fatal server error: no screen found (errno 111) unable to connect to X server.  

I resolved my issue booting into recovery mode and running an xfix.  Booted right up.  May want to try that.

Thanks,
Jen

---

### Post by gali98 on 2008-10-23
Try going into recovery mode and running those commands.
Kory

---

