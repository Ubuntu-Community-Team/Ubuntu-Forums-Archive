---
title: "rm: cannot remove `/usr/lib/gcc/i686-linux-gnu/4.5': Permission denied"
date: 2012-06-11
forum: Installation &amp; Upgrades
---

### Post by bhaskar123 on 2012-06-11
hai guys,
         iam login as a root
but whenever am try to remove  following directory ,

rm -rf /usr/lib/gcc/i686-linux-gnu/4.5

it will shows permission denied as fallows.......solution please


rm: cannot remove `/usr/lib/gcc/i686-linux-gnu/4.5': Permission denied:mad:

---

### Post by raja.genupula on 2012-06-11
hi could you give me the terminal code exactly , how you have login as root ?

---

### Post by codemaniac on 2012-06-11
> **bhaskar123 said:**
> hai guys,
         iam login as a root
but whenever am try to remove  following directory ,

rm -rf /usr/lib/gcc/i686-linux-gnu/4.5

it will shows permission denied as fallows.......solution please


rm: cannot remove `/usr/lib/gcc/i686-linux-gnu/4.5': Permission denied:mad:

First of all root has all the necessary permissions to delete or manipulate any system objects across filesystem .

As asked by Raja please provide the details how you logged in as root .

However I surprise why you want to remove the above directory where essentials files required for gcc to operate, resides .If you want to uninstall gcc you can use package managers .

---

