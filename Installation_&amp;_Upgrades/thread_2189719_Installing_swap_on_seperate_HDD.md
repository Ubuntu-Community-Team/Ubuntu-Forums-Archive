---
title: "Installing swap on seperate HDD"
date: 2013-11-23
forum: Installation &amp; Upgrades
---

### Post by alex199020 on 2013-11-23
Hi,

i'm about to install ubunutu on my PC but my boot drive is only small so would like to put the swap partition on a secondary drive. I also don't have the secondary HDD yet so won't be able to specify it during the install. How do i go about adding a swap in after i've installed and got my secondary HDD?

Thanks in advance
Alex

---

### Post by Bashing-om on 2013-11-23
alex199020; Hi !

Adding swap at a later time is no big deal ( enough ram, and no intentions to hibernate the machine, may not even have to have swap)
Fire up GParted and make the partition;
"sudo blkid" to get the uuid of the swap partition;
edit "/etc/fstab" to add the swap partition.
for reference: mine;
```

sysop@1304mini:~$ sudo blkid
[sudo] password for sysop: 
/dev/sda1: LABEL="1304mroot" UUID="3a47f1f1-ed1f-4134-b6aa-be101a7d97b4" TYPE="ext4" 
/dev/sda2: LABEL="1304mhome" UUID="29a6fc4f-ff12-4cac-8eb1-e98e50f1107f" TYPE="ext4" 
[color=red]/dev/sda5: UUID="192a4783-56fa-4fd0-a62f-c45a14c08482" TYPE="swap" [/color]
/dev/sda6: LABEL="DATA" UUID="3ad091a1-5036-463b-ba4e-88e98e41b07a" TYPE="ext4" 
/dev/sda7: LABEL="LUBU1204" UUID="4e6cd96d-49bd-47f0-9dfe-8eeebad4cf9d" TYPE="ext4" 
/dev/sda8: LABEL="1304mvar" UUID="136af805-5758-4880-acc4-0e1d35e2c266" TYPE="ext4" 
/dev/sdb1: LABEL="my_stuff" UUID="6a24777c-8191-4230-81f1-376f31b321e5" TYPE="ext4" 
/dev/sdc1: LABEL="ubie1204" UUID="5bae8c40-b15d-42f8-9fc9-0cf087f338d4" TYPE="ext4" 
sysop@1304mini:~$ 

```A shared swap between 3 installs.

[INDENT][INDENT]piece of cake
[/INDENT][/INDENT]

---

### Post by ptrakk on 2013-11-23
gparted makes it very simple for creating the swap partitions. use the above method to auto swapon at boot.

---

