---
title: "BFG Nvidia 680i + RAID 5 + Feisty"
date: 2007-09-06
forum: Installation &amp; Upgrades
---

### Post by staulkor on 2007-09-06
I am trying to do a RAID 5 with 5x500gb sata2 drives on a BFG Nvidia 680i mobo and I cant get this thing working. I had RAID 0 working on the old nforce 4 board and I am trying to replicate the procedure, but it just will not work.

If i type 'dmraid -tay' I get the following:

```
nvidia_ddbieahe: 0 3907092480 raid45 core 2 131072 nosync raid5_ls 1 128 5 -1 /dev/sda 0 /dev/sdd 0 /dev/sdf 0 /dev/sdb 0 /dev/sdc 0
```

'dmraid -r' gives me:

```
/dev/sda: nvidia, "nvidia_ddbieahe", raid5_ls, ok, 976773166 sectors, data@ 0
/dev/sdb: nvidia, "nvidia_ddbieahe", raid5_ls, ok, 976773166 sectors, data@ 0
/dev/sdc: nvidia, "nvidia_ddbieahe", raid5_ls, ok, 976773166 sectors, data@ 0
/dev/sdd: nvidia, "nvidia_ddbieahe", raid5_ls, ok, 976773166 sectors, data@ 0
/dev/sdf: nvidia, "nvidia_ddbieahe", raid5_ls, ok, 976773166 sectors, data@ 0
```

'ls -l /dev/mapper' gives me:

```
total 0
crw-rw---- 1 root root 10, 63 2007-09-07 01:33 control
```

Dont know what is going on. Also, is the RAID config I am doing hardware or software? I mean it sounds like hardware because the mobo is controlling it and everything, but I could be wrong. :(

---

