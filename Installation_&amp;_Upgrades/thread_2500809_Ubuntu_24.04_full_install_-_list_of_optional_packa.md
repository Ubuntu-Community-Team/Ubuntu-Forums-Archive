---
title: "Ubuntu 24.04 full install - list of optional packages"
date: 2024-09-12
forum: Installation &amp; Upgrades
---

### Post by davetheoldcoder on 2024-09-12
When I installed Ubuntu 24.04, I selected the option to do a minimal install. Is there a list of the specific packages that would have been included if I had selected the option to do the more complete install?

---

### Post by tea for one on 2024-09-12
There is a comprehensive manifest list here 
[https://releases.ubuntu.com/noble/ubuntu-24.04.1-desktop-amd64.manifest](https://releases.ubuntu.com/noble/ubuntu-24.04.1-desktop-amd64.manifest)

I don't think that there is a list of packages removed (or not included) during the minimal installation.

---

### Post by davetheoldcoder on 2024-09-12
Thanks, that's helpful. I didn't think to look there.  I'll hold off marking this as "solved" for a while, in case someone knows where to find a specific list.  I'll try to create my own list by using that file to make a script that does a "dpkg --status" on each of those packages, unless I think of a better way.

---

### Post by tea for one on 2024-09-12
I had a quick look around for more info and stumbled across this answer about seed files.
[https://askubuntu.com/questions/1511204/what-is-the-difference-between-ubuntu-24-04-default-minimal-installation-and-f](https://askubuntu.com/questions/1511204/what-is-the-difference-between-ubuntu-24-04-default-minimal-installation-and-f)
Any use?

---

### Post by davetheoldcoder on 2024-09-12
That looks like the answer.  Thanks!

---

