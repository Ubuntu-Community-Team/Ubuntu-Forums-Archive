---
title: "no default or UI configuration directive found"
date: 2010-09-27
forum: Installation &amp; Upgrades
---

### Post by craag1 on 2010-09-27
Last week, I made the mistake of trying to update Ubuntu without my netbook being plugged in, and it ran out of power half way through the update and now my computer wont boot.

So now I'm trying to reinstall Ubuntu. I made the flash drive, formatted it to FAT32 or whatever, and set my BIOS to boot off of USB. 

But shortly after turning my computer on it gives me the error, "no default or UI configuration directive found."

The flash drive is made by Kingston. 

My netbook is [http://www.officedepot.com/a/products/241804/HP-Mini-110-1012NR-XP-Edition/](http://www.officedepot.com/a/products/241804/HP-Mini-110-1012NR-XP-Edition/)

Thanks in advance for any help :)

EDIT: I found the answer in this thread: [http://ubuntuforums.org/showthread.php?t=1487937&highlight=default+ui+configuration](http://ubuntuforums.org/showthread.php?t=1487937&highlight=default+ui+configuration)

I just had to rename a folder on the flash drive.

---

### Post by magicfab on 2010-11-27
I worked around this by formatting to FAT16 and using a 1GB partition to create my bootable USB key.

---

### Post by khurtsiya on 2011-02-27
so if I have 4GB flash - no chance to figure this out?

---

### Post by megamasha on 2011-08-01
I used a 2GB FAT partition and it worked. Though I did partition it using Windows. I'm not sure it works if you format it with Linux.

---

### Post by polipantev on 2012-02-28
Guys i am really totally lost so please help really done evrything i saw here but nothing made things work.First of all i do not know if the problem isn't in the Universall USB installer because i downloaded it then downloaded the version Ubuntu 11.10 and installed it on a USB stick which i formatted to FAT file system!!!Then i get the message when i boot from the same USB mentioned "no default or UI configuration directive found" and when i read about renaming files on the USBdir i opened those files and for example in isolinux/syslinux i found nothing guys...I am totally lost and really hate it when i feel like noob so please help!!!Thank you in advance!

BTW i am trying to run it on a Compaq Mini 110c-1110EQ


Microprocessor 	1.60 GHz Intel Atom processor N270
Microprocessor Cache 	512 MB Level 2 cache
Memory 	1024 MB (1 x 1024 MB)
Memory Max 	Up to 1 GB DDR2
Video Graphics 	Intel GMA950
Video Memory 	Up to 128 MB
Hard Drive 	160 GB (5400 rpm)
Display 	10.1” Diagonal SD LED Anti-glare Widescreen Display (1024 x 576)
Network Card 	Integrated 10/100 Ethernet LAN

---

### Post by shexixi on 2012-03-03
Hello guys ! The thread is tagged SOLVED but i really dont get it! i have the same problem and i cant fix it! i am new at ubuntu and i will like to learn ubuntu,so please help me! I 've done FAT,FAT16,FAT32 disk format with no result.i also renamed isolinux files with syslinux but no result again!

---

### Post by SuporteTecnicoID on 2012-10-29
> **shexixi said:**
> Hello guys ! The thread is tagged SOLVED but i really dont get it! i have the same problem and i cant fix it! i am new at ubuntu and i will like to learn ubuntu,so please help me! I 've done FAT,FAT16,FAT32 disk format with no result.i also renamed isolinux files with syslinux but no result again!

Estranho, eu to usando o KDu Linux e ele esta rodando bem pelo Pendrive e não apresenta esta falha, no0 entanto quando vou tentar rodar ele pela Maquina virtual , ai sim surge esta mesma informação....

Ainda não sei o que pode ser, talves algo relativo ao Syslinux, vamos ver.....

---

