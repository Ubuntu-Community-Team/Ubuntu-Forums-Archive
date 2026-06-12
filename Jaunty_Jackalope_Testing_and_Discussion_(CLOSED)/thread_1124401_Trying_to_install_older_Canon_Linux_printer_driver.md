---
title: "Trying to install older Canon Linux printer driver; need advice please!"
date: 2009-04-13
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by GARoss on 2009-04-13
I've read that the Canon PIXUS 950i is the same as US version, i950 Canon. So, I when to this site;

[ftp://download.canon.jp/pub/driver/bj/linux/](ftp://download.canon.jp/pub/driver/bj/linux/)

after reading this forum post;

[http://ubuntuforums.org/showthread.php?t=10540&highlight=i950+driver&page=8](http://ubuntuforums.org/showthread.php?t=10540&highlight=i950+driver&page=8)

...downloaded & converted using alien to deb files as instructed & nothing prints when using the PIXUS 950i driver from the drop-down list. I'm not seeing any Canon software anywhere either. 
But, the above thread was started in 2005 & Ubuntu has changed a great deal since then so I may be missing something. I know the support libtiff & libpng have been updated in that time & Canon hasn't updated anything, of coarse.
If anyone out there has any ideas I'd appreciate them.
Thanks

---

### Post by castrojo on 2009-04-13
When you plug it in the printer thing has an option to get the driver from the internet, did that not work?

---

### Post by GARoss on 2009-04-13
> **whiprush said:**
> When you plug it in the printer thing has an option to get the driver from the internet, did that not work?

Yes. Found none. The attached thread in my 1st post explains the trial & tribulations of older Canon printers finding working Linux drivers. The driver I downloaded **is** for my printer, just the Japan version that Canon never released in the US market.

What I need is help getting this to work in Jaunty like those did a few years back in older Ubuntu versions!
Thanks

---

### Post by GARoss on 2009-04-15
Finally! Found a thread by Tom.Servo,

[http://ubuntuforums.org/showthread.php?t=972352&highlight=libtiff3](http://ubuntuforums.org/showthread.php?t=972352&highlight=libtiff3)

...where Tom had success by pointing a missing libtiff3 to libtiff4; 

cd /usr/lib/
sudo ln -s ./libtiff.so.4.2.1 ./libtiff.so.3

This did not completely fix the issue, however, as another one - libpng2 pointer was needed as well. This was solved by adding,

cd /usr/lib/
sudo ln -s ./libpng.so.3 ./libpng.so.2

So, Canon i950 now works with Canon's Linux version PIXUS 950i driver! 
Now, does anyone know how to get the software to work?:guitar:

---

