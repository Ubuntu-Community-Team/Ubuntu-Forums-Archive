---
title: "after ubuntu loads its good for 30 seconds then freezes"
date: 2010-05-26
forum: Installation &amp; Upgrades
---

### Post by Ten31 on 2010-05-26
I am new at ubuntu and i have tried loading it 2 times once from a disk and once within windows.  after everything is done i turn on computer go to ubuntu I log in just fine and for about 30-45 seconds i can do whatever i want then it freezes and i have to force shutdown.  I have now deleted ubuntu and im going to redownload and install it. but if this happens again what should i do?

---

### Post by WinRiddance on 2010-05-26
It would help to know which version of Windows you're running since there appear to be some issues between Windows7 and Lucid? Also, you have to make sure that the partition that you're using for either Ubuntu 9.10 Karmic or Ubuntu 10.04 Lucid have been formatted with [COLOR=DarkRed]**ext4**[/COLOR] and **not** the ext3 file system. Also important is the type of Ubuntu or rather is it a 32bit or 64bit version that you're trying to install? You can only install 64bit versions if your processor supports 64bits.

Last but not least, if the newest Ubuntu 10.04 seems to have some issues with your pre-installled Windows, try to download the older Ubuntu 9.10 Karmic instead and install that one. It's only 6 months older. Karmic is awesome too, just doesn't look quite as snazzy and it's missing some fairly minor things that you probably wouldn't even be aware of. Give it a try ... and good luck.

---

### Post by Catharsis on 2010-05-27
What graphics card do you have?
```
lspci | grep VGA
```

---

### Post by kansasnoob on 2010-05-27
@ WinRiddance:

> Also, you have to make sure that the partition that you're using for either Ubuntu 9.10 Karmic or Ubuntu 10.04 Lucid have been formatted with ext4 and not the ext3 file system. 

That is not true. EXT4 is the default in 9.10 and 10.04 but you can still use EXT3 if you prefer.

> You can only install 64bit versions if your processor supports 64bits.

Also not true. I've used i386 on 64 bit systems a number of times due to flash problems, etc.

> there appear to be some issues between Windows7 and Lucid?

What issues?

---

### Post by kansasnoob on 2010-05-27
> **Catharsis said:**
> What graphics card do you have?
```
lspci | grep VGA
```

+1! There are some very specific "bug" issues with various graphics chips.

---

