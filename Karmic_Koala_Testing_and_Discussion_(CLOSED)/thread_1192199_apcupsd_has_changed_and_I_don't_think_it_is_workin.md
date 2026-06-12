---
title: "apcupsd has changed and I don't think it is working"
date: 2009-06-19
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by ranch hand on 2009-06-19
I have my doubts about this working because I do not see the "on battery power" tab in System->Preferences->Power Management.

When I pull that up and check the box for "always show icon" I just get the Plugged In icon.  I do not get the UPS/Battery icon.

I reallize this is a new version as I have never had to edit any files to get it to work before (8.04, 8.10, 9.04) on this box.

I have no idea what I need to do about this.  I pulled up the man page and pulled up the /etc/apcupsd/apcupsd.conf file (listed in man page as /etc/apcupsd.conf) and it looked like it ought to work to me.

I am using an APC Smart-UPS 1500 on the box in my sig, and on 9.10A2.

Besides some problems multi-booting with grub2 this is the only real problem I have found in 9.10.

---

### Post by taavikko on 2009-06-20
> **ranch hand said:**
> 
Besides some problems multi-booting with grub2 this is the only real problem I have found in 9.10.

apcups comes from "universe" and it's not really officially supported software, hence not really a problem with 9.10.

All you can do is to raise awareness on maintainers/upstream thet the issue might someday get resolved.

---

### Post by ranch hand on 2009-06-20
Ah, then I do not believe I will worry about it.

It works great on all the others, APC is the main UPS out there, it will work I am sure.

It is doing its job anyway.  The bells and whistles are not working.

Everyone should have one of these.

---

