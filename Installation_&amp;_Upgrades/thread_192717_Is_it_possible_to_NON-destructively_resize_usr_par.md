---
title: "Is it possible to NON-destructively resize /usr partition to allow for upgrade?"
date: 2006-06-09
forum: Installation &amp; Upgrades
---

### Post by SkyNet2029 on 2006-06-09
I am at a moral quandry: do i redo my entire installation for the sake of having a larger /usr partition? Or is there a non-destructive method to go about this? Prior to my Dapper upgrade from Breezy 5.10 (yes, with both KDE and gnome) I am sitting at 32% of usable file space in /usr partiton. I do not wish to redo this setup, as it currently is devoid of any orphaned libs/apps/ has no third-party packages installed. It is a very smooth running machine and rather quick for only 398MB (SD-Ram) on a K6-2 350Mhz. Via board. I want to know if there is a way to reallocate the existing 27.8 GB of disk space to sort of do an overlay to enable more files to migrate to my /usr folder. Again, I do not wish to reinstall this config. Any help would be appreciated. Thanks.! .....everthing works fine here, it's just from previous experience, the dist-upgrade to dapper uses almost a Gig and a half (remember-I have both Ubuntu-desktop and FULL KDE desktop installed). Thanks, thanks thanks. PLeaseeeEE help me!](*,) When I try to nuke the ubuntu-desktop all it seems to do is remove the metapackage, but eaves installed files alone/I would prefer to stick with the Kubuntu desktop environment simply because Gnome just stalls on loading -the menu bars show then die, ad nauseum.

---

### Post by glotz on 2006-06-09
See [http://www.psychocats.net/ubuntu/purekde](http://www.psychocats.net/ubuntu/purekde)

And post a screenshot of your System > Admin > Gnome partition editor
(use imageshack.us hosting for example)

---

### Post by DougC on 2006-06-09
I know you can resize a partition if you've created you partition on a LVM (Logical Volume Manager) disk, but I'm guessing you havn't done this. I don't know if it's possible just to make a linux partition bigger other wise.

---

### Post by glotz on 2006-06-09
I think it is, if the partition setup is suitable(, that is, the partition he'd like to resize is next to unallocated space or another partition he intends to reisize.) Booting onto a liveCD will enable edition / partition too (with gparted).

---

### Post by DougC on 2006-06-09
Yeah, quite possibly.

But if you try it make sure you've backed everything up! :)

---

### Post by glotz on 2006-06-09
Heeheehee...

---

### Post by SkyNet2029 on 2006-06-10
My partition editor only shows that I prefer to runpartitions side by side, with no space in between them.. Hence my question. What my thought were leaning towards is more of 'moving' all but the /boot partition over to the left (see diagram). Has anyone tried this and broken anything...yet

Splendidly cramped desktop (1260x1024)

[[IMG]http://img143.imageshack.us/img143/673/snapshot49lk.png[/IMG]](http://imageshack.us)

---

