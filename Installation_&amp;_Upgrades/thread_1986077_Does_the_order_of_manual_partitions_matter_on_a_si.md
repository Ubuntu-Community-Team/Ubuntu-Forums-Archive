---
title: "Does the order of manual partitions matter on a single OS PC?"
date: 2012-05-24
forum: Installation &amp; Upgrades
---

### Post by Rytron on 2012-05-24
Does the order of manual partitions matter on a single OS PC?

For example I think this was the order of my current install (is there a way to check?).
[I]sda3 /
sda5 swap
sda2 home[/I]

It would usually be like this example [attached image].

---

### Post by eleftg on 2012-05-24
No it doesn't matter. The number after sda is not consistent through all installations. The only way to check it, is to see the UUID of the partition by running ```
sudo blkid
```

---

### Post by 23dornot23d on 2012-05-24
Use gparted and post a screen shot of how you have set you drive up .....

sudo apt-get update
sudo apt-get install gparted

Just view the setup - do a screenshot and post it ...... with one OS there should be no real problem.

beat me to it .....

useful to know ...

> 
[keith2@keith-aspire-7730zg ~]$ sudo blkid
Password: 
/dev/sda1: LABEL="Expansion Drive" UUID="DCA427C3A4279F50" TYPE="ntfs" 
/dev/sda3: UUID="16ee20dc-9da2-4134-99d2-d4adc6af3fc8" TYPE="ext4" 
/dev/sda4: UUID="9766881a-6a10-4400-b39e-d93131c000b3" TYPE="ext4" 
/dev/sda5: UUID="d1948aaa-f505-4a23-a80a-46ee834737c7" TYPE="ext4" 
/dev/sda6: UUID="a86f532b-a9bb-4d52-8f9d-780cdbb42101" TYPE="swap" 
/dev/sda7: UUID="23119efb-1320-4995-a6f6-9e542aa75439" TYPE="ext4" 
/dev/sda8: UUID="d7551920-866c-4a8f-901d-808fe287b319" TYPE="ext4" 
/dev/sda9: UUID="c0fd6b8c-09d7-41a7-87c6-aab175aa8532" TYPE="swap" 
/dev/sda10: UUID="e2579a77-2bfe-4af3-8180-be0b8b242bbb" TYPE="ext4" 
/dev/sdb1: LABEL="Expansion Drive" UUID="984400C44400A6DA" TYPE="ntfs" 
/dev/sdb2: UUID="04c1dceb-f5e0-42b6-8e94-c5727f9230c0" TYPE="ext4" 
/dev/sdb5: UUID="78a08b27-9c4e-48a4-a4ed-24ec6f0e966a" TYPE="swap" 
/dev/sdb6: UUID="59f3313d-663c-4a68-a29f-b0c0690fabcd" TYPE="swap" 
/dev/sdb7: LABEL="oneirictron" UUID="bf53f9c4-89d2-4238-82a0-7de304e296ed" TYPE="ext4" 
/dev/sdb8: LABEL="Photos A1" UUID="3D6E-40CD" TYPE="vfat" 
/dev/sdb9: LABEL="Accounts Li" UUID="44F7-A759" TYPE="vfat" 
/dev/sdb10: LABEL="3D Complete" UUID="4BE3-A6FB" TYPE="vfat" 
/dev/sdb11: UUID="D0D9-6B14" TYPE="vfat" 
/dev/sdb12: UUID="e53e12d7-aedd-492c-9c11-c1ae3337b850" TYPE="ext4" 
/dev/sdb13: UUID="e0761f26-af5f-4ca9-aafe-1c5163673942" TYPE="ext4" 
/dev/sdb14: UUID="599f0caa-c774-4820-aed8-67bba7fbedba" TYPE="ext4" 
/dev/sdb15: LABEL="Photgarphic" UUID="2AB1-2122" TYPE="vfat" 
/dev/sdb16: UUID="0acb7a0c-a265-4a54-9316-3feaf505c02c" TYPE="ext4" 
/dev/sdb17: UUID="cb5e2789-a3b9-40bf-94b7-942cde4bfe07" TYPE="ext4" 
/dev/sdb18: UUID="4ecb0ef2-b641-4325-a19f-b3e4f01e4ddb" TYPE="ext4" 
/dev/sdb19: UUID="c547af6d-574a-4b05-818a-7f6fe4b279b6" TYPE="swap" 
/dev/sdb20: UUID="34d582ba-0bb1-46a0-848f-6984ceca4239" TYPE="ext4" 
/dev/sdb21: UUID="92201dd7-9cda-4406-8203-c0b05e82c2d4" TYPE="swap" 
/dev/sdc1: SEC_TYPE="msdos" TYPE="vfat" 
[keith2@keith-aspire-7730zg ~]$ 



or using 

sudo gparted

[IMG]http://img52.imageshack.us/img52/3382/seen60.jpg[/IMG]

---

### Post by kc1di on 2012-05-24
I don't believe it matters to linux but it does to windows. 

so you should be fine. 

:)

---

### Post by haqking on 2012-05-24
> **Rytron said:**
> Does the order of manual partitions matter on a single OS PC?

For example I think this was the order of my current install (is there a way to check?).
[I]sda3 /
sda5 swap
sda2 home[/I]

It would usually be like this example [attached image].

not really, though it is considered more prudent to place the /swap at the beginning of the drive, but depends on if swap is used much really.

Also the numbers after sda will depend on whether its a primary such as sda1, sda2 or if its logical in a extended such as sda5, sda6 etc.

Peace

---

