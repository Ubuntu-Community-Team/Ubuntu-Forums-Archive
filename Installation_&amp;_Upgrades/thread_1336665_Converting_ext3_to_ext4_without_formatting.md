---
title: "Converting ext3 to ext4 without formatting"
date: 2009-11-24
forum: Installation &amp; Upgrades
---

### Post by theblackphantom on 2009-11-24
Hello, I want to convert ext3 to ext4 on Ubuntu 9.10 Karmic, I can't unmount my filesytem since it is inuse:S, and I dont want to format it ( long story ) help please.

I used the way where you have to enter e2fprogs way but I have to unmount my filesystem, and I don't have the 9.04 neither the 9.10 live cd, I only have the 8.10 and 8.04 LTS

Any other way ???

---

### Post by kiran88pnjr on 2009-11-24
> **theblackphantom said:**
> Hello, I want to convert ext3 to ext4 on Ubuntu 9.10 Karmic, I can't unmount my filesytem since it is inuse:S, and I dont want to format it ( long story ) help please.

I used the way where you have to enter e2fprogs way but I have to unmount my filesystem, and I don't have the 9.04 neither the 9.10 live cd, I only have the 8.10 and 8.04 LTS

Any other way ???

Just visit this link bro : [http://www.debian-administration.org/article/Migrating_a_live_system_from_ext3_to_ext4_filesystem](http://www.debian-administration.org/article/Migrating_a_live_system_from_ext3_to_ext4_filesystem)

Cheers!!! TC \\:D/\\:D/\\:D/

---

### Post by stlsaint on 2009-11-24
see here [UbuntuBlog]("http://ubuntu-blog.com/how-to-convert-partitions-from-ext3-to-ext4-without-formatting-the-hard-disk")

---

### Post by theblackphantom on 2009-11-24
> **kiran88pnjr said:**
> Just visit this link bro : [http://www.debian-administration.org/article/Migrating_a_live_system_from_ext3_to_ext4_filesystem](http://www.debian-administration.org/article/Migrating_a_live_system_from_ext3_to_ext4_filesystem)

Cheers!!! TC \\:D/\\:D/\\:D/

Thanks for your reply Kiran, everything went smoothly following the link you gave until when I wanted to mount the filesystem in read-only I got this:


```
hadi@hadi-laptop:~$ sudo mount -o remount,ro /
mount: / is busy
```

How to make it unbusy lol

---

### Post by kiran88pnjr on 2009-11-25
> **theblackphantom said:**
> Thanks for your reply Kiran, everything went smoothly following the link you gave until when I wanted to mount the filesystem in read-only I got this:


```
hadi@hadi-laptop:~$ sudo mount -o remount,ro /
mount: / is busy
```

How to make it unbusy lol

I've no knowledge about it. Please post new thread about it & share it with me. I want to know the solution too.

TC !!!!!!!!!!!!!  :popcorn:

---

