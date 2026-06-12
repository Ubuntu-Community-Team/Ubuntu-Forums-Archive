---
title: "can I delete /usr/src/linux-2.6.25"
date: 2008-05-27
forum: Installation &amp; Upgrades
---

### Post by Vivian-Synecdoche on 2008-05-27
Hello,

I used kernelcheck to compile the new linux kernel 2.6.25.

After a while, I realized that the difference between my previous kernel, linux-2.6.24-16-generic, and the new one, kernel 2.6.25-4, was rather minimal. When I realized that there were some broken-ness (read: unexplained crashes and incompatibilities), I decided to go back to my 2.6.24.

I did this by removing the linux header and image files specific to 2.6.25 via synaptics.

Everything's now back to regular .24 and I'm still awesome.

But now there's a folder (/usr/src/linux-2.6.25) residing in my HDD and taking up about 2GB of space. I'm wondering if I can *just* rm the folder or do I have to do something else before removing it. I don't want to break anything - please help.

---

### Post by buzzbo on 2009-01-15
bump!

I have a similar question.  I am cleaning things up.  At one time, I was messing around with compiling the kernel from source, and now I see that I have:

/usr/src/linux-source-2.6.22 

which is 3.0 GB

fwiw I lately I am booting vmlinuz-2.6.27-7-generic

so is it OK to delete?

Buzz

---

### Post by rednectar on 2010-02-09
buzzbo - did you ever find out? I also need some spare disk space and I see in /usr/src:
 linux-headers-2.6.24-16
 linux-headers-2.6.24-16-generic
 linux-headers-2.6.24-22
 linux-headers-2.6.24-22-generic

I'd like to delete this stuff - its 83MB

---

### Post by buzzbo on 2010-02-09
> **rednectar said:**
> buzzbo - did you ever find out? I also need some spare disk space and I see in /usr/src:
 linux-headers-2.6.24-16
 linux-headers-2.6.24-16-generic
 linux-headers-2.6.24-22
 linux-headers-2.6.24-22-generic

I'd like to delete this stuff - its 83MB

Pretty sure I deleted it with no problems.  It's probably safe to wipe.  You may want to make absolutely sure you have a newer compiled kernel, when you "uname -a".

---

