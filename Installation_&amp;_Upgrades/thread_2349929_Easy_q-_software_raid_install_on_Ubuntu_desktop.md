---
title: "Easy q- software raid install on Ubuntu desktop?"
date: 2017-01-19
forum: Installation &amp; Upgrades
---

### Post by cincibluer6 on 2017-01-19
How do I handle this? The GUI installer isn't as robust as the server one for this kind of thing. The goal is a RAID 1. This is a build for a family member and I kinda want some redundancy because this will be on the cheap (not so much for saving data so much as saving time in case one dies.)

Can I use mdadm via the live disc before installing somehow? I tried in a VM and set up a mirror but am not sure how the GUI is gonna handle this, etc. and how I would save the config in /etc afterwards.

---

### Post by cincibluer6 on 2017-01-21
Found the solution (or multiple):

1) Install Ubuntu server and then just add the desktop
2) Install using the net installer (mini.iso is like 57 MB)- the text installer will allow you to configure the RAID, etc.
3) Use this guide- [http://askubuntu.com/questions/505446/how-to-install-ubuntu-14-04-with-raid-1-using-desktop-installer](http://askubuntu.com/questions/505446/how-to-install-ubuntu-14-04-with-raid-1-using-desktop-installer)
That guide still works as of 16.04 and I can verify the RAID is functioning as intended.

---

