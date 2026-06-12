---
title: "dualboot ubuntu 5.04 and mandrake 9.2"
date: 2005-04-29
forum: Installation &amp; Upgrades
---

### Post by -murdoc- on 2005-04-29
can anyone tell me how to dualboot ubuntu 5.04 and mandrake 9.2

---

### Post by -murdoc- on 2005-04-29
i no its a n00b question but please help!

---

### Post by -murdoc- on 2005-04-29
man i want 2 b 100% ubuntu brew!

---

### Post by -murdoc- on 2005-04-29
man i want 2 b 100% ubuntu brew!l

---

### Post by -murdoc- on 2005-04-29
haha!

---

### Post by derrick1985 on 2005-04-29
Yes, technically you can.

Personally, i've never tried it before with Mandrake, but right now I have Ubuntu and Kubuntu on their own partitions and both of their respective entries in my GRUB file, and seem to work no problem.

Should be as easy as having two EXT3 partitions (your root partitions) installing either OS first (I would say Mandrake) then installing your second Ubuntu on the other ext3 partition, and Ubuntu's GRUB should pick up Mandrake in the mix.

Now, if you want a more graphic way of logging in (mandrake's GRUB) then just do what I said in reverse.

---

