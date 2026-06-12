---
title: "Feisty upgrade broke my installation ..."
date: 2007-04-29
forum: Installation &amp; Upgrades
---

### Post by NickR1999 on 2007-04-29
Hello all! Any help would be appreciated. :confused: 

Basically, the upgrade got interrupted, and left my system in an inconsistent state.

My reboot hangs at the progress bar, then drops into the initramfs shell and prompt.

To fix, I tried to follow the instructions that had me boot using a LiveCD, opening up a terminal,
remounting my old root, chrooting to it, then doing the following:

  apt-get  clean
  apt-get -f update
  apt-get -f upgrade
  apt-get -f dist-upgrade
then,
  apt-get -f install

This all works except for the last step, The install fails because of 2 packages: bluez-utils and gaim. There,
the failure stems from the fact that the bluetooth services are not running under the LiveCD, and so the 'stop' that dpkg runs in its pre-remove script fails. Sigh! I have tried also using the -m option (ignore-missing). No dice: it tells me to use the -f option! I cannot remove the offending package either, since this reproduces the same obstacle.

Basically, I need a totalitarian --force option: which does not seem to exist. Or I need to disable the processing for specific packages. Or I need something that is beyond my current knowledge and/or imagination.

Thanks!

---

### Post by NickR1999 on 2007-04-29
Forgive me!

No sooner had I posted this request for help than I remembered to boot into the GRUB menu.

There, I was able to choose the previous version of the kernel, and am running my apt-get -f install now!

---

