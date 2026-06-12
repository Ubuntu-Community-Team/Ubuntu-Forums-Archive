---
title: "&quot;Replace Windows 8&quot; option erases entire disk"
date: 2014-05-19
forum: Installation &amp; Upgrades
---

### Post by wingedboars on 2014-05-19
I have HDD which until recently had two partitions: NTFS with legitimate Windows 8 and ext4 with Fedora 20. I decided to install Ubuntu instead of Windows, just to give Ubuntu a try. I took "replace windows 8" option (&#1084;y thoughts were: "What a service!") during installation, assuming that only windows 8 will be removed. Imagine my surprise when I discovered that Ubuntu "replaced" entire disk with itself.

[ATTACH=CONFIG]253290[/ATTACH]

Soooooo painful. So be careful.

Did I miss something or is it really a flaw?

---

### Post by oldfred on 2014-05-19
Same as this as it just uses entire drive.
Always best to use Something Else and manually format & choose partitions.

 Reinstall says overwrite Ubuntu but it also erases existing Windows.
[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1265192](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1265192)

---

### Post by wingedboars on 2014-05-19
[https://bugs.launchpad.net/ubuntu/+s...y/+bug/1265192]("https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1265192")
This is not exactly the same, but very similar. Ok, thanks, I added my two cents to this bug report. 
But this bug in at least six months old? Ahahaha. Well, I better move on then. Too friendly distr for me.:lolflag:

---

