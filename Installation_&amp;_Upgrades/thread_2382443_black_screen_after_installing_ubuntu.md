---
title: "black screen after installing ubuntu"
date: 2018-01-13
forum: Installation &amp; Upgrades
---

### Post by mandeep62 on 2018-01-13
Hi all,

There is a issue which I'm facing after installing ubuntu alongside with windows 10. The ubuntu works just fine unless I boot windows.

If I boot windows, and again try to boot ubuntu then, It lands me up to a black screen " initfsrams" something like that. To fix this, I use fsck to repair the file system of linux. This is just a temporary fix.


Everytime I boot windows and then try to boot ubuntu, I encounter same issue? anyone know the fix?

---

### Post by mörgæs on 2018-01-13
Hi, welcome to the fora.

It's easier to help if you provide a complete hardware description. Please copy and paste ```
sudo lshw -sanitize > lshw.txt
``` into the terminal, run it and post lshw.txt in CODE tags.

---

