---
title: "Unable to log in after apt-get"
date: 2005-03-21
forum: Installation &amp; Upgrades
---

### Post by g2devi on 2005-03-21
This morning, when I try to log in, gdm complains that something happened with wtmp and that the session lasted less than 10 seconds. It then logs me out. 

I left my machine on all week-end, so I don't know the exact time the problem started, but I did several apt-get updates this weekend to fix a "cannot upgrade" mplayer issue. At one point I did an apt-get on k3b to see if it was any good then uninstalled it and the KDE libraries. There is a possibility that I uninstalled one too many k-libraries, but from what I remember of what I uninstalled, this seems unlikely.

One thing that I noticed is that sound stopped working yesterday afternoon.

I've been using Warty without incident for several months, so it isn't an installation issue.

On Fedora, I'd be able to log in to console mode and debug the startx error messages until I figure out what went wrong, but I don't think that Ubuntu has any equivalent to "telinit 3", does it?

At this point, I'm stuck. I can't log in to fix or debug the problem.

Does anyone have any ideas what could have gone wrong or how to fix the problem?

Thanks in advance.

---

### Post by g2devi on 2005-03-21
Okay, I found the solution to the problem GDM login issue.

This morning, I found the problem just before I went to work, so I forgot that I still had virtual terminals available (ALT-CTRL-F1). I was able to log in and look at the .xsession-errors file. It indicated that it could not open .ICEauthority. Apparently, root was the owner. .bash_history was also owned by root. I changed the permissions back and I was able to log in again.

The question remains why .ICEauthority and .bash_history had root permissions. When I ran K3B, it said that it didn't have permission to write to CD to I ran K3B through sudo. I'm guessing that this somehow messed things up.

I still have no sound, but given the above permission problem, I'm guessing that it may be related.

---

