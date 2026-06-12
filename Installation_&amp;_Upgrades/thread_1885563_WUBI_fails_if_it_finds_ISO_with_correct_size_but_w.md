---
title: "WUBI fails if it finds ISO with correct size but wrong content"
date: 2011-11-23
forum: Installation &amp; Upgrades
---

### Post by emendelson on 2011-11-23
When I tried to run WUBI to install Ubuntu on a Windows XP system, it failed without any warning. I finally found the log file, and discovered that WUBI fails silently if it finds an ISO with the file size that it expects to find, but without the correct content. 

The only way to solve this was to run WUBI multiple times, and each time check the log file to find which ISO file it tried to load - and then rename the file to another extension (for example, .ISO--) so that WUBI would not try to load it. After renaming three such ISO files, WUBI eventually ran.

Perhaps WUBI could at least post an error message explaining why it did not run. That would be better than failing silently.

---

### Post by bcbc on 2011-11-23
You should file a bug: [http://bugs.launchpad.net/wubi/+filebug](http://bugs.launchpad.net/wubi/+filebug)

---

### Post by emendelson on 2011-11-23
Done:

[https://bugs.launchpad.net/wubi/+bug/894164](https://bugs.launchpad.net/wubi/+bug/894164)

Thank you for the easy-to-use link!

---

### Post by bcbc on 2011-11-23
Great! Don't forget to attach the wubi log file to the bug.

---

### Post by emendelson on 2011-11-23
Argh. I probably destroyed the log file. I can reproduce it easily, however, and will add a log file later.

---

### Post by bcbc on 2011-11-23
What you've added now looks good. It's enough for them to know how to reproduce the problem. Wubi is supposed to ignore incorrect ISO's and keep going, eventually download a new one if required. Even if it finds a valid Ubuntu ISO it checks inside for a /.disk/info file to confirm it's the correct release - so I suspect this is a new bug introduced in 11.10.

PS if you do have the log file (or recreate it) just add it as an attachment. Sometimes there are bits that don't seem important. I don't think that's an issue in this case, but in general it's better.

---

### Post by emendelson on 2011-11-23
Have now added a log file. Now that I look at it (as I explain in my bug-report post) I wonder if the problem has something to do with packed ISO files. But the maintainers will be able to figure it out from the log, I hope.

---

