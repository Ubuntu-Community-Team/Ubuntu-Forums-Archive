---
title: "gutsy boot into console text mode"
date: 2007-10-31
forum: Installation &amp; Upgrades
---

### Post by taikhoanphu on 2007-10-31
I use debootstrap to build a gutsy filesystem for user mode linux. Then the boot hang at running local boot scripts. I want to change to default run level to 3 but there is no /etc/inittab and I am not familiar with upstart. Any help would be much appreciated.
Thanks.
Matt

---

### Post by Bliepo32 on 2007-10-31
I don't know if this will work (I am not an expert), but you could try it anyway:
```

gdm start

```

It probably will not work, but you could try never the less...

---

### Post by taikhoanphu on 2007-10-31
No that wouldn't help. There is no GUI element on the core filesystem. I need to see the logon console (i.e. text mode)

---

