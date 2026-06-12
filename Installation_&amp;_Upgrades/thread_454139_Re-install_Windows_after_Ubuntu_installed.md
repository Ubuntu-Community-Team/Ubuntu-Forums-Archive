---
title: "Re-install Windows after Ubuntu installed"
date: 2007-05-25
forum: Installation &amp; Upgrades
---

### Post by linhtinh321 on 2007-05-25
Here is my situation : 
     + Firstly I have windows XP installed.
     + Then, I install Ubuntu on the same hard-disk, and I can boot using Grub, everything is fine.
     + Now, my windows XP got some problems, and I am going to re-install it or more exactly restore it using Norton Ghost 8.0. I made this image ghost file before installing Ubuntu.

Hence, I don't know what will happen after I restore windows XP from the image ghost file :
     + Will Grub work as usual ? ( dual boot and I can choose between Ubuntu and Windows XP )
     + If it won't work, what will I do to make my computer works as before I restore windows ? will re-install Grub solve the problem ? 
     + An off-topic question, will MBR change after I restore windows using Norton Ghost ? 
I surfed this forum for these things but there is a mess in my mind, hence please show me the right way to go.
Thanks for your reading and advices .

---

### Post by Paperclips4u on 2007-05-25
For reference, what type of problems is XP having?

On to the imaging... It all depends on what exactly your image is composed of. Did you take the image of the entire drive or just the XP partition? If you only took an image of the XP system partition, it should be okay to wipe and reimage the partition now. Otherwise don't image your drive because it will over-write the other partitions and cause even more problems.... etc.

Basically, if the image size is equal or less than your current XP partition it should be okay as long as you only image the partition. If it's bigger than your partition it will corrupt other partitions.

---

### Post by linhtinh321 on 2007-05-25
> For reference, what type of problems is XP having?
I can not use the Windows Media Player and other software which require WMP such as Sopcast.
> On to the imaging... It all depends on what exactly your image is composed of. Did you take the image of the entire drive or just the XP partition? If you only took an image of the XP system partition, it should be okay to wipe and reimage the partition now. Otherwise don't image your drive because it will over-write the other partitions and cause even more problems.... etc.

Basically, if the image size is equal or less than your current XP partition it should be okay as long as you only image the partition. If it's bigger than your partition it will corrupt other partitions.
I just take the image of the XP system partition only. 
By the way, just want to update, I already restore windows and everything is ok now. I can use both OS and grub works fine.

---

### Post by Paperclips4u on 2007-05-26
Awesome :)

---

