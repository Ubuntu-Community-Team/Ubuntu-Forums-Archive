---
title: "Disk compression"
date: 2008-08-18
forum: Installation &amp; Upgrades
---

### Post by Borsook on 2008-08-18
Does any of the file systems supported by Ubuntu allow a per file compression in the manner similar to Ntfs? If so, can it be done in the GUI?

---

### Post by Pumalite on 2008-08-18
This might help:
[http://ubuntuguru.wordpress.com/2007/03/09/whats-the-best-file-compression-method/](http://ubuntuguru.wordpress.com/2007/03/09/whats-the-best-file-compression-method/)
[https://help.ubuntu.com/community/FileCompression](https://help.ubuntu.com/community/FileCompression)
[http://ubuntuforums.org/showthread.php?t=708600](http://ubuntuforums.org/showthread.php?t=708600)

---

### Post by Borsook on 2008-08-18
> **Pumalite said:**
> This might help:
[http://ubuntuguru.wordpress.com/2007/03/09/whats-the-best-file-compression-method/](http://ubuntuguru.wordpress.com/2007/03/09/whats-the-best-file-compression-method/)

The link is very interesting, but this is not what I mean - I have in mind a compression build in the file system itself that allows to compress individual files or whole partitions and their content can be used normally (i.e. it is unpacked on the fly) - such a feature is present in NTFS.

---

### Post by Pumalite on 2008-08-18
[http://www.partimage.org/Main_Page](http://www.partimage.org/Main_Page)

---

### Post by adam_kimber on 2008-08-18
Per file compression generally means creating an archive such as a zip, a tar or a 7z. 7z is supposed to be really good at file size compression, so if you want a small file then thats the way to go. Will have to wait it takes a while to compress compared to say zip. 

However as you mention NTFS and that is disk compression you might want to have a look at the post by diaa at the bottom of this [link]("http://ubuntuforums.org/showthread.php?t=245430")

---

### Post by insane_alien on 2008-08-18
i think he is talking about filesystem compression where you can transparently compress a single file or the whole filesystem.

---

### Post by adam_kimber on 2008-08-18
Then something like compfused, listed in my link, would be what he was after... :D

---

### Post by Borsook on 2008-08-18
> **insane_alien said:**
> i think he is talking about filesystem compression where you can transparently compress a single file or the whole filesystem.
yes that's exactly it. :)

---

### Post by Borsook on 2008-08-18
> **adam_kimber said:**
> Then something like compfused, listed in my link, would be what he was after... :D

Yes it is pretty close to what I had in mind, a pity none of the many file systems available has this functionality built in, not to mention included in the GUI...

---

### Post by adam_kimber on 2008-08-18
I will add that to my list of things that Linux is not as good as Windows. Which TBH is getting smaller by the day. Wireless and printing were my woes but they are pretty much working these days. I even have my XBOX360 wireless conroller working :D Next up integrated transparent filesystem compression. ITFC. :P

---

