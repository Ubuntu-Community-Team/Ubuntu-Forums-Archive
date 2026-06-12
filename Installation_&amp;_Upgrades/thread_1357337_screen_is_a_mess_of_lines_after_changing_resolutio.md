---
title: "screen is a mess of lines after changing resolution"
date: 2009-12-17
forum: Installation &amp; Upgrades
---

### Post by maulynvia on 2009-12-17
Hi
have a new installation,was just working fine when I tried changing screen resolution (using eee pc tray) - one click later my screen is a mess of lines. I can't see or click anything.

Presumably I need to go into the shell and manually change the resolution back (ubuntu 9.04).

I'm a newb - I've figured out how to do crt + alt + f2 to get to the shell - but is this the right approach? What do I do next?

Help!

M

---

### Post by audiomick on 2009-12-17
You should be able to re-boot into safe graphics mode and change it back from there, I think.

---

### Post by maulynvia on 2009-12-17
NOW SOLVED!

Someone (at eeebuntu forum) suggested:
It's not an xorg problem. You have two options:
1) ctrl+alt+F2, cat "1024x600" > /var/eeepc/resolution_saved and reboot (or whatever your preferred resolution is.
2) Use xrandr to force it back to the right resolution. Something like: xrandr --output LVDS --auto --rotate normal --pos 0x0 --size 1024x600 (or whatever your preferred resolution is)


Using option 1 gave an error: no file "1024x600"
I didnt understand/dare option 2.

However this helped me google "eeepc/resolution_saved" to the solution:

sudo rm /var/eeepc/resolution_saved

(which I think removes the unwanted setting completely)

---

### Post by fewt on 2009-12-17
> **maulynvia said:**
> NOW SOLVED!

Someone (at eeebuntu forum) suggested:
It's not an xorg problem. You have two options:
1) ctrl+alt+F2, cat "1024x600" > /var/eeepc/resolution_saved and reboot (or whatever your preferred resolution is.
2) Use xrandr to force it back to the right resolution. Something like: xrandr --output LVDS --auto --rotate normal --pos 0x0 --size 1024x600 (or whatever your preferred resolution is)


Using option 1 gave an error: no file "1024x600"
I didnt understand/dare option 2.

However this helped me google "eeepc/resolution_saved" to the solution:

sudo rm /var/eeepc/resolution_saved

(which I think removes the unwanted setting completely)

It IS an xorg problem, however the problem trigger was the Eee PC Tray resolution switch.

---

### Post by efflandt on 2009-12-18
Just for future reference for your 1) attempted solution, you should have used **echo** instead of **cat**.

 cat "1024x600" > somefile would copy a file called 1024x600 (which does not exist) to somefile

echo "1024x600" > somefile would create somefile containing the string "1024x600"

---

