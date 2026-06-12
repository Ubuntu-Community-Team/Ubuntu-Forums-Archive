---
title: "[&quot;SOLVED&quot;] Xfce4-power-manager not privileged to suspend/hibernate (minimal 12.04)"
date: 2013-05-27
forum: Installation &amp; Upgrades
---

### Post by rzeosz on 2013-05-27
Hi,

I'm in a very satisfying process of building my very on openbox based Ubuntu 12.04 LTS, starting from a minimal CD. However, I can't get suspend/hibernate options to work in the power manager. Suspending works for sure because when I try
```
sudo pm-suspend
```
it suspends my machine no problem at all. It won't work without sudo, so I presume it's all about granting access to that feature. How do I do that?

P.S. After installation I had no audio, and the solution was to edit /etc/group file and add my username to audio group. Maybe I can edit something there?

By the way, here's my ~/.config/openbox/autostart file
```
tint2 &
wicd-client --tray &
xfce4-power-manager &
xfce4-notifyd &
```
Maybe I'm missing some authentication daemon? However, WPA encrypted wi-fi works flawlessly without entering any passwords (apart from the WPA obviously).

Cheers,
Greg

EDIT: I'm not sure if this thread should go to desktop environments section. Sorry for the inconvenience, should it be moved.

---

### Post by ajgreeny on 2013-05-27
Hibernation was disabled from ubuntu (and xubuntu, kubuntu and lubuntu) 12.04, but can be easily re-enabled if you followthe instructions at [http://askubuntu.com/questions/94754/how-to-enable-hibernation](http://askubuntu.com/questions/94754/how-to-enable-hibernation).

---

### Post by rzeosz on 2013-05-27
Thank you, very useful link. I should've stressed though I'm more interested in suspending the system. Is there an analogous solution for that?

---

### Post by slickymaster on 2013-05-27
[Hybrid suspend with Ubuntu 12.04 (Precise Pangolin)]("http://blog.futurile.net/2012/07/14/hybrid-suspend-with-ubuntu-12-04-precise-pangolin/")
[Set up hybrid suspend in Ubuntu]("http://www.webupd8.org/2012/11/how-to-use-hybrid-suspend-in-ubuntu.html")

---

### Post by rzeosz on 2013-05-28
Thank you for your help lads. I am happy to report that I have found a solution. What I have done is:

1. Remove Ubuntu completely.
2. Install Debian Wheezy (netinst).
3. Install 3.9.4 Liquorix kernel.

Everything now works pretty much out of the box. No hard feelings - just a very suitable solution.

Regards,
Greg

---

