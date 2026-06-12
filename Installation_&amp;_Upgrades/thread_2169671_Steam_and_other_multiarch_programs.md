---
title: "Steam and other multiarch programs"
date: 2013-08-23
forum: Installation &amp; Upgrades
---

### Post by joseph5 on 2013-08-23
I installed multiarch then installed steam, later I wanted to remove steam but of course no uninstall bash and when running sudo apt-get remove steam I got "Package steam:i386 is not installed, so not removed" as I am sure many have so I tried with --force-i386 and even steam:i386 but still nothing.

I am sure this is a common problem for most people trying to remove a multiarch program and I am sure someone already found the solution but for me for those that are stuck the solution that worked for me

```
sudo apt-get remove steam:*
``` with that command it looked in the registry and discovered 3 entires and it sucessfully removed leaving nothing behind...just thought I would share this with the community incase someone else is having problems.

---

