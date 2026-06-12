---
title: "Triple boot Windows 7, Karmic, and Lucid"
date: 2010-02-18
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by david20063 on 2010-02-18
I am trying to triple boot Windows 7, Ubuntu Karmic, and Ubuntu Lucid. I have my partitions set up like this.

dev/sda2 Windows 7
dev/sda3 /
dev/sda4 /home
dev/sda6 (where i want Lucid root)
dev/sda5 swap

My problem is it won't let me mark sda6 as my / cause I already have a root so how do i set it up to let me install lucid root on sda6?

---

### Post by oldfred on 2010-02-18
Just call it Lucid or beta. The label is just used for identification. When you do the install you choose manual and select that partition as root regardless of its label. You can use the same swap also.

---

### Post by david20063 on 2010-02-21
Thanks that has been driving me crazy I didn't think of that.

---

