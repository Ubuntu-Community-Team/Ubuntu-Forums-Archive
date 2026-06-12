---
title: "Managing SSH Host Keys in 20.04 Autoinstall/Cloud Init"
date: 2020-09-19
forum: Installation &amp; Upgrades
---

### Post by gr306 on 2020-09-19
I want to manage the generation of SSH host keys during a build of a 20.04 VM.

The default is that on first boot cloud-init deletes any host keys and creates fresh ones. The autoinstall docs don't talk about this. The cloud init docs talk about being able to use the "ssh_deletekeys: false" parameter to control this.

I've tried putting this at the top of my user-data file. i.e.

[FONT=courier new]#cloud-config
ssh_deletekeys: false
autoinstall:
...[/FONT]

That didn't work. I also tried manually adding it to the /target/var/lib/cloud/seed/nocloud-net/user-data prior to first reboot, but that didn't work either.
What am I doing wrong?

---

