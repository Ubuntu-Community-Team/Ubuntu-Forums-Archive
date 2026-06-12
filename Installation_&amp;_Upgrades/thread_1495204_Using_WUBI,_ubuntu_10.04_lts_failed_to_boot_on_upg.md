---
title: "Using WUBI, ubuntu 10.04 lts failed to boot on upgrade from ubuntu 9"
date: 2010-05-27
forum: Installation &amp; Upgrades
---

### Post by prateekswapnil on 2010-05-27
Hi,
I am using WUBI to run ubuntu.I upgraded to 10.04 from ubuntu 9 using the update option provided.On restart after the update,i get to grub rescue prompt.Here when i type ls i get the output as hd0 and hd31.I cannot login into windows because the option to select between windows 7 and ubuntu is not available anymore.
It would be great if somebody could suggest a solution to this problem.

---

### Post by oldfred on 2010-05-27
So we can see where everything is at - from liveCD:

Boot Info Script courtesy of forum member meierfra
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Be sure to highlight and use code tags (# in edit panel) to make it easier to read when you post the results.txt.


If you installed grub to the MBR, you will have to reinstall a windows boot loader. Do you have the windows Cd or a Ubuntu liveCD. We can use either to get windows booting.

---

### Post by prateekswapnil on 2010-05-27
Hi,
I can't download the script since the gui is not running from the live cd,only the terminal comes up.I do have windows 7 dvd with me,how can I run from that..

---

### Post by oldfred on 2010-05-28
You have to run from a liveCD as it uses linux commands to look at your system.

perhaps you also have a video issue. Try f6 on the boot of the CD and often nomodeset works for initial video, also other special settings for boot systems that need them are available under f6.

---

