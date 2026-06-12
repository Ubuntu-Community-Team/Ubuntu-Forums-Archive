---
title: "No Windows option in boot menu"
date: 2012-03-24
forum: Installation &amp; Upgrades
---

### Post by erimen on 2012-03-24
salut à toutes et a tous, 
j'ai un petit problème aujourd'hui j'ai décidé d'installer Ubuntu.  je l'ai installé à partir du CD officiel 10.04. le problème c'est qu'il  boot directement sur ubuntu et il ne me propose rien dutout au démarrage  ... j'ai voulu utiliser easyBCD pour le configurer j'ai donc installé  wine mais il ne veut pas me lancer easyBCD ... ducoup je fais appel a  vous car je n'y connais pas grand chose à linux :/ pardonnez mon  intolérable ignorance dans ce domaine :) 

merci d'avance pour votre aide qui j'espère ... m'aidera :D 
cordialement

erimen

(resume in english: i have windows seven and now ubuntu 10.04. but, on start, i don't have the choice of the OS, it start on ubuntu. help me please, my english is not very good sorry :s)

---

### Post by Elfy on 2012-03-24
Good day to you.

While I understand that you are not so good in English - this is an English forum so please use English - we will understand what you are saying :)

If you really prefer to use French then perhaps you'd be better using one of the other support options - one of which is a French speaking forum - [http://forum.ubuntu-fr.org/](http://forum.ubuntu-fr.org/)

[http://www.ubuntu.com/support/community/locallanguage#french](http://www.ubuntu.com/support/community/locallanguage#french)

In the meantime perhaps you could go here and follow the instructions - this will show us exactly what state your boot and partitions are in 

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

---

### Post by erimen on 2012-03-24
ok thanks. it is de content of results.txt :

  ```
                Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Grub2 (v1.97-1.98) is installed in the MBR of /dev/sda and looks at sector 
    1 of the same hard drive for core.img. core.img is at this location and 
    looks in partition 4 for /boot/grub.

sda1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disque /dev/sda: 320.1 Go, 320072933376 octets
255 têtes, 63 secteurs/piste, 38913 cylindres, total 625142448 secteurs
Unités = secteurs de 1 * 512 = 512 octets
Sector size (logical/physical): 512 bytes / 4096 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *          2,048       206,847       204,800   7 NTFS / exFAT / HPFS
/dev/sda2             206,848   206,850,047   206,643,200   7 NTFS / exFAT / HPFS
/dev/sda3         206,850,048   595,845,119   388,995,072   7 NTFS / exFAT / HPFS
/dev/sda4         595,845,120   625,141,759    29,296,640  83 Linux


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/sda1        90A0D860A0D84E7A                       ntfs       Réservé au système
/dev/sda2        E236EBFD36EBD099                       ntfs       Win7
/dev/sda3        9698809F98807F8B                       ntfs       Documents
/dev/sda4        8a034680-c4ce-47dd-88eb-b55ff0956cd5   ext4       

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/sda1        /tmp/BootInfo0/sda1      fuseblk    (ro,nosuid,nodev,allow_other,blksize=4096)
/dev/sda4        /                        ext4       (rw,errors=remount-ro)


========================== sda1/grldr embedded menu: ===========================

--------------------------------------------------------------------------------

=============================== StdErr Messages: ===============================

/home/erimen/Documents/boot_info_script.sh: line 1888: (  / 2 ) + 16 : erreur de syntaxe : opérande attendue (error token is "/ 2 ) + 16 ")
```

it's good ?
thanks

---

### Post by Elfy on 2012-03-24
> Please use code tags - if you are using New Reply button - highlight text and use the # button in the text box header. 
 
If using Quick Reply then [noparse]```
[/noparse] at the beginning and [noparse]
```[/noparse] at the end.


I think that looks ok.

When you're in ubuntu can you open a terminal and run 

```
sudo update-grub
```

It will ask for password - your normal password - it will NOT show as you type, this is normal.

Paste all that shows after you have run the command here please.

---

### Post by erimen on 2012-03-24
dat is the copy paste of your command :
```
erimen@erimen-linux:~$ sudo update-grub
[sudo] password for erimen: 
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-2.6.32-40-generic
Found initrd image: /boot/initrd.img-2.6.32-40-generic
Found linux image: /boot/vmlinuz-2.6.32-21-generic
Found initrd image: /boot/initrd.img-2.6.32-21-generic
Found memtest86+ image: /boot/memtest86+.bin
Found Windows 7 (loader) on /dev/sda1
done
erimen@erimen-linux:~$ 

```Dat is that ?

PS: i reboot for test

---

### Post by erimen on 2012-03-24
YEAH that run ! thanks you very mush ;)

---

### Post by Elfy on 2012-03-24
Welcome - and just so you know - you're English is fine and 100s of times better than my French :)

---

### Post by erimen on 2012-03-24
English is the internationnal language also :D (i don't use google translate and i have 1 year of english only ^^)

---

