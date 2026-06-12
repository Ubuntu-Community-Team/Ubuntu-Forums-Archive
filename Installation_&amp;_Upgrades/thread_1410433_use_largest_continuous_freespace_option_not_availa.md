---
title: "use largest continuous freespace option not available"
date: 2010-02-18
forum: Installation &amp; Upgrades
---

### Post by _nate on 2010-02-18
I have four partitions on my netbook. I resized them to make space for ubuntu netbook remix but when I try to install ubuntu the use largest available freespace option is not available so I am not sure how to proceed.  I am trying to install this on a asus eee 1005pe netbook and would like to keep windoze 7 installed as well.

---

### Post by darkod on 2010-02-18
You can't proceed because hdds have limitation of 4 partitions. That's why the option is not offered by the installer. If you delete one of the partitions, you will get the option.

Make some planning how to re-organize your hdd layout because with 4 partitions the ubuntu installer can't create another one.

---

### Post by oldfred on 2010-02-18
Win7 has probably used 2 primary partitions with its 100mb boot and its install. What are the other 2 partitions? If one is data, back it up and delete it. Then you can make an extended partition that can hold the data and the Ubuntu partitions as logical partitions inside the last primary/extended. If you cannot delete one of the existing you will not be able to install.

If one of the partitions already is an extended you will have to expand it to include the space you made available.

---

