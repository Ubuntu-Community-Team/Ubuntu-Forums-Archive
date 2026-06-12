---
title: "Getting default Gnome desktop"
date: 2005-10-07
forum: Installation &amp; Upgrades
---

### Post by bullraiser on 2005-10-07
Hi,

  I am installing Ubuntu for the first time and everything was going good. I got few errors on base configuration and did a "dpkg --configure -a" and relogged in. Now that the Gnome panel is empty and not displaying the default layout.

  Does anyone have idea, how to get the default gnome display. So, I have to reconfigure or update gnome. Any help would be appreciated.

--Thanks

---

### Post by Alexander Kirillov on 2005-10-07
[QUOTE=bullraiser]Hi,

  I am installing Ubuntu for the first time and everything was going good. I got few errors on base configuration and did a "dpkg --configure -a" and relogged in. Now that the Gnome panel is empty and not displaying the default layout.

  Does anyone have idea, how to get the default gnome display. So, I have to reconfigure or update gnome. Any help would be appreciated.

--Thanks[/QUOTE]
form the command line or KDe - not from GNOME - try removing (or better, moving to a different location) ~/.gnome* and ~/.gconf* files/directories. They will be recreated with default values at next login.

---

### Post by bullraiser on 2005-10-08
Thanks and after i moved my ~/.gnome* and ~/.gconf*, I am now able to get the default Gnome display. This is my frist successfull installation of Ubuntu on my machine and glad that I got a wide & immediate reponse and support from this community.

I also need to monitor my computer for excess log generation and usuage. Do we have some built in tool to control the disk usuage and log monitor.

Cheers--

---

### Post by Alexander Kirillov on 2005-10-09
[QUOTE=bullraiser]Thanks and after i moved my ~/.gnome* and ~/.gconf*, I am now able to get the default Gnome display. This is my frist successfull installation of Ubuntu on my machine and glad that I got a wide & immediate reponse and support from this community.

I also need to monitor my computer for excess log generation and usuage. Do we have some built in tool to control the disk usuage and log monitor.

Cheers--[/QUOTE]
Logs: they are automatically "rotated", with old logs renamed and archived. It is done as a cron job. In all my 10 years of using Linux, I've never had to do anything manually with logs. 

For disk usage, there are some tools for limiting disk usage per user - is this what you want? Then search for "quota"

---

