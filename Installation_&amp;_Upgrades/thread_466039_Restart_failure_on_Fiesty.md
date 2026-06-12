---
title: "Restart failure on Fiesty"
date: 2007-06-06
forum: Installation &amp; Upgrades
---

### Post by dld on 2007-06-06
I run a dual boot (XP and Ubuntu) system.  Since upgrading to Fiesty,
switching to XP is a pain.  Restart doesn't; it hangs with an empty
Ubuntu screen.  I have to power down and up to restart the machine
(Dell XPS 410) and select XP.  Any ideas?  Could I get the old Edgy 
code back?

---

### Post by sjardim on 2007-06-07
> **dld said:**
> I run a dual boot (XP and Ubuntu) system.  Since upgrading to Fiesty,
switching to XP is a pain.  Restart doesn't; it hangs with an empty
Ubuntu screen.  I have to power down and up to restart the machine
(Dell XPS 410) and select XP.  Any ideas?  Could I get the old Edgy 
code back?

I was having a similar problem until this hour ago. This blank screen you said appears after you log in the welcome screen?

In my case, the problem occurred after I updated the kernel, on Feisty, to the 20-16 release and reboot. When I logged in, a blank screen with a small white one (in the upper left corner of the screen) appeared and the system froze.

I found out that was a network interface problem! Two days ago I was setting my wireless card and I made some changes to the /etc/network/interfaces file. So, I just removed the settings for the wireless connection and voilá.

I hope this give you some clue. :)

p.s. If the X freezes, hit control + alt + backspace and it'll restart. And in the welcome screen, you can reboot by selecting this option.

---

