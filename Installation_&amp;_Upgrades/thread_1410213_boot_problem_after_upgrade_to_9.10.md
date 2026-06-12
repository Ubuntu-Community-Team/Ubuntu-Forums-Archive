---
title: "boot problem after upgrade to 9.10"
date: 2010-02-18
forum: Installation &amp; Upgrades
---

### Post by ubuscout on 2010-02-18
"Houston we have a problem... a BIG problem !" :-(

I was happy with my Jaunty on my Asus X53 with ati radeon hd2600 and restricted driver, until two hours ago...

I've started (after a long wait) to upgrade my Jaunty, everything was fine after upgrade, but I've noticed video was running with "ubuntu driver" and 3d wasn't available, so I started to install a fresh release of ati driver. But before I've saw in /usr/share/ati the previous copy of my restricted driver so before install the fresh copy I've run "sh ./fglrx-uninstall.sh" it had remove all telling me there wasn't any istance of fglrx (of course I thought...) ...and so before start with new installation I've thought about a reboot for first, but after it I'm unable to boot...

from normal boot it simply hang after a while, I think when it try to initialize video card...

...but more worse, also after choice recovery option at grub loader it hang after a bit, without give me any prompt... :(

I haven't any copy of ubuntu 9.10 with me now... :(


Any advice ?! I need really help !
thx

---

### Post by ubuscout on 2010-02-18
toc toc...

...could anyone help me ?! I need it really... :(

---

### Post by ubuscout on 2010-02-19
Hi people, this is my last call, so I hope someone can help me...

Now I 've got both cd (ubuntu desktop an alternate), I've boot with first and I have:
-mount hd root in /mnt
-sudo chroot /mnt
-sudo apt-get remove --purge xserver-xorg
-sudo apt-get install xserver-xorg
and reboot... but nothing happen... X doesn't start in normal mode and in recovery mode it hang after a bit...

(nb. by live cd everything load fine.)

...could really anyone help me plz ?!?

thx

---

