---
title: "upgrading Gutsy to Hardy"
date: 2008-04-25
forum: Installation &amp; Upgrades
---

### Post by whizkid25 on 2008-04-25
Hello all. I am considering for the upgrade. However, there are a few things I would like to clarify. When I installed Gutsy, I made 3 partitions 1 for SWAP, 1 for ROOT, 1 for HOME. Instead of upgrading directly, I was thinking that it would be better to wipe out ROOT, leaving HOME as it is and install Hardy. Could I do it this way or should I just backup HOME and wipe out both HOME and ROOT then install Hardy? Thanks in advance.

---

### Post by ajmorris on 2008-04-25
yep, you can just leave the home partition there, and wipe root, and install it into the newly formatted root partition. Also, are you aware you can just change your sources to hardy in /etc/apt/sources.list, then do sudo apt-get dist-upgrade. This way you upgrade to hardy, without having to re-format any drives.

AJ

---

### Post by whizkid25 on 2008-04-26
Great. But just to make sure, would I encounter more problems if I upgrade this way in comparison to a full wipe of ROOT and HOME installation?

---

