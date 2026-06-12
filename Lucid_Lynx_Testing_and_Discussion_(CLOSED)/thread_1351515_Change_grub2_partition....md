---
title: "Change grub2 partition..."
date: 2009-12-10
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by Xgen on 2009-12-10
I had grub2 on partition 10 as the loader and somehow it switched to the grub2 on partition 9. What command will make partition 10 the grub2 loader?

---

### Post by cariboo on 2009-12-10
A lot more info would be helpful. what does your partition setup look like?

---

### Post by kansasnoob on 2009-12-10
> **cariboo907 said:**
> A lot more info would be helpful. what does your partition setup look like?

+1! Need much more info, maybe start with:

```
sudo fdisk -l
```

Also remember that partition numbering changed in grub2. Drive numbering still begins with zero, but partition numbering begins with one.

---

### Post by VMC on 2009-12-10
> **Xgen said:**
> I had grub2 on partition 10 as the loader and somehow it switched to the grub2 on partition 9. What command will make partition 10 the grub2 loader?
I had a very similar situation. Ubiquity wouldn't let me install on a ext4 partition so I had to delete that partition first, then install alpha. 

When I did it that way my partitions were out of order. Using fdisk I fixed the order again, but that reversed everything. So instead of grub being on sda7, which is where alpha is, it now is on sda11, the original karmic?

I then needed to chroot to alpha and run "grub-install /dev/sda", to re-install grub back to alpha.

---

### Post by Xgen on 2009-12-11
Thanks, VMC - "sudo grub-install /dev/sda" corrected the problem.

---

