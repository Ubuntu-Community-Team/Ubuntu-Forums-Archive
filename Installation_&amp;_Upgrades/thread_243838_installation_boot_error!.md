---
title: "installation boot error!"
date: 2006-08-25
forum: Installation &amp; Upgrades
---

### Post by kkxecutor on 2006-08-25
since my PC doesn't like running the installer without

```
boot acpi=off
```

i run using that, and i get an error.
```

[738.375612]VFS: cannot open root device "<NULL>" or unknown-block(8,1)
[738.375683]please append a correct "root=" boot option
[738.375746]Kernel panic - not syncing: VFS: unable to mount root fs on unknown-block(8,1)
[738.375829]   
```

im trying to install "Version 6.06 LTS for your PC"
my pc is a HP pavillion a.509
2.6ghz intel celeron
1024mb ram
NVIDIA Geforce 5200

any help appreciated :)

---

### Post by cleentrax on 2006-08-25
> 
im trying to install "Version 6.06 LTS for your PC"
my pc is a HP pavillion a.509
2.6ghz intel celeron
1024mb ram
NVIDIA Geforce 5200

any help appreciated :)

Is this a fresh install on an empty HD, or is this going to be a dual boot with a current Windows install? What happens when you don't do the acpi=off?

---

### Post by kkxecutor on 2006-08-31
dual boot with windows XP Pro, without acpi=off it loads the kernel then reboots...

---

