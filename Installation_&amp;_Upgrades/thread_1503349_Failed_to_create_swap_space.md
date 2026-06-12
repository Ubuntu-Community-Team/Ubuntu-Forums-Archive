---
title: "Failed to create swap space"
date: 2010-06-06
forum: Installation &amp; Upgrades
---

### Post by HornOkPlease on 2010-06-06
Hi, 

I was fortunate enough to acquire some old 2u server hardware (from 2005) on which I wanted to learn how to use Ubuntu. 

Ubuntu fails to mount any partition, in fact gparted cannot detect anything. The installer detects the scsi hdds but then fails when it tries to actually make a partition. 

I've searched this forum, linuxquestions and google. Nothing relevant was found and the solutions involving probing with commands within linux were irrelevant since zero partitions show. (If I've missed something please post the link.)

I've tried Ubuntu 10.4, but settled on trying to install 8.10 since it seems to boot up faster and at least detects the physical hard drives quicker. Also tried windows xp and that says "no hard disk detected". I would've tried windows 7 but the server doesn't have a dvd drive. 

Thanks in advance, any help is appreciated. (Screenshots attached.) 

Joe

---

### Post by spcwingo on 2010-06-06
Have you tried partitioning manually during install?  Just be sure to allocate at least as much swap as physical RAM if you want to hibernate (suspend to disk).

---

### Post by HornOkPlease on 2010-06-06
> **spcwingo said:**
> Have you tried partitioning manually during install?  Just be sure to allocate at least as much swap as physical RAM if you want to hibernate (suspend to disk).

Yes I have tried partitioning manually. It allows me to design all the partitions, but when it's time to commit them to disk the same error occurs.

---

### Post by spcwingo on 2010-06-06
From the live system open a terminal and input this command:

```
sudo fdisk -l
``` (that's a lowercase "L")

Then post the output here.

---

### Post by wojox on 2010-06-06
Do you really need a Swap with 6 gb of memory? Are you really gonna put you server to sleep or suspend?

---

### Post by HornOkPlease on 2010-06-06
> **spcwingo said:**
> From the live system open a terminal and input this command:

```
sudo fdisk -l
``` (that's a lowercase "L")

Then post the output here.

I tried the "sudo fdisk -l" command. The output was blank. It just returned to the command prompt.

---

### Post by spcwingo on 2010-06-06
Wow, I'm at a complete loss as what to try next.  You could always try the server version, alternate install disc, or mini disc.  If not, just hang around here for a while and I'm sure someone else will be along shortly to help you get this sorted out.  I'm sorry that I couldn't get you going.  :(

---

### Post by HornOkPlease on 2010-06-06
No problem spcwingo, thanks for trying.

---

### Post by HornOkPlease on 2010-06-06
> **wojox said:**
> Do you really need a Swap with 6 gb of memory? Are you really gonna put you server to sleep or suspend?

I guess I could do with less, but my main problem is getting linux to create a partition, right now it doesn't seem to be recognizing my harddrives beyond step 3 of the install process.

---

