---
title: "Disk Utility error/bug?"
date: 2009-09-01
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by bl33d on 2009-09-01
Whenever I start the machine I get this annoying little thing pop up.

[IMG]http://img215.imageshack.us/img215/3057/screenshotgdunotificati.png[/IMG]

But when I run the self test it passes, and tells me I have bad sectors >_<.

[IMG]http://img215.imageshack.us/img215/6214/screenshotpalimpsestdis.png[/IMG]

Everything works fine. Windows doesn't bitch at me like this does.

---

### Post by VMC on 2009-09-01
This topic has come up before. I think you will find LP reports on the issue. Search this forum for some discussions.

You might have a troubled hard drive so to be sure check it with other utilities.

---

### Post by bl33d on 2009-09-01
> **VMC said:**
> This topic has come up before. I think you will find LP reports on the issue. Search this forum for some discussions.

You might have a troubled hard drive so to be sure check it with other utilities.

Such as?

---

### Post by forumache on 2009-09-01
> **bl33d said:**
> Such as?

Such as hardware check utilities provided by your harddisk manufacturer.
Check their support site.

This is an example for Western Digital:   
[http://support.wdc.com/product/download.asp?groupid=502&sid=3&lang=en](http://support.wdc.com/product/download.asp?groupid=502&sid=3&lang=en)

It might be a genuine error. The fact that Windows does not notify you does not matter, it will crash at the right moment ;)

---

### Post by bl33d on 2009-09-01
> **forumache said:**
> Such as hardware check utilities provided by your harddisk manufacturer.
Check their support site.

This is an example for Western Digital:   
[http://support.wdc.com/product/download.asp?groupid=502&sid=3&lang=en](http://support.wdc.com/product/download.asp?groupid=502&sid=3&lang=en)

It might be a genuine error. The fact that Windows does not notify you does not matter, it will crash at the right moment ;)

Any linux tools? I can't be bothered to make a partition for Vista.

---

### Post by forumache on 2009-09-01
> **bl33d said:**
> Any linux tools? I can't be bothered to make a partition for Vista.

You said: "Everything works fine. Windows doesn't bitch at me like this does." so I presumed that you have Windows installed.

It doesn't matter, you can visit the site I indicated and see there you can download an ISO image. You burn it to a CD and boot from that CD and test your HDD. The operating system does not matter in this case, it will work even without OS.

The link I indicated is only for WD Caviar HDDs, check your HDD manufacturer website to download the tool you need.

---

### Post by nhasian on 2009-09-01
the new HD tool gives false positives about half the time.  it still needs some tweaking.  i wouldnt worry but if you like you can always just download the bootable iso from the HD manufacturer to test your HD.

---

### Post by bl33d on 2009-09-01
> **forumache said:**
> You said: "Everything works fine. Windows doesn't bitch at me like this does." so I presumed that you have Windows installed.

It doesn't matter, you can visit the site I indicated and see there you can download an ISO image. You burn it to a CD and boot from that CD and test your HDD. The operating system does not matter in this case, it will work even without OS.

The link I indicated is only for WD Caviar HDDs, check your HDD manufacturer website to download the tool you need.

Windows got deleted for Karmic about 4 hours ago, it was also doing the same with dualboot. And I'm out of DVDs...

---

### Post by forumache on 2009-09-01
> **bl33d said:**
> Windows got deleted for Karmic about 4 hours ago, it was also doing the same with dualboot. And I'm out of DVDs...

You can use the new GRUB2 (which is default on Karmic) to boot directly from an iso image, no need to burn it to a DVD first: [http://michael-prokop.at/blog/2009/05/25/boot-an-iso-via-grub2/](http://michael-prokop.at/blog/2009/05/25/boot-an-iso-via-grub2/)

By the way, you don't need a DVD, just a CD will do. But if you don't have it, you have two options: go and buy one (easy) or just use the grub2 iso booting method (hard).

It is good that you have a DVD burner, otherwise only the hard solution would have remained.

---

### Post by bl33d on 2009-09-01
> **forumache said:**
> You can use the new GRUB2 (which is default on Karmic) to boot directly from an iso image, no need to burn it to a DVD first: [http://michael-prokop.at/blog/2009/05/25/boot-an-iso-via-grub2/](http://michael-prokop.at/blog/2009/05/25/boot-an-iso-via-grub2/)

By the way, you don't need a DVD, just a CD will do. But if you don't have it, you have two options: go and buy one (easy) or just use the grub2 iso booting method (hard).

It is good that you have a DVD burner, otherwise only the hard solution would have remained.

Meh nevermind. If it dies I will buy a new one.

---

