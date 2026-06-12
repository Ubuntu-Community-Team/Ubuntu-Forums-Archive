---
title: "Failed getting release"
date: 2008-11-10
forum: Installation &amp; Upgrades
---

### Post by digambar.patankar on 2008-11-10
I have Ubuntu 8.04 installed in my system, and installed Image creator-.47
i am trying to create a project.but after giving progect path and selecting project (maccaslin ) platform it just hangs in order to create project chroot environment.and i am getting fallowing error when i am trying to execute debootsrap command.help in this regards 


-desktop: g~/Desktop/d/moblin-image-creator$ sudo image-creator 
Setting new status label: Creating the project chroot environment
--------Platform rootstrap creation try: 1 ----------
Execing command: debootstrap --arch lpia --include=apt --components=main,restricted,universe,multiverse gutsy /home/digambar/Desktop/d/moblin-image-creator/t1 [http://ports.ubuntu.com/ubuntu-ports/](http://ports.ubuntu.com/ubuntu-ports/)
I: Retrieving Release
E: Failed getting release file [http://ports.ubuntu.com/ubuntu-ports/dists/gutsy/Release](http://ports.ubuntu.com/ubuntu-ports/dists/gutsy/Release)
--------Platform rootstrap creation failed result: 1 ----------
--------For try: 1.  Sleeping for 30 seconds... -----------------
--------Platform rootstrap creation try: 2 ----------
Execing command: debootstrap --arch lpia --include=apt --components=main,restricted,universe,multiverse gutsy /home/digambar/Desktop/d/moblin-image-creator/t1 [http://ports.ubuntu.com/ubuntu-ports/](http://ports.ubuntu.com/ubuntu-ports/)
I: Retrieving Release
E: Failed getting release file [http://ports.ubuntu.com/ubuntu-ports/dists/gutsy/Release](http://ports.ubuntu.com/ubuntu-ports/dists/gutsy/Release)
--------Platform rootstrap creation failed result: 1 ----------
--------For try: 2.  Sleeping for 30 seconds... -----------------

---

