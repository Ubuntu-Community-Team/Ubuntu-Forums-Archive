---
title: "Botched upgrade to 2.6.31-20 kernel. Any ideas on a cause/fix?"
date: 2010-03-05
forum: Installation &amp; Upgrades
---

### Post by immerohnegott on 2010-03-05
Ran a standard dist-upgrade a couple days ago, and apt attempted to install a new kernel (2.6.31-20-generic). The installation failed at dpkg/configure:

```
dpkg: error processing linux-image-2.6.31-20-generic (--configure):
 subprocess installed post-installation script returned error exit status 1
```  

apparently when attempting to run the GRUB2 config script.

Said script spits an error like "no path or device specified", followed by the whole update process dying without dignity - basically spitting out a bunch of dependency errors because the linux-image .deb couldn't be configured completely.

So, thoughts? I've attempted to purge/reinstall the packages to no avail. Ran dpkg --configure -a. Nothing. As these are kernel/bootloader packs, I'm pretty hesitant to start just going to town on the files until something works (or, with my luck, causes my machine to implode).

For what it's worth, I can still boot just fine into 2.6.31-19 to fix this mess.

---

### Post by Barriehie on 2010-03-05
> **immerohnegott said:**
> Ran a standard dist-upgrade a couple days ago, and apt attempted to install a new kernel (2.6.31-20-generic). The installation failed at dpkg/configure:

```
dpkg: error processing linux-image-2.6.31-20-generic (--configure):
 subprocess installed post-installation script returned error exit status 1
```  

apparently when attempting to run the GRUB2 config script.

Said script spits an error like "no path or device specified", followed by the whole update process dying without dignity - basically spitting out a bunch of dependency errors because the linux-image .deb couldn't be configured completely.

So, thoughts? I've attempted to purge/reinstall the packages to no avail. Ran dpkg --configure -a. Nothing. As these are kernel/bootloader packs, I'm pretty hesitant to start just going to town on the files until something works (or, with my luck, causes my machine to implode).

For what it's worth, I can still boot just fine into 2.6.31-19 to fix this mess.

You can manually remove the botched kernel by rm'ing the linux-image-2.6.31-20-generic files in **/var/lib/dpkg/info/** and you'll have to edit your grub menu file.  I'm not familiar with grub2 so I can't help you there.  After rm'ing, or renaming, the kernel files then run apt-get update to resynchronize everything.  Have to run as root.

HTH,
Barrie

---

### Post by immerohnegott on 2010-03-08
I wasn't aware of that folder in /var/. Deleted, ran apt-get update, and the kernel errors were fixed. There was still an error in GRUB, though, as update-grub was still giving me crap. Out of whimsy, I decided to change GRUB's background image - evidently changing a config file around fixed it right up, as update-grub ran flawlessly after that.

---

### Post by Barriehie on 2010-03-08
> **immerohnegott said:**
> I wasn't aware of that folder in /var/. Deleted, ran apt-get update, and the kernel errors were fixed. There was still an error in GRUB, though, as update-grub was still giving me crap. Out of whimsy, I decided to change GRUB's background image - evidently changing a config file around fixed it right up, as update-grub ran flawlessly after that.

Good deal then! So this thread is solved?

---

