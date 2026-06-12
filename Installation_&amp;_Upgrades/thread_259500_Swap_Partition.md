---
title: "Swap Partition"
date: 2006-09-17
forum: Installation &amp; Upgrades
---

### Post by Loft on 2006-09-17
Hey guys.  Just a general question about swap partitions and their benefits.

When I install Ubuntu (or any other Linux distro for that matter) I'm always recommended to create a swap partition.  Now I usually do, usually about 1GB in size, not really a problem, but I've always wondered what exactly is it for?  I've never really questioned it until I installed an ext3 partition reader in Windows.

It would read my Ubuntu partition perfectly, but when I came to go on the swap partition, it said the volume needed formatting.  Now excuse my stupidness, but if it's not formatted, then what exactly is it doing?  It was definatly the right partition to corresspond with the swap partition.

So the question is, what does the swap partition do, and do I really need it?

---

### Post by jd65pl on 2006-09-17
Hello,

I think the Ubuntu Wiki May be able to help you![URL="https://help.ubuntu.com/community/SwapFaq"]

https://help.ubuntu.com/community/SwapFaq[/URL]

If you have plenty of ram then a swap partition might not be necessary. I have a gig of ram and have never used the swap partition (a further 1gb) however I don't do much resource heavy computing such as gaming or image editing.

Thanks

J

---

### Post by coffeecat on 2006-09-17
> **Loft said:**
> It would read my Ubuntu partition perfectly, but when I came to go on the swap partition, it said the volume needed formatting.  Now excuse my stupidness, but if it's not formatted, then what exactly is it doing? 

No, you're not being stupid; it's Windows being stupid. (Nothing new there then.... :roll:) Your swap partition is formatted (but not as ext3) but not in a way that Windows recognises so, thinking in it's arrogance that it is the only OS in the Universe, it's telling you that a partition that it doesn't recognise is unformatted. :)

---

