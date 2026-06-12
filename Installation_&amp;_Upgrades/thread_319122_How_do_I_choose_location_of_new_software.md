---
title: "How do I choose location of new software?"
date: 2006-12-15
forum: Installation &amp; Upgrades
---

### Post by sarikan on 2006-12-15
Hi there, 
I'd like to use anohter partition other than the / for installing new applications, since my root partition is almos full at the moment. How can I do that? Is there a way I can configure synaptic so that I can setup new apps to another partition?

---

### Post by bapoumba on 2006-12-15
Hi,
you may already know this : **df -H **will tell you exactly how full are your / and /home (if you have a separate partition for /home).
**sudo apt-get clean** (or aptitude) will free some space on /.

If you do not have a separate /home partition, your /home is in /, and may be filling it up. You could free space from your /home too.

Basically, with a separate /home, my edgy / is 3 Go at the most (I have 9 Go for /, which is way too much ;)).

---

### Post by sarikan on 2006-12-15
Well, thanks for the response, but my situation is like this: I have /home under my /, and there is only 400+ mb space left in the partition. I can add another partition, but I can not resize my current / or move it to a larger drive. I am stuck with the way it is now; and I have to install my new software to a new partition. 
So is it possible to choose a location for installing new software?

---

### Post by mcduck on 2006-12-15
in short, no. Linux doesn't install programs into one place, but instead puts all executable binary files from all programs to one place, all documents to one place and so on. 

But it is possible to copy everything from /usr to the new partition and then mount the partition as /usr, that would make at least most files from user installed applications to go to that new partition.

I would rather suggest using the new partition as /home, keeping all your own files there and freeing space on the root partition that way. It would add the benefit of being able to keep your home and all your files and settings if you ever need to do a reinstall.

---

### Post by bapoumba on 2006-12-15
Well, have you tried **sudo apt-get clean** and removing stuff from your /home directory ?

Packages make it to /usr and indexes on /var when installed with apt-get or aptitude. Moving these partitions somewhere else is not simple.

[http://www.debian.org/releases/stable/i386/ch06s03.html.en]("http://www.debian.org/releases/stable/i386/ch06s03.html.en")
[http://www.debian.org/doc/manuals/reference/ch-package.en.html]("http://www.debian.org/doc/manuals/reference/ch-package.en.html")

Ideally, you make up a new partition, format it ext3, use a live CD on **read only mounted  /**, copy the whole /var or /usr to that new partition, adjust your fstab and keep your fingers crossed when rebooting ;)

I would rather move /home (that I have already done once).

First, you should really check what is taking all your space.

---

### Post by zgornel on 2006-12-15
I used to get inside .deb packages with mc and extract the files i needed :D. Should work.

---

### Post by sarikan on 2006-12-15
Thanks a lot for the suggestions. I'll follow them for sure :)
Regards

Seref Arikan

---

