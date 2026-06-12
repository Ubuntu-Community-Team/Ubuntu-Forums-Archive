---
title: "False duplicate sources.list entry warning"
date: 2010-02-18
forum: Installation &amp; Upgrades
---

### Post by Nick Payne on 2010-02-18
If in Software Sources I have "Download from" set to "Server for Australia", then when I run sudo apt-get update, I get a warning at the end

```
Reading package lists... Done
W: Duplicate sources.list entry http://dl.google.com stable/main Packages (/var/lib/apt/lists/dl.google.com_linux_deb_dists_stable_main_binary-i386_Packages)
W: You may want to run apt-get update to correct these problems
```

There is definitely only one entry for Google in sources.list, and if I change Download from to be another Australian mirror, with no change in sources.list, then I don't get the warning messages when running apt-get update. What causes an apparently false warning to be issued?

---

### Post by ajgreeny on 2010-02-18
Have a look to see if there is a **/etc/apt/sources.list.d** folder which may contain the duplicate entry.  Third party entries often go into this folder, eg, medibuntu.list, and are read as if in sources.list.

---

### Post by Nick Payne on 2010-02-18
Thanks, I checked /etc/apt/sources.list.d and it contains the file google-chrome.list which contains the duplicate line. But why should it make a difference which mirror server I point to as to whether I get the duplicate sources.list warning or not, as dl.google.com is a 3rd party source separate from the mirror.

If I no longer have the error with the current mirror, should I leave the dl.google.com line in both sources.list and google-chrome.list? The current mirror is better for me anyway than the default Australian mirror, as it is my local ISP and therefore unmetered for downloads.

---

### Post by ajgreeny on 2010-02-18
I don't think it will matter where the line for **google.etc etc** is as long as it is there somewhere.  I would get rid of one or other by just commenting it out and trying the apt-get update command, just to make sure than the google repo is still enabled.  There's no point having it twice as it may cause problems later in some way.

---

