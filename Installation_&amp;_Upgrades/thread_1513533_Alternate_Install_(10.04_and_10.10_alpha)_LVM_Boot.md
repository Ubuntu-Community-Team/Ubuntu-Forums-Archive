---
title: "Alternate Install (10.04 and 10.10 alpha) LVM Boot Problem"
date: 2010-06-19
forum: Installation &amp; Upgrades
---

### Post by Freddie on 2010-06-19
Hi all,

Today I decided to replace my 9.04 install with 10.04. (I did this on a separate hard disk.) As I am a big fan of LVM I used the 'Alternate' install CD.

Everything installed fine.

However, upon booting I observed two things: firstly there was no grub menu. No countdown timer, no menu. Just a flickering cursor. After 15 seconds or so I got a message telling me that:
```

/dev/mapper/bromine-root

```

(My root partition.) does not exist and that it had given up waiting. Finding this kind of strange I tried the alpha of 10.10 --- same again.

Hence I have two questions: firstly, where did the nice grub menu go; secondly, what is wrong with LVM and grub these days? At the initframfs prompt I am thrown to there are some LVM utilities and they appear to show my volumes.

Switching back to my old pair of hard disks and everything works as expected (i.e, the hardware is fine and supported by Linux.)

Regards, Freddie.

---

### Post by darkod on 2010-06-19
Did you make separate /boot partition outside the LVM? I think you need to do this for LVM.

---

### Post by Freddie on 2010-06-19
> **darkod said:**
> Did you make separate /boot partition outside the LVM? I think you need to do this for LVM.

Yep. Ensured that boot was not on under the control of LVM.

Regards, Freddie.

---

