---
title: "Can I clone a system as an image file, not installed package export?"
date: 2007-02-01
forum: Installation &amp; Upgrades
---

### Post by caffienda on 2007-02-01
I would like to create an image of an install that retains all the programs, updates and upgrades that are installed.  I guess this would be similar to Norton ghost, but in Linux if this is possible.  

Here is why.  I do the same install a few times a day on virtual servers and each install takes about an hour to download the updates, programs and upgrades.  

Is it possible to clone over FTP or from 1 drive to another?  
Does anyone know how to do this in VMWare?

---

### Post by RAOF on 2007-02-01
Well, you could use **dd**.

Something like ```
sudo dd if=/dev/*<partition to image>* of=*/path/to/image/file*
```

The *of* can go anywhere you've got mounted.

Then, to write that image out, you'd just swap *if* with *of*.

That will take a bit-perfect image of your partition.  If the partition you want to write it to is bigger, then you'll probably need to resize the filesystem after you write the image to it.  If the partition you want to write it to is *smaller*, I don't think it'll work.

---

