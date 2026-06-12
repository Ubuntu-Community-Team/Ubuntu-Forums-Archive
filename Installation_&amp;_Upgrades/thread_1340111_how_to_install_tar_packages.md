---
title: "how to install tar packages"
date: 2009-11-28
forum: Installation &amp; Upgrades
---

### Post by deeptiaggarwal on 2009-11-28
i m trying to install tar packages in ubuntu 9.10. for that i just write 
sudo i
./configure
make
make install
but it is giving me error! and give me to use "apt- get install" .but i dnt have net connection. cant i install any tar packages without net?

---

### Post by SuperSonic4 on 2009-11-28
1. You should be able to. Moreover you shouldn't do all those commands as root

2. What program are you installing? It's often easier to say so it can be looked for

3. Run the following one at a time. (/path/to/dir) is where the decompressed tarball is

```
cd /path/to/dir
./configure
make
sudo make install
```

4. Usually there is a README or INSTALL file which often tells you what to do

---

### Post by wojox on 2009-11-28
tar -xvf NAME.tar.gz
cd NAME/
./configure
make
sudo make install

You need build essentials and linux headers from your live cd installed in order to compile it

---

### Post by GregBrannon on 2009-11-28
You should find this [link]("https://help.ubuntu.com/community/CompilingEasyHowTo") very helpful.  Browse the rest of the same guide to answer other questions about installing programs that you may have.  Perhaps you don't need to install from the command line at all but can use a package manager.

---

