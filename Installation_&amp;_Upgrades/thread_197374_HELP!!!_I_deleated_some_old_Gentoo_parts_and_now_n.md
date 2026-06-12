---
title: "HELP!!! I deleated some old Gentoo parts and now need to reinstall GRUB"
date: 2006-06-15
forum: Installation &amp; Upgrades
---

### Post by Dylnuge on 2006-06-15
I made a huge mistake:

I used to use Gentoo. I dual boot with Windows. I decided to deleate my Gentoo partitions (3 extended parts). Ubuntu automaticly made some partitions in the now unallocated space, which was I was fine with (nothing harmed windows). Now Grub gives me an Error 22. Being a bit experianced with Grub (but not really), I know that last time this happened, I just changed by Grub.conf. Only thing is, I did that from a fully functioning Gentoo Partition. How do I do it from the Ubuntu LiveCD (I can chroot if nessicary, its the same as Gentoo, right?)

Thanks,
Dylan

EDIT/PS: I know my main problem is with Grub wanting to see my 7 old parts (which contained gentoo) and only getting my new 5 parts.

---

### Post by ayoli on 2006-06-15
maybe that can help:
[https://wiki.ubuntu.com/phbc50/howtos/how-to_reinstall_grub?highlight=%28grub%29%7C%28reinstall%29]("https://wiki.ubuntu.com/phbc50/howtos/how-to_reinstall_grub?highlight=%28grub%29%7C%28reinstall%29")

---

### Post by Dylnuge on 2006-06-15
What I need is wiat to type in my /boot/grub/menu.lst to add windows to the list. My Windows XP runs on Sda2, or (hd0, 1). (Sda1 is recovery).

---

### Post by Dylnuge on 2006-06-16
What do I type to do this?

---

### Post by grexk on 2006-06-16
Try "sudo update-grub"

---

### Post by Dylnuge on 2006-06-16
Interesting thing is, I didn;t realise that Ubuntu automaticly configured grub to work with my Windows dual-boot. Noticed it last night, and now everything is fine.

---

