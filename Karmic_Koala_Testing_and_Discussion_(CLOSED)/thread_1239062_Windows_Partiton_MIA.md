---
title: "Windows Partiton MIA"
date: 2009-08-13
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by Duskao on 2009-08-13
I'm totally aware that this is a bug with Karmic, but I am wondering if anybody can tell me how to alter GRUB 2 so that I can boot into my windows partition as well as ubuntu 9.10? I know it was doable with GRUB 1.5. Please help.

Edit: Sorry it says that it's GRUB 1.9 (something something) goes very quickly. Still same problem though.

---

### Post by Jay_Bee on 2009-08-13
press ESC while the GRUB is showing to see the boot options

---

### Post by Duskao on 2009-08-13
That seems to be unnecessary, right away it shows the kernel for ubuntu 9.10 and the second boot option for that as well, then 2 memory tests. However, there is no windows. The windows partition is still in tact as I can mount it while I am using 9.10. 
I just need to edit the GRUB startup list.

---

### Post by psyke83 on 2009-08-13
> **Duskao said:**
> That seems to be unnecessary, right away it shows the kernel for ubuntu 9.10 and the second boot option for that as well, then 2 memory tests. However, there is no windows. The windows partition is still in tact as I can mount it while I am using 9.10. 
I just need to edit the GRUB startup list.

Boot to Ubuntu, then:

```
$ sudo apt-get install os-prober
$ sudo update-grub2
```

Note: if you recently installed from alpha 3, make sure to do an upgrade before following these steps.

---

### Post by Duskao on 2009-08-13
wow, how much easier is this???? And I finally found the GRUB 2 basics branch as well. Sorry for rehashing. Thanks for the help.

---

