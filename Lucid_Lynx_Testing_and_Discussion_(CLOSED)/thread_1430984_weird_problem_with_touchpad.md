---
title: "weird problem with touchpad"
date: 2010-03-16
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by giorsat on 2010-03-16
Hi. I have this strange problem on lucid using nvidia current drivers (I need them to run gnome-shell)
when I log in as user I usually disable the touch pad cause when I write this messes up cause I touch it. well, the problem is that when I disable it pushing the bottn (I have a hp dv 7 pavillion), it hangs xorg . the only solution is to ctrl alt F3 and when I'm in consolle xorg stats over...
never happened before, now it's routine. should I file a bug?

---

### Post by Zorael on 2010-03-16
Have you checked the logs at **/var/log/Xorg.0.log**? Perhaps they say something just as it hangs.

As a workaround you can disable it in software, such as by using the terminal xinput tool.
```
$ xinput set-int-prop '"SynPS/2 Synaptics TouchPad"' "Synaptics Off" 8 **1**
```
I think that should work. Change the last digit to 0 to enable it again.

---

