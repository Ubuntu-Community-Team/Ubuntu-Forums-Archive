---
title: "The program 'apt-get' is not currently installed"
date: 2007-04-20
forum: Installation &amp; Upgrades
---

### Post by AusIV4 on 2007-04-20
I just finished trying to upgrade Kubuntu, and as it was nearing the end, the update manager crashed. When I tried to restart, I'm now getting a notice that says:

The program 'apt-get' is not currently installed. You can install it by typing: apt-get install apt.

Needless to say, this presents a bit of a conundrum.

Is there any fix to this, or should I just be glad I backed up?

---

### Post by MetalMusicAddict on 2007-04-20
Do you also sit at a root prompt?

---

### Post by pepsi_max2k on 2007-04-20
>> apt-get install apt

lol, that was my first thought when i read the title :roll:

you should be able to download the apt package from a repo manually through http then install it... some how... as long as apt isn't the only installer available :|

---

### Post by JoshHendo on 2007-04-20
[http://packages.ubuntu.com/feisty/base/apt](http://packages.ubuntu.com/feisty/base/apt)
(replace feisty in the url with the name of the version you are using if you arn't using feisty)

Download the deb packages from there and see if you are able to install them :)

(Direct link for i386: [http://packages.ubuntu.com/cgi-bin/download.pl?arch=i386&file=pool%2Fmain%2Fa%2Fapt%2Fapt_0.6.46.4ubuntu10_i386.deb&md5sum=443c5f7f5ca9adce4394de2a035dd7ee&arch=i386&type=main](http://packages.ubuntu.com/cgi-bin/download.pl?arch=i386&file=pool%2Fmain%2Fa%2Fapt%2Fapt_0.6.46.4ubuntu10_i386.deb&md5sum=443c5f7f5ca9adce4394de2a035dd7ee&arch=i386&type=main) )

- Josh

---

### Post by MetalMusicAddict on 2007-04-20
If I'm right just installing the apt.deb wont help. Its a issue with the partitions.

Im willing to bet the partitions are defined one way in the fstab or GRUB and now after upgrade they are being seen another.

I noticed this when installing Feisty on my server. I hit this same issue and others if I didn't define each drive/partition on install.

I got all kinds of crazyness.

---

### Post by AusIV4 on 2007-04-20
Turns out if I type exit, it continues to KDE, and the virtual terminals use apt just fine. I also found that my swap partition was no longer active after the upgrade.

---

