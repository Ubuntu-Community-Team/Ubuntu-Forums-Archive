---
title: "Why upgrade kernel?"
date: 2017-01-04
forum: MINT
---

### Post by Dirk_Ouellette on 2017-01-04
After upgrading the last time on my Linux Mint 18, I had nothing but trouble with trying to keep my wifi going. Why would I now want to upgrade the kernel to 4.4.0-57.58?
 My machine , an Acer Aspire V5-531, now runs beautifully. I don't want to mess with what ain't broke!! :-)  :-)  :confused:  :confused:  :confused:
Thanks all...

---

### Post by howefield on 2017-01-04
Moved to the "*MINT*" forum.

---

### Post by ajgreeny on 2017-01-04
By default, if I remember correctly, Mint does not update kernels, nor xorg graphics package versions, unless there is a very good security reason for doing so.

If you have a difficult wifi adapter leave the kernels untouched by choosing update safety categories (or however it is they describe them) 1-3 only, avoid the 4 & 5 categories.

Inn the times that I have used Mint in the past, and always using ethernet, not wifi, I always enabled all updates without any problems but if I had been using wifi things may have been different for me.

---

### Post by jeremy31 on 2017-01-04
I have never had a wifi issue that was caused by a kernel update either in Linux Mint or Ubuntu.  What wifi card do you have?  Please post results from terminal for ```
lspci -nnk | grep -iA2 net; lsusb
```

---

