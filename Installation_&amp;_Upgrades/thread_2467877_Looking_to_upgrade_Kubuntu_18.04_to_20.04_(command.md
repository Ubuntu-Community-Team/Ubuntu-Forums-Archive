---
title: "Looking to upgrade Kubuntu 18.04 to 20.04 (command line)"
date: 2021-10-11
forum: Installation &amp; Upgrades
---

### Post by operator-error on 2021-10-11
I'd like to upgrade my system from Kubuntu 18.04 to 20.04 via the command line. What I've found is the following:

sudo apt update && apt upgrade
(reboot system)
sudo do-release-upgrade -m desktop

My big question is that will my KDE/Plasma desktop environment be preserved, or will it be overwritten with the "vanilla" Ubuntu (Unity???) desktop environment?

Or, is are there different commands for a Kubuntu (KDE/Plasma) system? Thanks in advance.

---

### Post by operator-error on 2021-10-11
My other question is will my partition setup be preserved? I keep my /home directory in it's own partition.

---

### Post by deadflowr on 2021-10-11
It won't install Ubuntu's desktop.
It won't change your partitioning scheme.

I hope you have read through the Kubuntu release notes to see what will be changed?
[https://wiki.ubuntu.com/FocalFossa/ReleaseNotes/Kubuntu]("https://wiki.ubuntu.com/FocalFossa/ReleaseNotes/Kubuntu")

---

### Post by operator-error on 2021-10-11
Thanks for your response. I haven't yet read the release notes. I'll do so now. Thanks again for your reply.

---

