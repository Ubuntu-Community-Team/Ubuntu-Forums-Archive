---
title: "Creating image of multi-partition hard drive"
date: 2013-12-29
forum: Installation &amp; Upgrades
---

### Post by flxrht on 2013-12-29
Hi

I'm not sure which category to post this under but figured "installation & upgrades" would be most relevant.

I recently bought a new Lenovo Thinkcentre desktop with Windows 7 pre-installed.  The hard drive on the desktop has three partitions: 1-SYSTEM_DRV (is hidden -no drive letter), 2-Windows7_OS (C drive) and 3-Lenovo_Recovery (Q drive).  My goal is to create an image of 1 and 2 so that if the hard drive ever becomes corrupted, I can simply re-image the hard drive. 

In order to avoid having to download additional software or add complexity, I was planning on just using a Ubuntu 12.04 live cd and the dd command to create the image and use the dd command again in the future to re-image the hard drive if needed.

Can someone help me in creating this image of the two partitions?

---

### Post by sudodus on 2013-12-29
Welcome to the Ubuntu Forums :-)

I can help you to use ***dd***. But it is nick-named 'disk destroyer' because

1. It is very powerful
2. It does what you tell it to do
3. It does not ask any questions

So if you tell it to do something that you really don't want to do (for example by a small typing error), you can destroy the content of the drive instead of backing it up.

Instead I suggest that you download ***Clonezilla*** and make a live CD/DVD/USB drive and use it to make a clone (exact copy) or a compressed image of the whole drive or selected partitions. An extra bonus is that Clonezilla copies only the blocks containing data and skips the unused (empty) blocks, so it is much faster than using dd.

---

### Post by oldfred on 2013-12-29
> [Last edited by sudodus]("http://ubuntuforums.org/posthistory.php?p=12886042"); 7 Minutes Ago at 01:35 PM. 				 				 					Reason: typing error 				 			

Good thing sudodus was not using dd to make his post. :)

---

