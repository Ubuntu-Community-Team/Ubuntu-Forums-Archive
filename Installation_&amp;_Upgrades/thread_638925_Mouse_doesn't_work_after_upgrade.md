---
title: "Mouse doesn't work after upgrade"
date: 2007-12-12
forum: Installation &amp; Upgrades
---

### Post by John Franklin on 2007-12-12
I've just upgraded from 6.04 to 6.10 and my mouse no longer works properly. Jumping all over the place so that it's impossible to select anything. Also the keyboard is repeating characters.

I then decided to continue the upgrade to 7.04 (eventually I need to get to 7.10) to see if that would fix it, but the problem is the same. 

The system's unusable like this. What can I do? As an almost newbie to Linux I'm not yet familiar with what does what, so I need some assistance to solve this.

Many thanks.

---

### Post by tajreed on 2007-12-12
do a clean install of 7.1. Download the iso and burn an install disk.Continuous upgrades can be problematic.

---

### Post by Sims2789 on 2007-12-12
If you need help burning the iso, right-click it after you download it and select Write to Disc...

I hope your mouse can do this. ;-)

---

### Post by John Franklin on 2007-12-13
I was hoping not to do a clean install to save having to reload and reconfigure programs and data (notwithstanding that I could back up data and known config files). Does a clean install wipe everything or just the operating system (i.e. how different is it in wider impact to doing sequential upgrades)?

I would stilll prefer just to fix the mouse problem - the rest of the upgrade seems to have gone OK.

---

### Post by Partyboi2 on 2007-12-13
you could try to reconfigure xorg and see if that helps.
```
sudo dpkg-reconfigure xserver-xorg
```
If you haven't done this before its pretty easy, if you are unsure about something just use the default setting.
If you were to do a clean install you would loose everything. One way around it is to move your /home to its own partition. That way when you go to reinstall you will not loose all your Documents and settings.
Have a look at this:
[http://psychocats.net/ubuntu/separatehome](http://psychocats.net/ubuntu/separatehome)

---

### Post by John Franklin on 2007-12-13
Further investigation has shown the problem to be associated with my KVM switch (Starview SV411). With mouse plugged direct into the computer all is well, plugged via the KVM it isn't. It works with Windows and worked with Dapper, but not since. I've tried more than one mouse/track ball but the problem seems to be associated with the KVM/Ubuntu interface. How do I find what's changed here since Dapper? And how do I change the mouse driver, in case that's the problem?

---

