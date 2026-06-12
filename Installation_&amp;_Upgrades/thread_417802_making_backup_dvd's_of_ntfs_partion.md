---
title: "making backup dvd's of ntfs partion?"
date: 2007-04-21
forum: Installation &amp; Upgrades
---

### Post by cyberdemon on 2007-04-21
I am gong to give the spec's of my notebook first

Acer Aspire 5100-3019
AMD Turion 64 MK-36 (2ghz)
2GB Ram
ATI Radeion 1100
80 GB HD (upgrading to 160GB)

my system came with 3 partions

Partion1 restore partion ~7GB
Partion2 Windows Vista partion ~37GB
Partion3 Data Partion ~37 GB

I have repartitioned the data drive for ubuntu and have a duel boot system so my partions now look like this
Partion1 Restore partion
Partion2 Vista
Partion3 /
Partion4 Swap

I just got a new hardrive and would like to duel boot with this same configuration. my question is how do I go about cloning the restore partion to the new drive (don't really care about the vista partion haven't used it yet)

I have several External hardrives I can use however I would rather burn an image onto a few DVDs

Is there any linux software that can do this?

i just used this comand
dd if=/dev/hda1 | gzip -c | split -b 2000m - /mnt/backup.img.gz.

my terminal window has frozen... I hope it is actually working.

I have hopes that dd will suite my needs and allow me to burn these files to DVD and later restore them to hda1 

is there a better utility for this task?
what would you linux guru's do (besides completely dump vista)

Any and all help is greatly appreciated

---

### Post by cyberdemon on 2007-04-22
bump

---

### Post by Dominus Suus on 2007-07-26
I'm in the same boat.  I want to backup a Windows XP machine using dd to several DVDs (as there is about 40 gigs worth to backup) before I wipe and reload it.

Has anyone tried this and (emphasis on successfully) done it?

---

