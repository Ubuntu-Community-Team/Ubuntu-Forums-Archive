---
title: "how do you update/upgrade programs that didn't come &quot;out of the box"
date: 2018-05-03
forum: Installation &amp; Upgrades
---

### Post by Jorhel on 2018-05-03
hi,
I started with xubuntu 14.04 installed a few things through the sofware manager or apt-get function (Digikam, Kmymoney, libre office etc...) then I did a clean install of 16.04 and had to reinstall all those programs and realised that they had gone to a newer version so surely I could have upgraded them at some stage if I had been aware that the new version existed.

In the live and learn part of the process:

1) I discovered that when I saved all my files on a USB stick prior to reinstalling I should have also saved the database file for digikam file since I lost all my tags just as well I had not gone very far in the use of them, still ennoying...
2) Software installer does not work in the 16.04 version a common problem apparently that I solved by installing Synaptic instead.
3) I lost all the fonts that I had installed in Libre office so should have thought of saving that somewhere too...

Now I imagine there is a way to backup all those small changes because after a while I don't really remember what came with the package and what i modified down the track.

---

### Post by Xian on 2018-05-03
Without choosing to use a file backup program like Unison, Grsync or likewise:

         Keep /home on a separate partition and don't format it during a clean install
         Backup /usr/share/ contents to a removable device

That'll secure 99.9% of anything you'd ever need.

---

### Post by Impavidus on 2018-05-04
The database files for your pictures and maybe your fonts (depending on how you installed them) are in your home directory. Backup the entire directory and restore after installing the new release of Ubuntu, or simply use a /home partition.

If you manually install stuff system-wide, the best place to do so is in /usr/local/. Backup and restore that directory, or make it a separate partition.

Sometimes people manually install stuff in places like /usr/share, which is also used by stuff installed by the package manager, but I think its best to keep those separated. You don't want to overwrite anything put there by the package manager.

---

