---
title: "No Root File System error"
date: 2006-12-06
forum: Installation &amp; Upgrades
---

### Post by tamray on 2006-12-06
I am trying to do a new ubuntu install on a dell poweredge 2650, raid 5, dual  processor. (1.2TB and 3Ghz)

I have made four attempts and continue to get a pop up (No Root File System)

I am using the auto format selection.


Any ideas?

Raymond

---

### Post by drphilngood on 2006-12-06
You may find this useful.

A similar error is mentioned in the **Configuring the Bootloader** section of the [FakeRaidHowto]("https://help.ubuntu.com/community/FakeRaidHowto#head-ebcba6caa78bc698bd85e365603bc8cba784368f") in the Ubuntu Community Docs.


> ...
```

title           Ubuntu, kernel 2.6.15-29-amd64-k8
root            (hd0,4)
kernel          /vmlinuz-2.6.15-29-amd64-k8 root=/dev/mapper/via_hfciifae7 ro quiet 
initrd          /initrd.img-2.6.15-29-amd64-k8
```

IMPORTANT: Note that I removed "savedefault". If you leave this in, you will get a "file not found" error when you try to boot (you also can't set use default=saved up top as it shows in the menu.lst file's example). Again, if you are not using a separate boot partition, you can leave /boot in the paths. The "boot" command you would issue at the grub prompt is implied, so you can leave it out of the menu file. 

The guide details many other such errors, so you might want to read them all over.

I hope this helps.

---

### Post by ReaderRat on 2006-12-06
Other RAID documentation can be found [**HERE**](https://wiki.ubuntu.com/?action=fullsearch&context=180&value=RAID&titlesearch=Titles)

---

