---
title: "How to skip partman stage (to install to custom FS) in Xubuntu 20.04 ?"
date: 2021-04-29
forum: Installation &amp; Upgrades
---

### Post by Nyyr on 2021-04-29
Hello,

I'd like to create and mount my own filesystem structure for Xubuntu 20.04 installation, i.e.
create partitions and filesystems, mount them under for example /target directory of the live CD
and then run Ubiquity, answer all those questions but when it is asking how to install it
(the one with Erase disk and install Xubuntu or Do something else) I want this part
to be skipped (partman not executed at all) and continue right away with the next step (installation of
packages into prepared mount point).
How would I do that?

I was looking into preseed files but it seems partman just reads those files and modifies disk(s)
according to it but is not skipped at all. I need filesystem not supported by partman so I want to skip it.

---

### Post by ActionParsnip on 2021-04-29
Use the something else option then select the existing partitions and their uses

---

