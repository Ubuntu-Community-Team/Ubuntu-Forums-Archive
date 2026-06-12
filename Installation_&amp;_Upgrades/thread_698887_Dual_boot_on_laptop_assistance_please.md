---
title: "Dual boot on laptop assistance please"
date: 2008-02-16
forum: Installation &amp; Upgrades
---

### Post by Thinminnow on 2008-02-16
Hello All,
I'm a newbie and am hoping to get some help with setting up a dual boot system on a laptop. I've read all the material but am still unclear as to to correct way to set this up. I have found it a little confusing. I have an Asus A6J laptop which has a hundred gig drive. So far I've only created a 25 gig ntfs partition and have installed windows xp on it. I have 75 gigs of unpartitioned space. It would be great if I could share file between linux and xp. Any help would be very greatly appreciated. I've tried this before and created a bit of a mess.

Very Sincerely,

Rich

---

### Post by pmgr33r on 2008-02-16
make about a 6gb ext3 partition for root (mounted under /) and then the remainder as FAT 32 or NTFS and mount under /home or whever you want it. (All the mounting stuff will be asked during live install) I know windows should be able to read both NTFS and FAT32, at least on an external it will.

---

### Post by Thinminnow on 2008-02-16
Wow! thanks very much for the speedy reply. I didn't think linux could deal with ntfs? Should the partioning be done with xp or in the linux world? Perhaps you mean linux. Don't know of the ext3 partition  type under windows. Do I need a swap partition with linux?

Thanks,

Rich

---

### Post by kbless7 on 2008-02-16
> **Thinminnow said:**
> Wow! thanks very much for the speedy reply. I didn't think linux could deal with ntfs? Should the partioning be done with xp or in the linux world? Perhaps you mean linux. Don't know of the ext3 partition  type under windows. Do I need a swap partition with linux?

Thanks,

Rich

The ext3 is for the ubuntu to install on, and a linux swap should be automatically created upon install.  As for the ntfs format, i'm not sure if linux will deal with it, but i'm sure there is some software that can be installed to have ubuntu read/write to it.

---

