---
title: "problems with update-grub"
date: 2008-10-26
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by Tuig on 2008-10-26
Hi,

recently, ubuntu-ibex failed while updating the kernel.
I've traced it down to a setting in /boot/grub/menu.lst.

If 
```
# updatedefaultentry=false
```
is set to "true", update-grub fails, and this causes installation
of new kernels via apt-get update to fail.

This problem started recently, 2.6.27-4 still installed fine.
Does anyone else have this problem ? (as in, should a bug report be filed,
or did I just do something wrong?

---

### Post by caljohnsmith on 2008-10-26
I just helped someone else recently who was getting some rather bizarre behavior from the update-grub command, and we fixed it by reinstalling Grub; you have nothing to lose, so I would give it a shot and see if it maybe fixes your problem:
```
sudo apt-get purge grub
sudo apt-get install grub
```
And then try running the update-grub script again:
```
sudo update-grub
```
Let me know if that changes anything. :)

---

