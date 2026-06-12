---
title: "Cannot download 10.04 image into LiveCD filesystem"
date: 2010-09-30
forum: Installation &amp; Upgrades
---

### Post by Rogue_417 on 2010-09-30
Recently I've been struggling with an upgrade to Karmic Koala (see my Cannot Boot from Hard Disk) from Jaunty Jackalope.  Despite a valiant effort to find and install grub2 I've decided instead to download and install Lucid Linx.  However when I visit the download site on ubuntu.com it gives no options as to where I might save it.  Since I'm currently running Karmic from a LiveCD the filesystem doesn't have enough room for the 700mg .iso, although I have plenty of room on the 40 gig HDD.  How do I point the download towards my hdd rather than the LiveCD filesystem?

---

### Post by drs305 on 2010-09-30
Is the 40GB drive mounted already? If it is and you are using the LiveCD's Firefox:
Edit > Preferences. General tab.
Downloads. Save files to ... Browse.
Located your mounted 40GB partition and choose a folder on that partition.

If the partition isn't mounted and you need instructions on how to do so, just ask.

After you have set the default download location in Firefox, when you start the download the package will be saved to the location you selected in the "Save to" window.

---

### Post by Rogue_417 on 2010-10-01
Thank you!  Worked like a charm!

---

