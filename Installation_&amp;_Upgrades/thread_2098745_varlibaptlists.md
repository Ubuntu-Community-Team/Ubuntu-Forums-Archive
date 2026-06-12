---
title: "/var/lib/apt/lists/"
date: 2012-12-27
forum: Installation &amp; Upgrades
---

### Post by SergeScyld on 2012-12-27
About a month ago I tried to update some programs and i kept getting a message revolving around "/var/lib/apt/lists/skulltag.net_download_files_release_deb_dists_stable_multiverse_binary-i386_Packages". 

Now, I had skulltag installed at the time, but since then i have uninstalled and deleted every file related to it. However, in the /var/lib/apt/lists/ directory, this file still shows up and will not go away. 

It is keeping me from updating anything on my computer. Every time i try to update a program in terminal it gives me this error "Problem with MergeList /var/lib/apt/lists/skulltag.net_download_files_release_deb_dists_stable_multiverse_binary-i386_Packages"

Someone please help.

---

### Post by ibjsb4 on 2012-12-27
Try this

```
sudo rm /var/lib/apt/lists/* -vf && sudo apt-get update
```

[https://help.ubuntu.com/community/UsingTheTerminal#Starting_a_Terminal](https://help.ubuntu.com/community/UsingTheTerminal#Starting_a_Terminal)

---

