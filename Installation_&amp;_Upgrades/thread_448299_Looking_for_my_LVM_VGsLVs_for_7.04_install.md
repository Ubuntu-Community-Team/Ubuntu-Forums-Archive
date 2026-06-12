---
title: "Looking for my LVM VGs/LVs for 7.04 install"
date: 2007-05-19
forum: Installation &amp; Upgrades
---

### Post by TimP on 2007-05-19
I have a machine running Ubuntu 5.10 server and I'm looking to re-install it with 7.04 server. I have everything but root and boot on LVM and I want to keep the current LVM structure and only format a few LVs while saving the rest (the bulk of the data). When I get to the partitioning screen on the 7.04 server install disc, it picks up the physical partitions that I use for LVM with no information on them (i.e. doesn't see them as LVM PVs) and therefore, the LVM options are disabled. I can set them to LVM PVs without formatting, but I have a feeling it's not going to recognize my VG or any LVs at the LVM dialog. If anyone has any experience installing 7.04 on an existing LVM setup, I'd appreciate some tips. I don't see anything in the setup so I'm wondering if I have to prep something on 5.10 before I install.

Thanks!

---

### Post by busfahrer on 2007-05-19
Hi, 

I'm not sure I understood your question correctly, so I'm gonna tell you about my setup here at home, which I think is what you meant:

I have a relatively small partition that holds my / file system. My /home filesystem (where I keep all my data) is stored on a large LVM VG. Now for the switch from Edgy to Feisty I decided to do a re-install instead of an upgrade.
The beauty of LVM is that I just could overwrite the (small) / partition with Feisty, and ignore the LVM containing partitions during the installation. When the installation was finished I just did apt-get install lvm2, and did a reboot. That was enough to get my VG back, automatically.

I hope that answers your question.
PS: I'm not sure if the version of LVM in use plays a role, but you should be fine as long as your existing setup is LVM2 (as opposed to LVM1).

Greetings, busfahrer

---

