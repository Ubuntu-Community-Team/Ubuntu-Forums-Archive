---
title: "Thunderbird problem--only after updating system"
date: 2008-01-01
forum: Installation &amp; Upgrades
---

### Post by metasonix on 2008-01-01
Here's a good one for you:

I have used Ubuntu Dapper for the last 2 years with hardly any problems. Thunderbird 1.5.0.10 was the email program, it never gave ANY trouble....until today.

Today, I updated the system using the normal Update Manager. And now, Thunderbird won't start. Running it from a terminal gives this:

DOUBLE-CLICK: 400 --> -1 THRESHOLD: 8 --> -1 /usr/lib/mozilla-thunderbird/run-mozilla.sh: line 131:  6802 Floating point exception"$prog" ${1+"$@"}

I uninstalled and reinstalled it. I installed Thunderbird 2.0 using the Ubuntuzilla installer. I removed it, then reinstalled 1.5. I even removed SCIM, because there were a few people complaining it interfered with Thunderbird 2.0.
 
No change. Still won't start. I can run it with gksudo, but that's not recommended. If I run it with gksudo, it won't find my address book or folders anyway.....

It appears that I will be using Evolution on this machine from now on. If only I could import my old sent messages....any suggestions for fixing Thunderbird, or whatever is causing it to crash?

---

### Post by foolsh on 2008-01-01
Often just uninstalling something leaves tidbits of the package lying around on the hard drive
try 
```
sudo aptitude purge thunderbird
```
then reinstall it
hope that helps

---

### Post by metasonix on 2008-01-06
I did the purge--it worked! I was able to reinstall and everything was ok--it even reaccessed my mail folders.

Unfortunately, the update also killed my Evolution program.....same thing, it won't start.

---

