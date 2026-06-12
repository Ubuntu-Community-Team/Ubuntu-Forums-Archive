---
title: "Hanging on Ubuntu installing screen"
date: 2015-11-20
forum: Installation &amp; Upgrades
---

### Post by Julian_HIndelang on 2015-11-20
Hey, I have the problem, that the Ubuntu Installation allways hung up if I try to install Ubuntu. I tryed different installations, 14 LTS and the new one 15. And the charachters in the installation windows doesn't get showed right.
The installation allways hung up at the point where the installation tells me, that it is writing the root partion to the disk. The PC isn't hanging, the installations just won't move the loading bar, at this Point I can wait 30 minutes without any changes.

I actually tryed to install ubuntu from CD and afterward from USB-stick.

What can that be?

If you need more information let me know it.

I uploaded pictures which shows the issue:
[[IMG]http://www2.pic-upload.de/thumb/28904856/1.jpg[/IMG]](http://www.pic-upload.de/view-28904856/1.jpg.html)
(notice the missing characters)
[http://www.pic-upload.de/view-28904785/2.jpg.html](http://www.pic-upload.de/view-28904785/2.jpg.html)
[http://www.pic-upload.de/view-28904783/3.jpg.html](http://www.pic-upload.de/view-28904783/3.jpg.html)
[http://www.pic-upload.de/view-28904786/4.jpg.html](http://www.pic-upload.de/view-28904786/4.jpg.html)
[http://www.pic-upload.de/view-28904794/5.jpg.html](http://www.pic-upload.de/view-28904794/5.jpg.html)
[http://www.pic-upload.de/view-28904799/6.jpg.html](http://www.pic-upload.de/view-28904799/6.jpg.html)
[http://www.pic-upload.de/view-28904795/7.jpg.html](http://www.pic-upload.de/view-28904795/7.jpg.html)
[http://www.pic-upload.de/view-28904817/8.jpg.html](http://www.pic-upload.de/view-28904817/8.jpg.html)
[http://www.pic-upload.de/view-28904816/10.jpg.html](http://www.pic-upload.de/view-28904816/10.jpg.html)
At the last picture, the installation hangs.

Any idea, what wents wrong?

---

### Post by Julian_HIndelang on 2015-11-21
Now I tryed to install Mageia. With that I'm getting a more precise error message (instead of none). Obviously the setup have problems with formatting my HDD on which I want to install Linux (a can't delete /dev/sdc1 error). But if I delete the HDD with Windows data carrier administrator (what works without any problems) and try afterward to install Mageia, I'm getting the message, when the installation try to copy the installation neccessary datas to the HDD, that media.cfg can't be found.
(if I format the HDD under Windows as NTFS, I'm able to use my HDD without any problems)
Any ideas?

---

### Post by Julian_HIndelang on 2015-11-21
I solved the problem: I ereased the GTD Table from my HDD, and the installation worked.

---

