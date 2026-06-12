---
title: "Grow Boot Sector. Delete Swap Partition. Can't boot afterwards."
date: 2010-03-07
forum: Installation &amp; Upgrades
---

### Post by kendoori on 2010-03-07
I'm running 9.10 off of a 4 GiB CF card. I keep running into space issues with updates, so I purchased an 8 GiB replacement card. I've cloned the 4 GiB card to a .IMG file using DD. I've then copied the 4 GiB image back to the 8 GiB card using the Ubuntu startup disk creator program. Once done, I'm able to properly boot off of the new 8 GiB clone.

Unfortunately, the clone ends up with 3.67 GiB of unallocated space at the end *see attached). I tried deleting the "extended" partition that the swap is located at after booting from a Live CD and the system was unable to boot after this. I was thinking that I would delete the swap entirely and create a swap file after I merged the existing partitions, but I was unable to do this.

Can anyone advise the best way to do this (e.g. get one large 8 GiB partition with my old image on it)? I still have the original untouched 4 GiB card and also have an external CF drive if I need to redo the cloning. I've also used Clonezilla before, so perhaps there's a way to do this that allow me to grow the image as it's being cloned.

---

### Post by kendoori on 2010-03-07
Figured out that the boot sequence of the machine had somehow put the CF card in second place, so machine wasn't booting because it was pointing to an unbootable SATA hard drive used for just data.

---

