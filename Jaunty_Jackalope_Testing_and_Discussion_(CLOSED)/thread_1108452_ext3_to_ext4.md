---
title: "ext3 to ext4"
date: 2009-03-27
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by fballem on 2009-03-27
I'm a relative newbie, running Jaunty Beta AMD 64 (happily, I might add). I am running under ext3 and would like to try ext4.

Is it easy to make the conversion (I have a backup of my data, so that's not an issue). If it is, could someone please provide me with specific instructions on how to do the conversion.

If the best option is to do a clean install, then that's fine. Where do I find the option to setup ext4?

Thanks,

---

### Post by BGFG on 2009-03-27
See my sig :)

[http://ubuntuforums.org/showthread.php?t=1107027&highlight=ext4](http://ubuntuforums.org/showthread.php?t=1107027&highlight=ext4)

---

### Post by fballem on 2009-03-27
When I run tune2fs -O extents,uninit_bg,dir_index /dev/sda1

I get the following error:

tune2fs 1.41.4 (27-Jan-2009)
tune2fs: Permission denied while trying to open /dev/sda1
Couldn't find valid filesystem superblock.

What am I doing wrong?

Thanks,

---

### Post by BGFG on 2009-03-27
nothing :) just put sudo in front of the commands and you'll be fine. hence
```

sudo tune2fs so on, so forth......

```

---

### Post by fballem on 2009-03-27
thanks - I'll give it a shot and let you know how I make out.

---

### Post by fballem on 2009-03-28
Ended up with an error in the second step (fsk -pf /dev/sda1). It wanted me to try without a parameter.

Rather than fuss over it, I ended up doing a clean install. At the point in the process where the installation was specifying the partitions, I chose custom, and was able to specify ext4 for my primary partition. (sorry, I don't recall the exact message)

Proves the value of a painfully learned lesson - always have a current backup of your important data.

Thanks,

---

