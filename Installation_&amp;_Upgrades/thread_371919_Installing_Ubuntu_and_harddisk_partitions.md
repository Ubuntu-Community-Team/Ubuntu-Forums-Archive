---
title: "Installing Ubuntu and harddisk partitions"
date: 2007-02-27
forum: Installation &amp; Upgrades
---

### Post by dery on 2007-02-27
Hy everybody. I`m new to this forum, new to Ubuntu, and new to Linux. :) 

Let me tell you why I`m here. I have downloaded Ubuntu 6.10, burn it onto a CD, run it, but I just can`t get over the install... Prior to this, I had partitioned my 80giga harddrive (on which I also have WinXP), and made two new physical partitions, a 12giga in "linux ext3" type, and a 1,6giga "linux swap". I have positioned them before C:, but as they are not NTFS, they did not affect the WinXP. Returning to the installation of Ubuntu. When I`m asked in the install window if I want to manually set which partitions Ubuntu to use, I clicked yes (if I would of not, than the install would overwrite my C: harddrive, hence my WinXP). And here comes the problem: I come across a window were I`m asked to set the mounting points or something like that, for the "/" (root), "/home" "/div" and two others as such, plus my swap. While for the swap I`ve set the swap partion, for the root ("/") I`ve set the "linux ext3" partion. I left the others unset, and I click the next button. An error image appears, which says something like root not set....", basically asking me to set partitions for the rest of that "/..." stuff. When I try to set for those, the same "linux ext3" partition, another error says that I can`t share the same partion. The only choice I have is to select (and hence formated) my NTFS partitions, on which I have Windows installed. What should I do? Partition my "linux ext3" into four smaller partitions, one for each of the "/..." stuff? Why is that? Can`t I just select to have Ubuntu installed on only one partition, and have it autamatically create a tree structure for each of the "/..." elements?

---

### Post by Irony on 2007-02-27
It would be simpler to delete the non-windows partitions (leaving them unallocated) and thus leave them as free space - then auto install to the freespace.

That way Ubuntu will create root and swap in the freespace without you having to do anything.

---

### Post by dery on 2007-02-28
> **Irony said:**
> It would be simpler to delete the non-windows partitions (leaving them unallocated) and thus leave them as free space - then auto install to the freespace.

That way Ubuntu will create root and swap in the freespace without you having to do anything.


But wouldn`t that mean that it will take space not only from unallocated space, but also from the free space from the other (NTFS) partitions? 

[Here]("http://ubuntuforums.org/showthread.php?t=372019"), to a simmilar question, the answer was the opposite :confused: . To roughly the same question, the answer was 

> You need to go back and complete creating new partitions out of what was hda1. Make a 38GB ext3 partition and the remainder ~1GB to swap. Then when you get back to the mount point screens you'll specify '/' for the 38Gb and /swap for the 1GB, and tick the 'reformat' boxes for those two but NOT the windows parititon on hda2 (or whatever it's designated after you do the above).

---

### Post by dery on 2007-02-28
Problem solved. Thanks Irony! I gave you solution a chance, plus I`ve read what exactly "to mount" means, made the connection with the "Reformat?" option, and managed to get Ubuntu installed :guitar:

---

