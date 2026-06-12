---
title: "Second HDD appears as folder in home directory( comments please)"
date: 2014-04-28
forum: Installation &amp; Upgrades
---

### Post by uwe-bungto on 2014-04-28
I hope this will not cause grief in the future.
I decided to install Ubuntu Studio along with Darktable and Lightworks for audio visual work. I wanted the AV progects on a second internal drive; but easily accessible from my home directory.
Instead of a path like /media/av I thought maybe ./av would be simpler.

I tried mount from fstab with out luck mount point not found.
UUID=3eeb2980-222b-48df-9026-03f89dd9e787   /av         ext4    defaults 0    2

I created a folder in / called av and chmod 2777
then ln -s /av /home/<user name>/av

Now I have the access I wanted.

Can anyone see if I have created a trap for myself or is this a workable solution?

Paul

---

### Post by oldfred on 2014-04-28
I use links, and now mount in /mnt.

But lots of arguments over where you should mount things. I think I started with / like you have and someone commented you should use /mnt or /media. Often more an issue in a server where multiple admins may configure it and need standard locations. Since you are only admin, it really does not matter.

Auto mounts are in /media. And other mounts may be in /mnt.
The standards base is not totally clear.
 [http://en.wikipedia.org/wiki/Linux_Standard_Base](http://en.wikipedia.org/wiki/Linux_Standard_Base)
[http://en.wikipedia.org/wiki/Unix_directory_structure](http://en.wikipedia.org/wiki/Unix_directory_structure)
Linux Standard Base details
[http://refspecs.linux-foundation.org/LSB_3.2.0/LSB-Core-generic/LSB-Core-generic/book1.html](http://refspecs.linux-foundation.org/LSB_3.2.0/LSB-Core-generic/LSB-Core-generic/book1.html)

---

