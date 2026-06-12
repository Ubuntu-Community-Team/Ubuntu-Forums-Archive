---
title: "Can't extract an ISO file"
date: 2012-06-09
forum: Installation &amp; Upgrades
---

### Post by Hadar0x on 2012-06-09
Hello everybody,

I was looking for the answer for a while, thought this might be the place.
I downloaded an ISO file compressed to .rar files, and when I try to unrar it with the archive manager it looks like it works, but it take only few seconds (700MB file) and the iso file is not where it supposed to be.

[Here's a snapshot.]("http://postimage.org/image/recqosc5x/")

Hope you can help. Thanks ahead..
Hadar

---

### Post by dino99 on 2012-06-09
take care to only use genuine ubuntu iso file(s), and i've never seen them compressed.

which rar package(s) are installed on your system ? On my side, both unrar & p7zip-rar are installed. Load synaptic for checking:

sudo apt-get install synaptic
sudo synaptic

---

### Post by Hadar0x on 2012-06-09
Hi

Thanks a lot. I checked it and I only had unrar-free. I installed 7zip and rar and it worked.

I'll mark it as SOLVED.

Thanks again,
Hadar

---

