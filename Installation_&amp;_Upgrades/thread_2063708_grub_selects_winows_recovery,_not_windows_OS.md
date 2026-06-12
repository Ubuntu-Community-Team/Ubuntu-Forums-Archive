---
title: "grub selects winows recovery, not windows OS"
date: 2012-09-27
forum: Installation &amp; Upgrades
---

### Post by sid0972 on 2012-09-27
after running boot-repair, i selected windows 7 as default OS, but at grub menu it selects windows recovery as default one

how do i make to select windows 7 OS as default?

---

### Post by critin on 2012-09-27
> **sid0972 said:**
> after running boot-repair, i selected windows 7 as default OS, but at grub menu it selects windows recovery as default one

how do i make to select windows 7 OS as default?

I wasn't aware that default could be chosen from boot-repair.  At any rate, recovery is usually one line under the main os.   It shouldn't be first so did you move it?

Perhaps you meant Grub Customizer?  It usually boots the last os used for me, so I have to be aware and choose the partition I want.

---

### Post by darkod on 2012-09-27
I don't know the details of what boot-repair offers in terms of default OS selection. I prefer doing it myself, having full control over it.

And whether the windows recovery will be before or after the windows OS depend on whether the recovery partition on the hdd is before or after the OS partition, since os-prober reads them in order. Some manufacturers make the windows recovery first, some last.

Do you currently have an entry for the windows OS in the grub menu or not?

It would also help if you can post updated bootinfo summary link. Just use boot-repair to create the link and post it, don't do any other operations. When we see what is where, we can recommend what to do.

---

### Post by critin on 2012-09-27
> **sid0972 said:**
> after running boot-repair, i selected windows 7 as default OS, but at grub menu it selects windows recovery as default one

how do i make to select windows 7 OS as default?

Okay Friend, I found the answer to how to set default via boot repair.  You have to use a live ubuntu cd/flash stick to set the default, or it won't apply.  The disk can't be mounted at the time.  Sounds logical, doesn't it?  lol

---

### Post by Mark Phelps on 2012-09-28
> **sid0972 said:**
> after running boot-repair, i selected windows 7 as default OS, but at grub menu it selects windows recovery as default one

how do i make to select windows 7 OS as default?

IF you see two Win7 entries, you can install Grub-Customizer and use it's settings to designate the OTHER Win7 entry as the default.

---

### Post by sid0972 on 2012-09-29
ok i'll try that
but how do i install it??

---

