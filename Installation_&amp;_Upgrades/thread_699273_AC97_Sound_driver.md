---
title: "AC97 Sound driver"
date: 2008-02-17
forum: Installation &amp; Upgrades
---

### Post by SilverFrost on 2008-02-17
Hi all.

I just downloaded the new AC97 sound-card driver from their site and it came in a "tar.bz2" file when it was down.
How do you install that kind of file and make it run on the system?

Thank you.

---

### Post by eggdeng on 2008-02-17
Use the cd command to change to the directory you downloaded the file to. Run
```
bunzip2 name_of_file.tar.bz2
```
to unzip the file. Then
```
tar -xzvf name of unzipped file.tar
```
This will unpack the tar file. Now cd into the newly created directory. Run
```
ls
```
You will find specific instructions for installing in the readme or install files.

---

