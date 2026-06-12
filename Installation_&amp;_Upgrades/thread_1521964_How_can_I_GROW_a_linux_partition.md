---
title: "How can I GROW a linux partition?"
date: 2010-07-01
forum: Installation &amp; Upgrades
---

### Post by Dara Javaherian on 2010-07-01
My hard drive looks like this:

[IMG]http://i218.photobucket.com/albums/cc189/DaraJava/Screenshot--dev-sda-GParted.png[/IMG]

However, I want to shrink the Windows partition and grow the Linux one. 

When I shrink the Windows partition, like this:

[IMG]http://i218.photobucket.com/albums/cc189/DaraJava/Screenshot--dev-sda-GParted-1.png[/IMG]

I can only shrink my Ubuntu partition. What's up with this?! It doesn't seem to see the unallocated space on my hard drive. Is there any way to grow my Linux partition?

Thanks.

N.B. I tried using the GParted Live CD (/dev/sda2/5/6 wasn't mounted) with no avail.

---

### Post by ronparent on 2010-07-01
You have to 1st expand the extended partition into the unallocated space produced by shrinking the win partition. You then will have to boot into a live cd - you can't do anything with a mounted partition. From the live cd just expand sda5 to fill the unallocated space in the extended partition. It will take some time for the operation to complete because all of the data on sda5 will have to be moved. Good luck.

---

### Post by Dara Javaherian on 2010-07-01
> **ronparent said:**
> You have to 1st expand the extended partition into the unallocated space produced by shrinking the win partition. You then will have to boot into a live cd - you can't do anything with a mounted partition. From the live cd just expand sda5 to fill the unallocated space in the extended partition. It will take some time for the operation to complete because all of the data on sda5 will have to be moved. Good luck.


Great! I was trying to grow my Linux partition only. I first had to grow the extended partition and then I had to grow the Linux partition.

---

