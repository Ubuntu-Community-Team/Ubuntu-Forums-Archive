---
title: "RAID Boot Problem"
date: 2009-04-09
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by Slalomsk8er on 2009-04-09
I updated to the Beta and having problems with booting from a software RAID1.

Some how it looks like mdadm does nothing in the initrd scripts as I can boot if I execute:

```
# mdadm --assemble --scan
# exit
```

After that the System resumes the boot process like it should with out my intervention.

Does some one know how to fix this?


Regards, Dominik

---

