---
title: "Since 19.04 Upgrade System Locks Up Daily and Restart Hangs"
date: 2019-05-13
forum: Installation &amp; Upgrades
---

### Post by scpatl4now on 2019-05-13
I upgraded to 19.04 a couple of weeks ago from 18.04 (via 18.10) and have been experiencing system lockups where everything freezes and I have to restart system.  When I restart it hangs while starting all the services (Usually Gnome Desktop Manager...but not always).  I have to literally power the whole thing down and start back up to get it to boot.  I have been looking at the log files and see this error

sender : lircd
Error: No /sys/class/rc/ devices found

It repeats hundreds of times even while the system is up.  I could find almost nothing about it online
(in the 20 mins since I posted this it now appears 2250 times)
My system is as follows
AMD Ryzen 7 1700x eight core
Nvidia GeForce GTX 1050 Ti/PCIe/SSE2 
Driver 418.56
32 Gigs Memory

It happens when I am working on the system and sometimes when its idle.  I dont know where to look so if there is more information I can provide let me know and I will do so
I'm considering a clean install and just reinstalling what I need but would rather avoid that if possible

---

### Post by dino99 on 2019-05-14
From the rescue grub mode, use the command line to clean the system first (clean/autoclean/autoremove) if you have not already done it.

---

### Post by scpatl4now on 2019-05-14
I had tried that.  Going to do a clean install today and see if that fixes it.  I usually always do a clean install...why I didnt this time, I dont know.  Guess you have to re-learn these lessons from time to time.  I've never had success with upgrades.  I'll post later if this solves my problem

---

### Post by scpatl4now on 2019-05-14
Finished clean install and reinstalled any apps I needed, and 2 restarts since no hangs...so here is hoping I'm good at this point

---

### Post by scpatl4now on 2019-05-14
I ran boot-repair to get system summery if that helps

[https://paste.ubuntu.com/p/VzxsCgQz4Z/](https://paste.ubuntu.com/p/VzxsCgQz4Z/)

---

### Post by scpatl4now on 2019-05-16
It just happened again but I was able to get the last 2 log entries

systemd-udevd.service: Killing process 477 (systemd-udevd) with signal SIGABRT.
systemd-udevd.service: Watchdog timeout (limit 3min)!

This is happening on a daily basis...sometimes multiple times

---

### Post by scpatl4now on 2019-05-27
I finally fixed this myself by looking around elsewhere.  Seems you have to disable Wayland in

 sudo gedit /etc/gdm3/custom.conf

and remove the # in front of
#Wayland = false
to
Wayland = false

I've had 3 successful boots so I'm guessing that solved it

---

