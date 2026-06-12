---
title: "cylinders, heads or sectors? what is my drive geometry."
date: 2007-02-28
forum: Installation &amp; Upgrades
---

### Post by newbwarning on 2007-02-28
Can anyone tell me how to determine my drive geometry?

My install is stopping at IDE recognition.

Thank you.

---

### Post by KhaaL on 2007-05-21
I'd also like to know this, however for a enitrely diffrent reason... running feisty kubuntu

---

### Post by kh4nh on 2007-05-21
In terminal, run:
```
sudo fdisk -l
```

This command will list all of your hard drives and their geometry.

Have fun

---

