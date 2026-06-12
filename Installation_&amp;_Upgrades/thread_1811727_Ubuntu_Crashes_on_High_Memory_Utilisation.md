---
title: "Ubuntu Crashes on High Memory Utilisation"
date: 2011-07-25
forum: Installation &amp; Upgrades
---

### Post by Balvinder25 on 2011-07-25
Hello All,

I have recently started  to get this problem but not sure if its hardware related or if is it ubuntu related.

whenever i do some sort of heavy resource using work, eg copy dvd or import files into shotwell, ubuntu just freezes and i have to restart it .

i have dual core 2.4, 2 gb ram, 160 gb hard drive space, 2 gb swap, but still this happens..

any help would be much appreciated.

---

### Post by dino99 on 2011-07-25
be sure that swap is well used in that case, and large enough

watch the logs 

have a look at valgrind & fwts

[https://wiki.ubuntu.com/Valgrind](https://wiki.ubuntu.com/Valgrind)

[https://wiki.ubuntu.com/Kernel/Reference/fwts](https://wiki.ubuntu.com/Kernel/Reference/fwts)

---

### Post by eric-yorba on 2011-07-25
Try running Memtest86. It's possible there's a bad bit in your computer's memory.

---

### Post by Balvinder25 on 2011-07-26
hello dino99 & eric-yorba, 

I think i found the problem, i had recently installed another repaired memory chip, so i removed it and then tried doing the same task again, and it worked fine. no crashes and no hangs.i suppose i will have to shell out some money now for a new one but im happy to find out that its not an ubuntu issue.

Thank you so much !

---

