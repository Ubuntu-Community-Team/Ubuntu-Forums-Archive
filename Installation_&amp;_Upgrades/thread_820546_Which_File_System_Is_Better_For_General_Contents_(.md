---
title: "Which File System Is Better For General Contents (media, doc,picture etc)"
date: 2008-06-06
forum: Installation &amp; Upgrades
---

### Post by azwar on 2008-06-06
I've been using ext3 since feisty fawn, as it's the default FS in ubuntu. Then I read an article about JFS on wikipedia that JFS is fast and reliable [http://en.wikipedia.org/wiki/JFS_%28file_system%29#JFS_in_Linux](http://en.wikipedia.org/wiki/JFS_%28file_system%29#JFS_in_Linux) . Then I used the JFS on gutsy which i notices some speed when boot time... 
Now I heard that the JFS Maintainer [http://linux.derkeiler.com/Mailing-Lists/Debian/2008-01/msg01808.html](http://linux.derkeiler.com/Mailing-Lists/Debian/2008-01/msg01808.html)  
not advice JFS for production use. So between reiserfs, ext2, ext3, jfs, & xfs, which is better for general desktop use.

---

### Post by zvacet on 2008-06-06
You said it all.Ext3 is default in Ubuntu,so use it.

---

### Post by azwar on 2008-06-06
Yes it's the default ubuntu FS. But is there any way to avoid the fsck screen when I boot my pc. (not on every boot up)

---

### Post by VMC on 2008-06-06
> **azwar said:**
> Yes it's the default ubuntu FS. But is there any way to avoid the fsck screen when I boot my pc. (not on every boot up)

I just read up on this yesterday when someone suggested I use ReiserFS. I haven't given it much thought up until now. I have heard of a new ext4 coming. Then suggestion came on the heels of asking if ubuntu could use ReiserFS V4.

Here is a link that ran some comparisions:
[http://linuxgazette.net/102/piszcz.html](http://linuxgazette.net/102/piszcz.html)

I haven't seen much on ubuntu forums though. I'm using the default. Maybe I'll change later. Right now I just want to make sure ubuntu 8.04 is stable enough for me. I have been using it exclusively for over a month. No Windows! Going "cold turkey", if you will.

---

### Post by zvacet on 2008-06-06
>  But is there any way to avoid the fsck screen when I boot my pc. (not on every boot up)

You can do it with **tune2fs**.Look man tune2fs.

---

