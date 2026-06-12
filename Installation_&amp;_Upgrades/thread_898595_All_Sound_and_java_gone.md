---
title: "All Sound and java gone"
date: 2008-08-23
forum: Installation &amp; Upgrades
---

### Post by tonu on 2008-08-23
Upgraded from 7.10 to 8.04 via the internet.

The "new" configuration worked well until I allowed a system update (forgot which one), then ALL sound failed including the login and start-up theme and also Youtube clips, etc., are soundless.

Later discovered that Java had failed as well.

Have a "HD removable rack" system, so, changed to WinXp DH and sound/Java OK. Used various live DVDs and again all OK!

Can I just reformat the sda1 partition and reinstall 8.04 from a .iso DVD?
Would this affect the home partition -ie., lose all my data?

tonu@tonu-desktop:~$ df -h / /home
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda1              12G  3.7G  7.7G  33% /
/dev/sda3              60G  3.8G   53G   7% /home

---

### Post by pfdevil on 2008-08-23
Open up your sound manager, start playing an mp3 file and start moving the master volume slider up and down, while also trying al the other sliders. Sometimes Ubuntu screws things up in there and needs a little convincing for it to kick in.

---

### Post by tonu on 2008-08-28
Thanks, but being a newbie, in 8.04, what sound manager and how do I find it?

---

### Post by pfdevil on 2008-08-31
Hey right click on the sound icon on the top right taskbar. Select open volume control and continue with my first post.

---

