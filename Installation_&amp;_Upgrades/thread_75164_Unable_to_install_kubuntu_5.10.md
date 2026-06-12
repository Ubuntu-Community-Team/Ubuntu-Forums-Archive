---
title: "Unable to install kubuntu 5.10"
date: 2005-10-13
forum: Installation &amp; Upgrades
---

### Post by ubunciak on 2005-10-13
1. kubuntu 5.10 iso dowloaded from torrent, burned on cd, no errors

2. new instalation on old ununtu 5.04 (formating old partition)

3. error: unable to install initrd-tools
check /target/var/log/bootstrap.log

4. error: instaling lilo or grub (/taget/...)

5. i must install once again 5.04 with grub and then go on windows to write this words :(

why 5.10 don't want install on my computer and 5.04 works perfectly?

best regards

---

### Post by claydoh on 2005-10-13
I suspect a bad iso image or bad burn.

First check the md5sum of the iso image and compare it to the md5sum given in the download directory where you got your torrent file. 

> md5sum <your-filename-goes-here.iso>
If you use k3b to burn the iso, it will display the info when you select the image file, at the bottom of the window that is just above the "options" section - you may need to scroll to see  it.

If those figures match up, then I would suggest burning a new disc at a slightly slower speed.

---

