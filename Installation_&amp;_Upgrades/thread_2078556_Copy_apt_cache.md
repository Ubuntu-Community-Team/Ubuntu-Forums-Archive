---
title: "Copy apt cache?"
date: 2012-10-31
forum: Installation &amp; Upgrades
---

### Post by bailout on 2012-10-31
I installed kubuntu 12.10 recently and need to wipe it and reinstall. I updated the install, added codecs, installed some apps etc and would want to do the same to the new install. To save downloading the packages again can I copy the apt cache to another partition and then copy it back to the new install so it doesn't have to download the same packages again?

If so should I copy /var/cache/apt/archives only or /var/cache/apt/ which includes 2 bin files as well.

I know there are some apps that will do this but as this is just a one off I would rather do it manually if possible.

thanks

---

### Post by Lars Noodén on 2012-10-31
You should be able to copy /var/cache/apt/ with tar.  However, one problem is that there can be multiple versions of the same package in the archive.  When an updated version is downloaded, the older ones are still kept around in the archive.  So I'm not sure of the best way to restore.

---

### Post by bailout on 2012-10-31
I was hoping that if I coppied the cache to the new install then when I installed updates it would 'see' the files in the copied cache and use those rather than downloading them again. I don't know whether it would pick up the files though or makes a list of them when downloading.

---

### Post by Linuxisfast on 2012-10-31
Use Apt-on-cd in software center to get this job done.

---

### Post by bailout on 2012-11-01
I decided to try it and just copied var/cache/apt/archive to my data disk and copied it back to the new install. When I ran the upgrades and installs apt used the copied files and didn't download them again.

---

