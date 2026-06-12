---
title: "thunderbird local folder"
date: 2007-03-28
forum: Installation &amp; Upgrades
---

### Post by kelmer on 2007-03-28
Hi everyone,
I am planning to upgrade my Dapper to Feisty (yes I resisted skiping one version:) ). Although I have my home partition in a separate partition,  I have important local folders of my thunderbird mail client on it. My question is: When I reinstall thunderbird, will it try to overwrite these folders ??? should I back up this mails somewhere, or is not necessary ?  thanks in advance.

---

### Post by Rui Pais on 2007-03-28
backup is always a good idea. 
But installing a new version should not overwrite your personal thunderbird folders anyway.

---

### Post by yoda29 on 2007-03-28
I had a problem when i upgraded to feisty. I have a shared partition (fat32) to share the definition of Firefox and Thunderbird. When i updated to feisty the partition was gone and Firefox and Thunderbird dont start anymore.

Solutions????

---

### Post by Rui Pais on 2007-03-28
> **yoda29 said:**
> I had a problem when i upgraded to feisty. I have a shared partition (fat32) to share the definition of Firefox and Thunderbird. When i updated to feisty the partition was gone and Firefox and Thunderbird dont start anymore.

Solutions????

why a share folder with fat32? do you share the firefox and thunderbird folders between windows and linux? That wasn't a little dangerous?... even if they have the same version numbers they belong to very different architectures... like, e.g., both save paths on config files, but paths are very different between the 2 systems and in some cases incompatible (fat32 isn't case sensitive...)


anyway, what do you mean by "was gone"?
Did feisty install remove the partition (occupying the space)? or deleted the contents? or simply fail on mount it?

---

### Post by yoda29 on 2007-03-29
> **Rui Pais said:**
> why a share folder with fat32? do you share the firefox and thunderbird folders between windows and linux? That wasn't a little dangerous?... even if they have the same version numbers they belong to very different architectures... like, e.g., both save paths on config files, but paths are very different between the 2 systems and in some cases incompatible (fat32 isn't case sensitive...)


anyway, what do you mean by "was gone"?
Did feisty install remove the partition (occupying the space)? or deleted the contents? or simply fail on mount it?

I'm new to this. I saw a tutorial on how to share Firefox and Thunderbird definitions files only. What happened when i upgrade to feisty was that it didn't mount the fat32 partition. I can see the Windows partition, but not that one.

---

### Post by Rui Pais on 2007-03-29
> **yoda29 said:**
> I'm new to this. I saw a tutorial on how to share Firefox and Thunderbird definitions files only. What happened when i upgrade to feisty was that it didn't mount the fat32 partition. I can see the Windows partition, but not that one.

So, you just forget to specified the mount point for the shared partition.
You simply need to edit the file /etc/fstab and edit... but you must give more information so i can tell you what you put there.

First do you know what it's the partition number, not the window notation (c:,d:) but the linux notation, something like /dev/hda2 or /dev/sda3)?

If you don't know post the output of:
```
sudo fdisk -l /dev/hda
```
or if your disks are SATA:
```
sudo fdisk -l /dev/sda
```
assuming that you have only one disk. 
Copy past the commands to a terminal to avoid typos, if you are not comfortable with those (note it's -l not -1).


post too what the output of:
```
ls -l .mozilla/firefox
```
and
```
ls -l .mozilla-thunderbird
```

---

### Post by yoda29 on 2007-03-30
Hello here comes the reply.... Hope you can help me..

```

yoda@yoda-laptop:~$ sudo fdisk -l /dev/hda
Password:
yoda@yoda-laptop:~$ sudo fdisk -l /dev/sda

Disco /dev/sda: 120.0 GB, 120034123776 bytes
255 cabeças, 63 setores/trilha, 14593 cilindros
Unidades = cilindros de 16065 * 512 = 8225280 bytes

Dispositivo Boot Início Fim Blocos Id Sistema
/dev/sda1   *           1        6374    51199123+   7  HPFS ou NTFS
/dev/sda2            6375       12735    51094732+   f  Win95 (LBA) Partição Ext                           endida
/dev/sda3           12736       12936     1614532+   c  W95 FAT32 (LBA)
/dev/sda5            6375       12603    50034411   83  Linux
/dev/sda6           12604       12735     1060258+  82  Linux swap / Solaris
yoda@yoda-laptop:~$ ls -l .mozilla/firefox
total 29
-rw------- 1 yoda yoda 15352 2007-03-20 09:13 pluginreg.dat
-rw-r--r-- 1 yoda yoda   122 2007-01-16 00:28 profiles.ini
-rw-r--r-- 1 yoda yoda   121 2007-01-16 00:08 profiles.ini~
-rw-r--r-- 1 yoda yoda    94 2007-01-15 22:32 profiles.ini~1
drwx------ 7 yoda yoda  1136 2007-01-16 00:26 t1hilfgv.default
yoda@yoda-laptop:~$ ls -l .mozilla-thunderbird
total 13
-rw-r--r-- 1 yoda yoda 335 2007-01-15 22:42 appreg
drwx------ 4 yoda yoda 560 2007-01-15 22:43 jqdyd0qi.default
-rw-r--r-- 1 yoda yoda 126 2007-01-15 22:43 profiles.ini
-rw-r--r-- 1 yoda yoda  94 2007-01-15 22:42 profiles.ini~
yoda@yoda-laptop:~$  

```


Best regards

---

### Post by yoda29 on 2007-03-30
Problem solved...

Just needed to edit the fstab.


Best regards.

---

### Post by Rui Pais on 2007-03-30
Hi,
sorry ,only now i could get to my computer...

But you managed to get it yourself. 
Good! Congratulations.

Have fun.

---

