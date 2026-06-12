---
title: "Manually fixing package to unblock apt"
date: 2012-02-21
forum: Installation &amp; Upgrades
---

### Post by loldotdot on 2012-02-21
Hi,
I had installed a version of Maya (converted from .rpm to .deb) and wanted to uninstall it. I wasn't aware it would be listed in Software Centre where I could remove it, so like the non-Linux user I am, I started to um, just delete files.

I permanently deleted the usr/autodesk/ folder, and also some in opt/. Then I noticed the option to remove in Software Centre (it was still listed) and I removed it and it was fine. 

Trying to remove "dmmpluginformaya2012x64" won't work though (it was in a subdirector of usr/autodesk/; trying via Software Centre 
yields:

```

installArchives() failed: (Reading database ... 
(Reading database ... 5%
...
(Reading database ... 100%
(Reading database ... 278286 files and directories currently installed.)
Removing dmmpluginformaya2012x64 ...
rmdir: failed to remove `/usr/autodesk/maya2012-x64/bin/plug-ins/dmm': No such file or directory
dpkg: error processing dmmpluginformaya2012x64 (--remove):
 subprocess installed post-removal script returned error exit status 1
Errors were encountered while processing:
 dmmpluginformaya2012x64
Error in function: 
SystemError: E:Sub-process /usr/bin/dpkg returned an error code (1)

```

and using:
```
$ sudo apt-get remove -f dmmpluginformaya2012x64 
$ dpkg --purge dmmpluginformaya2012x64 
```

each give a more detailed:
```

(Reading database ... 278286 files and directories currently installed.)
Removing dmmpluginformaya2012x64 ...
rmdir: failed to remove `/usr/autodesk/maya2012-x64/bin/plug-ins/dmm': No such file or directory
dpkg: error processing dmmpluginformaya2012x64 (--purge):
 subprocess installed post-removal script returned error exit status 1
Errors were encountered while processing:
 dmmpluginformaya2012x64

```

Sadface. I won't delete files randomly again :) But this is blocking the uninstall of other programs (like Spotify) via the Software Centre (which I just tried to remove via dpkg, and worked) - is there a way to clean it, such that it won't think that the dmmplugin is installed?

Thanks :)

---

### Post by dino99 on 2012-02-21
try into a terminal:

sudo apt-get clean
sudo apt-get autoclean
sudo apt-get autoremove

sudo apt-get update
sudo apt-get install -f
sudo dpkg-reconfigure -phigh -a
(can take a while, be patient)

---

### Post by cortman on 2012-02-21
Try the commands given by dino99, and if that still doesn't do it, you may need to keep on um, deleting things. :)

As in search in the root directory for "dmmpluginformaya2012x64" and delete any matches. Then run

```
sudo rm -r /var/lib/apt/lists/*
sudo apt-get update
```

to reload your list of installed and available software.

---

### Post by loldotdot on 2012-02-24
Thanks for the suggestions guys, but neither of these worked.
Searching in / for "dmmpluginformaya2012x64" didn't turn up anything.

Worst case is I just wait til 12.04... with each release (and consequently with each 7 days I spend with ubuntu) I learn something which helps me not break it in the same way as last time :)
---

Wanting to delay starting my homework a bit longer, I carried on. For anyone with the same issue, you can download the dmmplugin in rpm format [here]("http://usa.autodesk.com/adsk/servlet/ps/dl/item?siteID=123112&id=16935849&linkID=9242259").
```
alien <downloadeddmmpackage.rpm>
dpkg --install downloadeddmmpackage.deb
apt-get remove <dmmplugin...>
```

(Last one definitely needs sudo, can't remember if alien and dpkg do too.)

Thanks all :)

---

