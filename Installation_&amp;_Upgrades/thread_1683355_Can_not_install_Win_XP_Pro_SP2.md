---
title: "Can not install Win XP Pro SP2"
date: 2011-02-07
forum: Installation &amp; Upgrades
---

### Post by KrawieC on 2011-02-07
Hey

I would like to install Windows XP Pro SP2, but after the booting and line " Setup is inspecting your computer's hardware configuration..." noting happened. I thought that CD could be broken, but I've tried to install Win by VirtualBox, and it works.
Do you have any idea what i have to do?

Regards

---

### Post by ppv on 2011-02-07
Do you have Ubuntu already installed?

It is usually simpler to install windows first and then install Ubuntu after so. It will pick up your existing operating systems and configure the bootloader to provide with choices at startup.

---

### Post by KrawieC on 2011-02-07
Yes I have. Also I have configured separated partition for boot. So you propose to formate disk and then try to install?

---

### Post by Rubi1200 on 2011-02-07
I suggest you make backups of all important data before continuing.

Also, please post the output of the following command from the terminal on Ubuntu:

```
sudo parted -l
```

(lowercase L not 1)

Thanks.

---

### Post by KrawieC on 2011-02-07
```
Model: ATA ST3160212ACE (scsi)
Dysk /dev/sda: 160GB
Rozmiar sektora (logiczny/fizyczny): 512B/512B
Tablica partycji: msdos

Numer  Pocz&#261;tek  Koniec  Rozmiar  Typ       System plików   Flaga
 1     32,3kB    82,3MB  82,2MB   primary   ext3            &#322;adowalna
 3     82,3MB    14,0GB  14,0GB   primary   ntfs
 2     14,0GB    160GB   146GB    extended                  lba
 5     14,0GB    148GB   134GB    logical   ntfs            &#322;adowalna
 6     148GB     159GB   11,2GB   logical   ext3
 7     159GB     160GB   543MB    logical   linux-swap(v1)

```

---

### Post by ppv on 2011-02-07
If your Ubuntu is a fresh install or you are ok with reinstalling it, then you might want to do the following. (These steps will wipe your entire disk so backup the data that you want)

- Backup all data.
- Delete all existing partitions. To do this you can use a live CD of gparted or even an ubuntu live cd.
- Boot your computer with windows xp's cd.
- When it comes to the partitioning just create one single partition for windows xp of the desired size and let the remaining space be as is.
- Install windows xp on the new partition
- Using ubuntu's cd install ubuntu. Choose the options of using the remaining free space for partitions and install Ubuntu side-by-side with another operating system when asked.

This way you will have a dual boot system with grub bootloader and options to choose an OS at boot.

---

### Post by Rubi1200 on 2011-02-07
Did you create the 14GB partition to install Windows and create the NTFS file-system with GParted?

I have seen where Windows does not like it when the file-system is created by Linux tools.

Therefore, try this first (after backing up as ppv wisely suggested); go back to that partition and mark it as unallocated (delete it and leave it as free space), then try the Windows disk again and point it to that partition when installing.

---

