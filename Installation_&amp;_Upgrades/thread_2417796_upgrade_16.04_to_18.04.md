---
title: "upgrade 16.04 to 18.04"
date: 2019-04-27
forum: Installation &amp; Upgrades
---

### Post by chpnp on 2019-04-27
Hi,

I have ubuntu 16.04 which when installing updates proposes to upgrade to 18.05.
I would like to do some upgrade,

2 questions
- is the automated upgrade clean enough, or is a clean install from scrach the preferred way ?
- my system is installed on a (luks) crypted partition. Should I worry about an automated upgrade to 18.04 ? and favor the manual install from scratch for that reason ?

Thanks !
best regards

---

### Post by dino99 on 2019-04-27
> is a clean install from scrach the preferred way ?  yes , always.

but you may prefer a manual dist-upgrade by upgrading /etc/apt/sources.list and synaptic. That is preferable if you still want to use a separate /home repertory and not a dir like now with new fresh install, as well for /swap.

At end , use gtkorphan and bleachbit (as root, carefully select settings) to clean the system of old packages/settings.

---

### Post by Impavidus on 2019-04-27
Difficult to say. For some people, like me, upgrades simply work. I click the button, read a book and the upgrade is ready. Maybe I have to modify some home-made software, but I'd have to do that as well if I had made a fresh install. For other people those upgrades never work.

---

### Post by oldfred on 2019-04-27
Upgrades often do not work as users do not uninstall all ppa and proprietary drivers.

But I prefer clean installs, as then you also do a major houseclean of old logs, dpkg lists and other cruft that builds up over time. If really good about housecleaning upgrade should be ok.

I also like to keep system separate from data.
Then when I change from last LTS version to next LTS version as new main working system, I still have the old install in another 25 or 30GB / partition.  I may also install, other versions just as tests, but stay with LTS versions as main working install.

---

### Post by Tadaen_Sylvermane on 2019-04-27
In the upgrades I have tried I've had some success, but not a guaranteed win every time. 2 attempts on desktop, 2 successes with the GUI upgrade tool. Server is another story. 5 upgrade attempts, 1 successful. The 4 failures required rolling back my lvm snapshots. All with do-release-upgrade. Admittedly I've never fully removed my ppa software so that could be my problem. I wrote a script to automate a chroot installation with debootstrap. Is how I upgrade the server now. I keep an extra 2 partitions as potential / for chroot installs. I debootstrap, configure, and reboot to the new partition.

One nice thing about the debootstrap method is you can fully configure before bringing the machine down. Takes a bit to configure but assuming you get it right downtime is minimal. Little more than a reboot.

---

### Post by chpnp on 2019-04-27
Ok t hanks.

One more. I was considering a clean install. System and Data are in 2 partition separately encrypted. Then I am finding the 18.04 disk does not allow to nstall in a chosen encrypted partition ( as was possible with 16.04).

Am I missing anything here ?
Thanks

---

### Post by chpnp on 2019-06-12
Thanks to those who replied.
As it turned out, the upgrade worked quite well but took hours 
and i mistakenly believed i could not install 18.04 on a Luks partition (while it worked - not sure why i missed that)

I probablly will reinstall my other machines rather than upgrading them.
thanks again

---

