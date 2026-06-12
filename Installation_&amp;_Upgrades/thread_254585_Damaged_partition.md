---
title: "Damaged partition"
date: 2006-09-10
forum: Installation &amp; Upgrades
---

### Post by skaboss on 2006-09-10
Hello,

I tried today to gain some space on my second hard drive, which used to contain my old Debian install.
So i formatted the / and var partitions, and of course left /home, which contains data i want to keep.
Did it with qtParted. The problem is i can't access the data on this drive anymore.

```

sudo mount /dev/hdb6 /media/debian -t ext3
mount: type erroné de système de fichiers, option erronée, super bloc erroné sur /dev/hdb6,
       codepage manquante ou autre erreur
       Dans quelques cas certaines informations sont utiles dans syslog - essayez
       dmesg | tail  ou quelque chose du genre

```
Sorry, it's in french, but means something like wrong system file, bad super block...

Here is what fdisk -l says : 
```

Disque /dev/hdb: 60.0 Go, 60022480896 octets
255 têtes, 63 secteurs/piste, 7297 cylindres
Unités = cylindres de 16065 * 512 = 8225280 octets

Périphérique Amorce    Début         Fin      Blocs    Id  Système
/dev/hdb1   *           1          34      273073+  83  Linux
/dev/hdb2              35        7297    58340047+   f  W95 Etendu (LBA)
/dev/hdb5            1245        7297    48620691   83  Linux
/dev/hdb6              35        1244     9719262   83  Linux

Les entrées de la table de partitions ne sont pas dans l'ordre du disque


```

The partition  i need to mount (/dev/hdb6) have always been ext3...
Can somebody help me please, i would like so much to get my data back !!

---

### Post by lukew on 2006-09-10
I wrote this howto on scanning vfat paritions. I am sure you can adapt this for ext3. I have never had any reason to check ext3, always solid as a rock.

[http://www.ubuntuforums.org/showthread.php?t=253621](http://www.ubuntuforums.org/showthread.php?t=253621)

I hope this helps.

Luke

---

### Post by skaboss on 2006-09-10
Thank you for the answer.
I already ran fsck on the infamous partition, and only got error message

```
fsck.ext3: Bad magic number in super-block lors de la tentative d'ouverture de /dev/hdb6

```

Sorry, it's still french, and means "Bad magic number in super-block while trying to open /dev/hdb6".

---

### Post by Mellon on 2006-09-12
i have the same problem but with other partition 

heres what i  get when i type "sudo mount -a"

> edwin@edwin-desktop:~$ sudo mount -a
Password:
mount: tipo de sistema de ficheros incorrecto, opción incorrecta,
       superbloque incorrecto en /dev/hdc1, falta la página de códigos,
       o algún otro error
       En algunos casos se encuentra información en syslog, pruebe
   dmesg | tail   o algo parecido


](*,)

---

### Post by Mellon on 2006-09-12
i just realease that it happents when ubuntu start, it say that gona scan my hard disk becouse it was mounted 30 times without check, it found some errors and tell me to scan manual, with a command i dont remember, now i can see a partition in ext2 when it used to be in ext3 so i cant see any files on there.

is there a way to reformat the partition without lost insformation couse with  gparted it say im gonna lost everything.

sorry for my english jejeje

and for the double post too ;)

---

### Post by Mellon on 2006-09-12
i fix my problem,

to solved i just change my fstab file,

instead of mount an ext3 partition i mounted an ext2 and thats all, i can read and write now.=D>

---

### Post by skaboss on 2006-09-13
I'm happy you solved your problem, but unfortunately, that doesn't work for me : i tried mount -t ext2, to mount my partition as ext2, but still have the same error message...

---

