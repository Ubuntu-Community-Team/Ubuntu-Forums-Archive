---
title: "Ubuntu Patching Question"
date: 2024-05-21
forum: Installation &amp; Upgrades
---

### Post by reteer on 2024-05-21
Hi I administer several kubernetes clusters, 4 total that run on Ubuntu 20.04 LTS and am trying to get a patching procedure together. 
I want to patch each cluster of Ubuntu servers one at a time, two weeks apart. 
I want to use this mini-string of commands to do so:
sudo -s -- <<EOF
apt-get update
apt-get upgrade -y
apt-get full-upgrade -y
apt-get autoremove -y
apt-get autoclean -y
EOF

What I really want to do is change the apt-get upgrade command to apt-get upgrade --download-only and do this on all the nodes in each cluster all at once.
Then when I'm ready to install these packages on each cluster it only installs what was downloaded. I understand to do that I have to use apt-get upgrade --no-download --ignore missing.

So my real question is how would that work if I want to use the apt-get full-upgrade command also? So these clusters are going to be patched 2 weeks apart how do I insure that they get
the exact same full-upgrades? Does it do the full-upgrade based on what was downloaded by the apt-get upgrade --download-only command?

---

### Post by TheFu on 2024-05-21
I don't think that is possible unless you completely replace all repos with repos under your control and you don't allow the local repos to be updated.  I have no idea how to accomplish this. Sorry.

I have an apt-cacher-ng server on our LAN and we patch weekly (usually early Saturday mornings).  For 20 system, it takes about 20 minutes total, unless a reboot is needed.  I'll usually do the reboots on Sunday morning.

I don't think there's any need to do both upgrade & full-upgrade.  Perhaps the manpage will clarify the results for you.

I have a script that loops over all my VMs and LXC containers, remotes into each and runs the update/upgrade on each, logging everything to a single file on my main workstation.  I looked at having ansible handle it. We use ansible, but for something like this, a simple script that I wrote in 2005 and barely touched since then has worked.

Then I have another script that does the autoremove/autoclean, which gets run after all is completed, including the reboots that are needed, if needed.  I want to delay those a bit - got burned about a decade ago by removing/cleaning too fast.  With an apt-cacher-ng server, the packages only get pulled down once per release/package, so updates for any other systems are really fast.  But apt-cacher-ng is setup as a cache. If there's a newer package, it will get pulled down for the systems that need it.

Sorry, I don't have any good answers.  Perhaps if you look at treating these systems like they are air-gapped, that might work better?

---

### Post by reteer on 2024-05-22
can I just use apt-get upgrade and not worry doing a full upgrade?

---

### Post by TheFu on 2024-05-22
> **reteer said:**
> can I just use apt-get upgrade and not worry doing a full upgrade?

It depends.  Or you could just do an **apt-get full-upgrade** and then it won't matter.  Full-upgrade is how to move from  

xx.yy.1 ---> xx.yy.2 ---> xx.yy.3 

So there is a support question.  Kernels for each .Release don't have unlimited support.  Generally, the first kernel has support for the 5 or 10 yrs of the LTS.  The .1, .2, .3, .4, .5 and .6 kernels only retain support until the next .dot release happens.  Then we are expected to move to that next release via full-upgrade.  There's a graph/chart showing this support model somewhere on Ubuntu.com.  Google for it.  If I can find it in 10 seconds, I'll post the link.  Nope. Didn't find it.

---

