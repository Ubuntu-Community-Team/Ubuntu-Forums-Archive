---
title: "Apt-mirror w/GPG error and need to remove the partners repo"
date: 2010-07-28
forum: Installation &amp; Upgrades
---

### Post by JackD on 2010-07-28
I'm setting up a local apt-mirror repository on a USB drive, so upgrade systems in Kenya when I visit next week.

The standard Lucid repos copied over so nicely, that I decided to try adding in the Partners repo. That has turned out to be problematic.

- Now, if I try and use the mirror archives from a USB drive on a test system, I'm prompted about a GPG failure.

Either 

- (1) I need to know how to get which key, and how to add it to the receiving workstation
- (2) Or I need to remove the Partners repo. However, apt-mirror doesn't pull in the Partners to a separate /mirror/archive.ubuntu.com/ubuntu/dists directory. Medibuntu works fine, so I find this puzzling.

---

