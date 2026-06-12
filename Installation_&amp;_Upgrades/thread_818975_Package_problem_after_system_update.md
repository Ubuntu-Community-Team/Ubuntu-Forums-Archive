---
title: "Package problem after system update"
date: 2008-06-04
forum: Installation &amp; Upgrades
---

### Post by DAC1138 on 2008-06-04
I did the system update. It got another kernel image, so I decided to remove the previous 4 kernel images I had. So i went into synaptic to remove them, and when I click apply, it does everything it should. At the end of the process, I'm left an this error and my kernel images still where they are.

The error is big, but I cant copy+paste it here. It basically says, "gzip: stdout: No space left on device."

---

### Post by iaculallad on 2008-06-04
Check the free spaces on the partition:

```
df -h
```

---

### Post by DAC1138 on 2008-06-04
My partitions are fine with free space. The only one that's full is /boot (100mb) which is why I'm trying to get rid of these old kernel images.

---

