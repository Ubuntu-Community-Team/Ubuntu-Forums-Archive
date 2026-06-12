---
title: "Feisty fresh install, error after grub"
date: 2007-04-22
forum: Installation &amp; Upgrades
---

### Post by tehbizz on 2007-04-22
So I decided to be adventurous and install Feisty fresh over my 6.06 install.  I went through the whole install and rebooted only to see my num-lock and scroll-lock keys keys flashing and the boot obviously halted.  So I reboot, edit grub to remove 'splash' so I can get some info on just what the problem may be and here's what I'm so eagerly greeted with:

```

Starting up ...
Loading, please wait ...
....info for kinit/resume truncated.... (simply because I'm not typing out the full UUIDs)
kinit: No resume image, doing normal boot...
init: Error parsing configuration: No such file or directory
[    4.664000] Kernel panic - not syncing: Attempted to kill init!
[    4.664000] 

```

And booting is fully halted.  This is not the first time I've installed Ubuntu (or Debian for that matter) but it's the first time I've ever encountered this error before.  Everything worked flawlessly with Dapper (it was done with the alternative install), Breezy, Hoary, Debian Sid, and Debian Etch.  Booting the liveCD worked without a hitch as well...otherwise the install would have never completed.

This is actually the second install of Feisty I've done tonight after the first one yielded the same results.

Ideas?

EDIT: Hardware is nothing fancy.  It's a Dell 700m laptop with an IDE Hitachi 80GB drive and normal Intel parts.

---

### Post by pepsi_max2k on 2007-04-22
i've seen kernel panic type stuff before when i've had my bootloader configured wrongly. /boot/grub/menu.lst? could be the wrong kernel listed...

---

### Post by tehbizz on 2007-04-22
Hmm, my desktop disk must have been borked.  I just ran an alternate install and everything is working fine.

---

### Post by Bowel on 2007-10-02
I've also been struggling with this error. For me, it turned out to be caused by having a separate /etc-partition. I reported it as bug [#148331](https://bugs.launchpad.net/ubuntu/+bug/148331)

---

