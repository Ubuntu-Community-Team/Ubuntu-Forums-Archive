---
title: "installing with separate home drive"
date: 2017-09-22
forum: Installation &amp; Upgrades
---

### Post by shoeleshunter78 on 2017-09-22
I have /home on a separate HDD. I wish to reinstall my system when I upgrade from 17.04 to 17.10. I will do this by unmounting the home HDD, installing Ubuntu, then mounting the /home HDD again.

My question-- configuration files under /home, for instance .KDE and .config, will be those of the older software versions. How will these files be treated when settings exist that no longer pertain to the newest releases of the programs they reference?

---

### Post by oldfred on 2017-09-22
Probably better to use Something Else and choosing existing / (root) as new root and existing /home as new /home but being sure NOT to check the format option. 

Be sure to have good backups which you should normally have anyway.

I have all data in a separate /mnt/data, so my /home is tiny with mostly hidden settings. So I keep it inside / and then create a new / for new install. So I have old install to revert back to if major issues with new install. I partition about 25GB for / and have used 8.3GB for my 16.04 install.

---

### Post by SeijiSensei on 2017-09-22
I doubt simply upgrading from 17.04 to 17.10 will wreak havoc with configuration files.  KDE had a major change between versions four (Kubuntu 14.04) and five (16.04), but that's all behind you.  You can take a more complicated route if you prefer. Let Kubuntu create a new /home/user directory for you inside the root partition.  Then back up the configurations in the old /home/user and replace them with the new ones.  Then try mounting the device as /home.

---

### Post by shoeleshunter78 on 2017-09-25
if I mount /dev/sdb at /home during installation and select *NOT* to format it, will the installer still write/update any necessary files to it?

---

### Post by SeijiSensei on 2017-09-25
I don't believe so especially if you mark it not to be formatted.

But why would you take this approach if you're worried?  Leave it out of the installation and add it in later with an entry in /etc/fstab.

---

### Post by oldfred on 2017-09-25
I have had installer ask it I wanted to keep an edited config file or use developers default config file. And there is no correct answer as edited file may not work with new install or developers file may include all the changed manually made to make it work, or may overwrite needed settings.
 
Again backups and accept defaults is what has worked for me as then I can restore or compare new settings with my old settings.

---

### Post by r_widell on 2017-09-26
Almost certainly.
Follow the suggestion above about selecting the "Something else" ("Manual" in Kubuntu) option at the disk partitioning stage.
To do a clean install, ensure that / (root), /boot and any other system mount points (/lib, /srv, /var, etc.)  will be formatted.
Ensure that the /home mountpoint doesn't get formatted.

The installer will put any necessary user startup files in the /home/USERNAME directory.

Note that there may be some cruft left over if any of the user startup files have different filenames under the new system.

I've never seen this cruft cause problems, since the old files never get used, but that doesn't mean that yours won't be the first.

Enjoy your new system.
ron

---

### Post by efflandt on 2017-09-27
I don't have a separate /home partition. But when I was going to do a fresh install of 14.04, I totally copied my 12.04 /home to an external drive, installed 14.04, then copied everything for /home back from the external drive. Everything worked.

When I installed 16.10 (due to issues I had with 16.04) to a different drive (mSATA from failed laptop in SATA adapter) I did not copy my entire /home over to that, I just copied over things related to firefox (so I would have bookmarks) and Steam game files which I had to relocate to the newer path after installing Steam, putting what was in ~/.local/share/Steam/SteamApps/ into ~/.steam/steam/steamapps/ (since original path from 12.04 that still also worked in 14.04 did not work in 16.10).

On a related note, on a tablet PC I split a 32 GB SD card into 3 partitions, one Ubuntu, one Lubuntu, both using a common /home partition (with grub only installed on one OS). That all worked fine.

Since 16.10 has reached end of support I need to figure out whether to back up to 16.04 LTS or upgrade to short term version 17.04.

---

