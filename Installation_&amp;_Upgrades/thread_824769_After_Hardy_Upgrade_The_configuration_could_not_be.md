---
title: "After Hardy Upgrade: The configuration could not be loaded"
date: 2008-06-10
forum: Installation &amp; Upgrades
---

### Post by akiark on 2008-06-10
I have just upgraded from gusty to Hardy, and when i try to open services-admin, time-admin, users-admin or network-admin, from the menu, i get the message :
> **The configuration could not be loaded**
You are not allowed to access the system configuration.

And from terminal:

> ** (network-admin:6815): CRITICAL **: Failed to execute program /usr/lib/dbus-1.0/dbus-daemon-launch-helper: Success

I think it's related to the policykit, but i dont find the way to fix it...

Thanks for the attention,
Alexis Rodriguez

---

### Post by chmorgan on 2008-06-22
> **akiark said:**
> I have just upgraded from gusty to Hardy, and when i try to open services-admin, time-admin, users-admin or network-admin, from the menu, i get the message :


And from terminal:



I think it's related to the policykit, but i dont find the way to fix it...

Thanks for the attention,
Alexis Rodriguez


I'm seeing the same thing here after a gutsy to hardy upgrade. Most people with this problem are reinstalling the OS which seems like a pretty severe way to fix things.

Chris

---

### Post by iponeverything on 2008-08-13
I had the same problem.

For me the issue was an incorrect group for:

usr/lib/dbus-1.0/dbus-daemon-launch-helper

once I changed it to "messagebus" all was good.

---
I did what no sane person should do, I copied the the sources over from a hardy machine to one with a knoppix disk install (a laptop) and did a dist-upgrade.

After fighting with the machine for 3 days I now have it to the point that I have no issues left to resolve.

mac

---

### Post by ralphmerridew on 2009-01-26
I'm having the same problem.  /usr/lib/dbus-1.0/dbus-deamon-launch-helper was already group messagebus.

-rwsr-xr-- 1 root messagebus 228628 2008-10-14 13:32 dbus-daemon-launch-helper

(Closely related side comment:  Is it possible to get XP to follow the rule of "system clock is GMT, but display local time"?)

---

