---
title: "Not sure how to install pre-downloaded copy of Thunderbird"
date: 2008-09-15
forum: Installation &amp; Upgrades
---

### Post by jeremytas on 2008-09-15
I have just downloaded a copy of Thunderbird 2.0.0.16 from the Mozilla website. After having done this, I realised I could have installed it using the "Add/Remove" option on the Applications menu or alternatively by typing "sudo apt-get install thunderbird" in a command shell. *Never mind, but...*

If I use either of these two automated methods, it will almost certainly download Thunderbird all over again. Is there a way I can just install the copy I have already downloaded? I can't see any sort of Setup or Install file.

Any help would be greatly appreciated, but if it's too complicated I might just use the "Add/Remove" option after all, which although straightforward, would be a waste of the file I have already downloaded.

---

### Post by jeremytas on 2008-09-15
Didn't get any suggestions from anyone with this, so never mind. I ended up deleting the copy that I had previously downloaded from the Mozilla website and just used the Add/Remove option (which downloaded it again).

---

### Post by babloo75 on 2009-01-30
any suggestions for the above query?????????????
please help..

---

### Post by Bios Element on 2009-01-30
...Just run this in console.
```
sudo apt-get install thunderbird
```

---

### Post by babloo75 on 2009-01-30
> **Bios Element said:**
> ...Just run this in console.
```
sudo apt-get install thunderbird
```

But will this command install the latest version?

---

### Post by cariboo on 2009-01-30
No it won't.  THe command will install the latest version that is in the repository. If you need the latest you have to down load it from Mozilla and install it manually. When you download a  compressed file, double-click and file-roller will extract it for you. Once the package is extracted, there isually a readme file that tells you how to install it. I would suggest if you manually install programs, you set up a directory to store the sources, that way if you want to uninstall it you just have to go into the source directory and follow the instruction in the readme or install file.

Jim

---

