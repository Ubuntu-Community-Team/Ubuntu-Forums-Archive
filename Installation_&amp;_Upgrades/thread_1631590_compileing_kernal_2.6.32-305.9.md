---
title: "compileing kernal 2.6.32-305.9"
date: 2010-11-26
forum: Installation &amp; Upgrades
---

### Post by leeper69 on 2010-11-26
Hi I am trying to compile the kernel on my computer running Ubuntu 10.10 to enable high memory. 
I started out at the Ubuntu help page at [http://help.ubuntu.com/community/kernel/compile@get](http://help.ubuntu.com/community/kernel/compile@get) the kernel source and followed the directions until they split up for the different versions then I was redirected to [http://blog.avirtualhome.com/2010/11/06/ how-to-compile-a-ubuntu-maverick-kernel/](http://blog.avirtualhome.com/2010/11/06/ how-to-compile-a-ubuntu-maverick-kernel/) from here I followed the directions and downloaded kernel 2.6.35-23.40 into the directory /hmq4/kernel/source everything went fine until I tried the git checkout ubuntu-2.6.35-23.40 -b core2 command which generated the following error message git checkout: updating path is incompatible with switching branches. did you intend to checkout 'ubuntu-2.6.35-23.40' which can not be resolved as commit? what did I do wrong?

---

### Post by leeper69 on 2010-12-15
this is how I made my branch.
from the directory you have downloaded your source into using the root terminal type in ( git checkout -b {your new branch name} master ) 
leave off the quotation marks and fill in your chosen branch name. 
then to check if the branch is made type ( git branch ) you should see the newly created branch in the generated list.
note: an astrics ( * ) next to the branch list means that that is the active branch.
to make your new branch active type
 ( git checkout -b {your branch name} master ) without the quotation marks and fill in your branch name. 

I hope this will help someone struggling to compile a new kernel.

---

