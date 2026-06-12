---
title: "Belarc Advisor equivalent for Linux?"
date: 2007-06-08
forum: Installation &amp; Upgrades
---

### Post by Shinobi326 on 2007-06-08
I miss having the capabilities to printout my system configuration.  Is there an equivalent program that we can use in Ubuntu that provides similar functionality?

---

### Post by jimmj43 on 2007-09-18
I just started to post the same question and was redirected here. Doesn't bode well when a question hangs unanswered for 5 months...

---

### Post by tomviolin on 2007-09-19
I'm sure all the information is sitting in /proc and/or lspci / lsusb / lsmod / etc.  It's just a matter of someone taking the time to write the thing.  I know I don't have the time, at least not right now. :(

---

### Post by SnakeHips on 2008-03-13
Have you tried "sysinfo" in terminal or synaptic ?

---

### Post by pwn2king on 2008-04-29
Has anyone tried using Belarc Advisor with WINE?

---

### Post by slibuntu on 2008-05-01
Not quite as polished as belarc advisor but a way to get all that info is by running this command - 

```
sudo lshw -html >> info.html
```


This will output a file called info.html to your home directory, just open it with firefox and you should have most of the info you need!

---

### Post by Aldenb on 2008-07-06
I'm having the same luck trying to run Belarc Advisor under WINE....it won't work.  There has to be someone out there with the expertise to get it to function.
Alden (K1HA@aol.com)

---

### Post by solitaire on 2008-07-06
Belarc was a life saver in my Pre Linux days! The amount of times i went to a client who lost all their Windows install disks including CD-Keys! Stick on BelArc and in a few seconds i have the CD key and full config for reference :D

A Linux version would be a bit harder (Since all the settings and info in windows were held in 4 or 5 *.DAT files that made up the registry!)

---

