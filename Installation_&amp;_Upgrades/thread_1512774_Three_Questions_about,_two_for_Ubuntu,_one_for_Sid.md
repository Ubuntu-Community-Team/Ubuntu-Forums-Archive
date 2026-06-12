---
title: "Three Questions about, two for Ubuntu, one for Sidux"
date: 2010-06-18
forum: Installation &amp; Upgrades
---

### Post by Lolpanda on 2010-06-18
Just three quick questions for you guys, 

1) Whenever a new release of Ubuntu comes out, I've always done a full replacement (Booted up live CD, formatted / and formatted /home) to ensure there's zero incompatibilities, including configuration files in my /home. That has, finally, gotten annoying and I was wondering what the actual chances of a configuration file causing problems was in the 6 months that Ubuntu was released in. Also, special consideration for Gnome 3 (aka gnome-shell) coming out with the current gnome configs. 

2) Any way to remove unneeded config files automatically? I don't always use purge when I remove a package just in case I want to reinstall it, well weeks later I def don't want it, is there an apt or dpkg command that will automatically remove them after the package is gone? I know autoclean and autoremove handle orphans and unneeded .deb's

3) How stable is Sidux in reality? Ran it in a VM and had a few errors every so often while using it, but i wasnt sure how much of that was the fact it was a VM. Some say its stable enough for daily use, some say it breaks every other day

---

### Post by Lolpanda on 2010-06-19
question 2 has been answered by myself, question 3 has been answered. Question one is still up in the air and looking for an answer.


Shameless little bump

---

### Post by snowpine on 2010-06-20
1) You do not need to reinstall Ubuntu every 6 months. You can upgrade by following the instructions on this page: [https://help.ubuntu.com/community/UpgradeNotes](https://help.ubuntu.com/community/UpgradeNotes)

2) Not sure the answer to this one. :)

3) I have found sidux to be at least as stable as Ubuntu. The difference however is that you need to carefully read [the sidux manual]("http://manual.sidux.com") and [upgrade warnings]("http://sidux.com/index.php?name=PNphpBB2&file=viewforum&f=29") to have long-term success with the distro. (You shouldn't just enable automatic updates like a lot of Ubuntu users do.) sidux developers have extensive experience with Debian Unstable and you would be foolish to disregard their advice (for example their warnings to quit X for dist-upgrade, don't use Synaptic, etc).

---

