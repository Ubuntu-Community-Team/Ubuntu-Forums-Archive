---
title: "Putting &quot;/home&quot; on a separate partition (already installed)"
date: 2008-03-18
forum: Installation &amp; Upgrades
---

### Post by Ck.asdf on 2008-03-18
Hello, I have Ubuntu Studio 7.10 installed, and I've heard that it's a good idea to have a separate "/home" directory ... and actually, I was going to ask about that before installing, but I forgot, and now it's installed.
Can I still change it so that /home is on a separate partition (changing uStudio's location for home)?

I know how to manually create a separate partition, so my question is if it's possible, how do I tell Ubuntu Studio to look on the other partition (say, sda7)?

---

### Post by dmitriyp13 on 2008-03-18
copy the entire home directory to your new hard drive and use gparted to change the new drive's mount point to /home

---

### Post by Ck.asdf on 2008-03-18
wow, how simple! so ubuntu will see the partition with mount point of "/home," and decide to use it? 
what if I had another OS, like fedora, installed; would it also use that same partition?

---

### Post by Pumalite on 2008-03-18
Take a look at this guide:
[http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome)

---

### Post by dmitriyp13 on 2008-03-18
You will have to define the mount points in every OS as it does not carry over from one install to another, unless you use the same fstab file.  I have never tried that before, but as long as the different distros use the same syntax, I don't see a problem with it.

---

