---
title: "Ubuntu 13.04 upgrade"
date: 2015-05-14
forum: Installation &amp; Upgrades
---

### Post by Matt_Reed on 2015-05-14
Okay, I'm running Ubuntu 13.04 on a dual-boot system with Win7. (Yes, I know it's a little out of date. I was sans-Internet for over a year.) I keep running into issues with my browser (Firefox) that it's out of date and I need a new version (as well as my Java won't update either to the newest version), but when I try to run the system updates, I get a message that everything is on the up-and-up. Now I see that Ubuntu is up to version 14.02. Is there a way I can upgrade my OS kernel through the existing GUI without having to reinstall a new OS kernel version from a DVD or USB? At this point, it's kind of unstable, so I need to be able to get the new patches and whatnot.

Thank you. (I attempted to search for 13.04 in the search bar, but I couldn't find any results in the hundreds of threads that exist. Dunno why.)

---

### Post by sammiev on 2015-05-14
Hi Matt_Reed,

You really need to update to 14.04LTS, 13.04 is not supported any more and depending on your ppa's and soure.list, you maybe better off to backup all your data and do a fresh install of a LTS ( Long Term Version ).

---

### Post by Matt_Reed on 2015-05-16
I'd love to update to 14.04 and that's the gist of my question. I don't have an external drive to which I can back up. Can I update from 13.04 to 14.04 and not completely wipe all my data? Will using my Win7 partition be an acceptable method of backing up my data?

---

### Post by Frogs Hair on 2015-05-16
If you have a cloud account like Drop-Box, Google Drive or numerous others you can move data there temporarily during the installation depending on the amount of space you can get for no cost . I use Drop-Box with my win 7 dual boots, by compressing the folders and uploading them. This works best for me since I install the latest release every six months. Creating a separate home partition is another option and  community documentation is available.

---

### Post by ian-weisser on 2015-05-17
> **Matt_Reed said:**
> Can I update from 13.04 to 14.04 and not completely wipe all my data?

Generally, yes. The Ubuntu installer will detect an existing filesystem, and won't overwrite the /home directory.
Simply don't repartition, and read the installer questions carefully.

The installer developers worked quite hard to develop that feature. That doesn't mean it works 100% of the time...though it has worked perfectly for me many times. Nevertheless, my data is backed up before I run the installer. Installs and upgrades always entail some risk.

You can certainly preserve data in your Windows partition, though file permissions and similar metadata may be lost.
Frogs Hair's idea to use Dropbox/GDrive is better - a backup on the same drive is not preferred. Drives die.

---

