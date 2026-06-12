---
title: "Firefox without Flash?"
date: 2010-04-10
forum: Installation &amp; Upgrades
---

### Post by BerlinNurse on 2010-04-10
I have installed netbook remixe. While using Facebook with Firefox it tell me that no Flash is installed.

What is behind it?

---

### Post by yabbadabbadont on 2010-04-10
Flash is not installed by default in Ubuntu.  (at least not any of the official versions)  Install it.

---

### Post by steveneddy on 2010-04-11
Maybe the answer is to - in terminal

```
sudo apt-get install flashplugin-nonfree
```

Hope that helps.

---

### Post by steveneddy on 2010-04-13
I noticed this is marked solved now.

What solved the issue you were having?

We are a curious bunch in UF and always like for the final answer to be posted so someone else searching the forums can get benefit from the answer.

---

### Post by mockingbird on 2010-04-13
Note:  Those with 64-bit version should download the Alpha 64-bit flash from [http://labs.adobe.com](http://labs.adobe.com) and extract the "libflashplayer.so" file to "/usr/lib/mozilla/plugins/".

If you install the flashplayer-nonfree to the 64-bit version, it is going to install a wrapper so that the 32-bit version can work in Firefox.

---

### Post by BerlinNurse on 2010-04-14
Because it is not in the repository I downloaded the deb from adobe directly.

---

### Post by steveneddy on 2010-04-14
> **BerlinNurse said:**
> Because it is not in the repository I downloaded the deb from adobe directly.

You should probably update your Sources List in 

System --> Administration --> Software Sources

and check off the boxes for 

Universe - Multiverse and Restricted

then update when it asks you to.

This will give you a complete repo system to choose from.

---

