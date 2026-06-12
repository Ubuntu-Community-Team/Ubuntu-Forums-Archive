---
title: "Gnome display problems with Intrepid Ibex"
date: 2008-10-29
forum: Installation &amp; Upgrades
---

### Post by jamescw4406 on 2008-10-29
I just upgraded from Hardy.  I get a logon screen, enter my password, and no Gnome, just the blank tan background (can't use the keyboard to get a shell or a run command).  SSH from another machine on my LAN shows that X is running ("active for display 0").  I'm not familiar with HAL but, according to my inexpert reading of my my xorg.conf file, Intrepid correctly identified my NVIDIA graphics card but not my monitor.  I have a rather weird 19" ASUS monitor with a 1400 X 900 resolution. I could probably find the Windows drivers CD for the monitor, if that would help. 

Do I need to reinstall the upgrade or are there some more focused remedies I can try?

Thanks.

---

### Post by cariboo on 2008-10-29
Restart in recovery mode and when you get to the menu choose xfix.

This will try to reconfigure xorg.conf

Jim

---

### Post by jamescw4406 on 2008-10-29
xfix wasn't successful.  I need to keep working on this.  Thanks.

---

