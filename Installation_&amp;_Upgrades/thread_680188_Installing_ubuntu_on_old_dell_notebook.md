---
title: "Installing ubuntu on old dell notebook"
date: 2008-01-27
forum: Installation &amp; Upgrades
---

### Post by cf_linux on 2008-01-27
I am trying to install ubuntu on my old Inspiron 2600 that is currently running XP Home. When I reboot with the install CD in the drive, the install screen comes up. I select "Start or Instal Ubuntu", and the orange progress bar appears. But once the bar is full, the screen goes blank, the CD drive spins down, and nothing happens. I've waited hours at this point and still nothing has changed. Somebody please help.

---

### Post by digital_exhaust on 2008-01-27
What are your specs? Specifically, how much memory does it have?

---

### Post by Martin Witte on 2008-01-27
how much ram (internal memory) do you have? if it's less than 192 mb you have to use the alternate cd to install, see [https://help.ubuntu.com/community/Installation/SystemRequirements](https://help.ubuntu.com/community/Installation/SystemRequirements)

---

### Post by cf_linux on 2008-01-27
That might be the problem. My laptop only has 128mb RAM. How do I get the alternate CD?

---

### Post by digital_exhaust on 2008-01-27
Try Xubuntu using the alternate install cd.. I have it running nicely on an old Toughbook with 128m. I had tried Ubuntu, but it was *really* sluggish...

---

### Post by cf_linux on 2008-01-27
I'm having trouble finding the alternate CD. Is there a link someone could send?

---

### Post by digital_exhaust on 2008-01-27
[Here]("http://us.releases.ubuntu.com/7.10/") you go.. scroll down towards the bottom of the page and select the flavor you want...(and I'm assuming your in the US, if not, sorry... )

---

### Post by cf_linux on 2008-01-28
Thanks. I downloaded Xubuntu and it installed smoothly. However, when I boot my system, the progress bar loads and then I get a black screen with random vertical lines. How do I fix this?

---

### Post by mocoloco on 2008-01-28
I hate to backtrack you, but out of curiosity did you ever try on the live CD to do "Start Ubuntu in safe graphics mode?"

For your current issue, press Ctrl+Alt+F2, log in, then type 
```
sudo dpkg-reconfigure xserver-xorg
```
If you're not sure of any question just go with the default.  Hopefully that will set up your X correctly for your graphics card and monitor.

---

### Post by Glendon on 2008-07-14
I followed this on my Inspiron 2600 and it worked like a charm:

[Link]("http://www.apfrod.com/works/2008/03/15/ubuntu_8_04_hardy_heron_on_dell_inspiron_2600")

---

