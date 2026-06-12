---
title: "Quesetion about swap partitions..."
date: 2006-06-03
forum: Installation &amp; Upgrades
---

### Post by darthvivi on 2006-06-03
I've installed Ubuntu Dapper Drake correctly, and everything is working fine so far, but when I installed I chose the first choice (resized Windows XP partition) so I just dragged the slider to 85% and clicked "next."

My question is...did that automatically set up a swap partition for me? If so how much?

---

### Post by jpkotta on 2006-06-03
Use the ```
swapon -s
``` command to check if you have a swap partition mounted (it also tells you the size and usage).

---

