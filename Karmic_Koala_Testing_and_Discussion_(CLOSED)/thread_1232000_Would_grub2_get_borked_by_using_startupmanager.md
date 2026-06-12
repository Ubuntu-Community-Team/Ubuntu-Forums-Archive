---
title: "Would grub2 get borked by using startupmanager ?"
date: 2009-08-05
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by philinux on 2009-08-05
It 's a nice little gui for grub stuff but not sure if it's compatible with grub2.

---

### Post by phenest on 2009-08-05
I would expect it to do nothing of the sort. In fact, I would expect it to do nothing. Scripts for Grub1 and 2 are in different locations to start with. And they work in very different ways.

---

### Post by taavikko on 2009-08-05
From one of it's homepage: [http://web.telia.com/~u88005282/sum/index.html](http://web.telia.com/~u88005282/sum/index.html)

> StartUp Manager, or SUM, is a gui tool for changing settings for Grub, Grub2, Usplash and Splashy.
SUM should work with recent versions of Debian and Debian-based distributions such as Ubuntu.

But not too sure how it actually works with grub2

---

### Post by philinux on 2009-08-05
So it's not yet updated to work with grub2.

[edit] Must not be able to type fast enough today lol.

---

### Post by phenest on 2009-08-05
Only one way to find out, I guess. I have VM with alpha 3 installed so I'll test with that.

---

### Post by phenest on 2009-08-05
I changed the boot resolution from 640x480 to 800x600 successfully.

EDIT: An it seems that you need a background the same size as the resolution. Grub2 doesn't seem the center or stretch the image.

---

### Post by philinux on 2009-08-05
Thanks for the test.

I had trouble with grub2 yesterday, had to reinstall it. I've got it on sdb1 partition and I think it don't like it. It gave a warning about putting grub2 on a partition instead of the mbr. I'm Dual booting from sda1 which has Jaunty on.

---

### Post by dentaku65 on 2009-08-05
I've used startupmanager with Grub2 and it works... well can't do much, but I've changed the timeout at the boot from 5sec to 10sec and the application did it. Can manage the vga and bootsplash too, but not (yet) the grub image or color. I did not changed my vga option anyway.

---

### Post by plun on 2009-08-05
You have comments from the author himself within this thread 

[http://ubuntuforums.org/showpost.php?p=7459352&postcount=45](http://ubuntuforums.org/showpost.php?p=7459352&postcount=45)

---

### Post by philinux on 2009-08-05
> **plun said:**
> You have comments from the author himself within this thread 

[http://ubuntuforums.org/showpost.php?p=7459352&postcount=45](http://ubuntuforums.org/showpost.php?p=7459352&postcount=45)

Cheers plun.

---

