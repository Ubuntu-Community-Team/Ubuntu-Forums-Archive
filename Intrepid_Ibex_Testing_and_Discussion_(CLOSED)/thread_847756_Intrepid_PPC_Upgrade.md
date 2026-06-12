---
title: "Intrepid PPC Upgrade"
date: 2008-07-02
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by BladeMelbourne on 2008-07-02
I'm just curious to know whether any PPC (G4) users have played with Intrepid yet? I upgraded to Hardy (from Gutsy) whilst it was in alpha (without issue), however upgrading the same system from Hardy to Intrepid turned out to be an epic failure for me.

GDM could not bring up X, so I installed KDM with apt-get which restored a login window. My desktop of choice (Xfce), would not load - it would just display the mouse background.
Then I installed IceWM with apt-get, and now I can login to that and execute Opera. Attempting to run Synaptic fails with a segfault.

An interesting message I saw in an xterm... this was compiled for a little endian system however this is a big endian system.

Anyway, my /home is on it's own partition, so I'm going to take copies of my yaboot.conf, xorg.conf, mysql db, etc. and blow away /.

I'm not upset or anything - this is kinda expected with bleeding edge. I just thought I would warn other PPC users to hold out on upgrading to Intrepid.

---

### Post by stream303 on 2008-07-03
Is Intrepid even available for PPC yet?  When Hardy came out, I had to wait past alpha and only saw PPC when it reached beta status.

As for Xubuntu / Xfce, have you looked at

/usr/share/xsessions/xfce4.desktop

and checked to see if the last line reads:

Exec=xfce4-session

Segfault with Synaptic?  Whoa, that sounds similar to another problem where a user would hang when trying to do a normal update, yet single application downloads would work...

---

