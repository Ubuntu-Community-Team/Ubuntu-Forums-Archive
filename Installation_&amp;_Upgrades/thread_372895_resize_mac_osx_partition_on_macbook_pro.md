---
title: "resize mac osx partition on macbook pro"
date: 2007-02-28
forum: Installation &amp; Upgrades
---

### Post by idn on 2007-02-28
hi, i have successfully installed ubuntu on a macbook pro, my partition table is below:


```

/dev/sda1 - efi boot
/dev/sda2 - mac osx (hfs+)
/dev/sda4 - ubuntu

```

I also have 2GB or unallocated space where the swap partition used to be, but i moved this to a swap file on my ubuntu partition. SO it used to lo like this

```

/dev/sda1 - efi boot
/dev/sda2 - mac osx (hfs+)
/dev/sda3 - swap
/dev/sda4 - ubuntu

```


So i now i have 2gb of space for another install - either another linux os or windows. This isnt really enough for windows or linux as i am likely to install lots of software etc once i start to use it.

EFI on the macbook pro can only support 4 partitions max, it does not support extended partitions either. So what I want to do is resize /dev/sda2 (the mac osx hfs+ partition) and then create merge the new space with the swap partiiton and bingo i have enough for a new OS. 

Trouble is I dont know how to do this, gparted doesnt seem to support resizing HFS+ so i dont really know what to do, is there a way to do this? Or maybe I have to go into Mac OSX and resize it there?

Cheers

---

### Post by idn on 2007-03-01
bump :) I have a feisty CD im itching to install on my machine lol, dont suppose anyone can help me with this?

---

