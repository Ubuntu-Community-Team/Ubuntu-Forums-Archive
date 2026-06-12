---
title: "Hard disk seen as empty (no partitions)"
date: 2008-03-30
forum: Installation &amp; Upgrades
---

### Post by abelthorne on 2008-03-30
Hello,
In november, I bought a Dell laptop (XPS M1330). It came with Windows Vista preinstalled, which I wanted to keep, and some Dell partitions (Recovery, Media center or such).
I resized the Windows partition (from inside Vista) to get space for Ubuntu, ran the LiveCD, created partitions in the available space and installed it without problem.

A few weeks ago, I've started to experience really bad performance issues with Ubuntu. Being unable to find the source of the problem and the OS being quite unusable in that state, I want to reinstall Gutsy from scratch and see if it fixes this behaviour.

Problem: I discovered about two days ago that GParted cannot see my partitions anymore (it sees unpartitioned space of 120 Gb - that's the hard disk size) : no FAT (Dell) / NTFS (Vista) / Ext3+swap (Ubuntu).
I've just tried to install the newest version of GParted I could find (0.3.6, from the official website) with no change.

If I run **fdisk -l** as root, it sees the partitons:
```
Disque /dev/sda: 120.0 Go, 120034123776 octets
255 heads, 63 sectors/track, 14593 cylinders
Units = cylindres of 16065 * 512 = 8225280 bytes
Disk identifier: 0x10000000

Périphérique Amorce    Début         Fin      Blocs    Id  Système
/dev/sda1   *       14267       14594     2620416    c  W95 FAT32 (LBA)
/dev/sda2              15        1320    10485760    7  HPFS/NTFS
/dev/sda3   *        1320        8228    55485440    7  HPFS/NTFS
/dev/sda4            8229       14594    51127887+   f  W95 Etendu (LBA)
/dev/sda5           14267       14594     2620416   dd  Inconnu
/dev/sda6   *        8229       14014    46476013+  83  Linux
/dev/sda7           14015       14266     2024158+  82  Linux swap / Solaris

Les entrées de la table de partitions ne sont pas dans l'ordre du disque
```

**(English version might be something like: *The partitions table entries are not in the disk order*.)**

And if I try **fdisk /dev/sda6**, I get a warning:
```
Le périphérique ne contient ni une partition ni une étiquette DOS, Sun, SGI ou OSF
Building a new DOS disklabel with disk identifier 0x015e7294.
Changes will remain in memory only, until you decide to write them.
After that, of course, the previous content won't be recoverable.

Le nombre de cylindres pour ce disque est initialisé à 5785.
Il n'y a rien d''incorrect avec cela, mais c'est plus grand que 1024,
et cela pourrait causer des problèmes en fonction pour certaines configurations:
1) logiciels qui sont exécutés à l'amorçage (i.e., vieilles versions de LILO)
2) logiciels d'amorçage et de partitionnement pour d'autres SE
   (i.e., DOS FDISK, OS/2 FDISK)
AVERTISSEMENT: fanion 0x0000 invalide de la table de partitions 4 sera corrigé par w(écriture)
```

[b](English would be: [i]The device contains no partition nor a DOS, Sun, SGI or OSF label/tag
[...]
The number of cylinders for this disk has been set to 5785. This is not an issue but it is greater than 1024 ans this could lead to problems with some configurations:
1) boot softwares (such as old LILO versions)
2) boot and partitioning softwares for other OS (DOS FDISK, OS/2 FDISK)
WARNING: invalid flag 0x0000 of partition table nb. 4 will be fixed with w(rite)[/i].)[/b]

Are these usual warnings from FDisk or is there a problem with my hard disk?
How do I reinstall Ubuntu (remove/recreate Ext3 partitions) without losing the other ones (Dell + Windows) ? of course, the LiveCD installer partition tool sees my whole hard disk as unpartitioned in the same way that GParted on my current system.

---

### Post by Pumalite on 2008-03-30
Use TestDisk to test your drive and maybe fix your partition table: 
[http://www.cgsecurity.org/wiki/TestDisk_Download](http://www.cgsecurity.org/wiki/TestDisk_Download)

---

### Post by abelthorne on 2008-03-30
Just done that and it finds a conflict between two partitions (they seem to overlap, although I don't understand how it is possible). Problem is it wants to remove one of the Dell Partitions...

---

### Post by Pumalite on 2008-03-30
Your Partition Table is messed up.

---

### Post by abelthorne on 2008-03-30
Ok, but it there a way to fix this without losing the Dell and Windows partitions? i.e. forcing to remove the Linux partitions as I want to remove them anyway?

It seems I can remove the partitions I want with testdisk, but I have access to the list only after it has removed the first Dell partition from it. So I guess that if I delete the Linux partitions and write the changes to disk, it will remove the Dell partition I'd like to keep.

---

### Post by Pumalite on 2008-03-30
Post:
sudo fdisk -lu

---

### Post by abelthorne on 2008-03-30
```
Disque /dev/sda: 120.0 Go, 120034123776 octets
255 heads, 63 sectors/track, 14593 cylinders, total 234441648 secteurs
Units = secteurs of 1 * 512 = 512 bytes
Disk identifier: 0x10000000

Périphérique Amorce    Début         Fin      Blocs    Id  Système
/dev/sda1   *   229197824   234438655     2620416    c  W95 FAT32 (LBA)
/dev/sda2          225280    21196799    10485760    7  HPFS/NTFS
/dev/sda3   *    21196800   132167679    55485440    7  HPFS/NTFS
/dev/sda4       132182881   234438655    51127887+   f  W95 Etendu (LBA)
/dev/sda5       229197824   234438655     2620416   dd  Inconnu
/dev/sda6   *   132182883   225134909    46476013+  83  Linux
/dev/sda7       225134973   229183289     2024158+  82  Linux swap / Solaris

Les entrées de la table de partitions ne sont pas dans l'ordre du disque
```

Testdisk sees a space conflict between partitions 1and 4 and wants to delete partition 1.

---

### Post by Pumalite on 2008-03-30
I think it's between 1 and 5 'inconnu'. Delete 5 with Gparted Live CD: 
[http://gparted.sourceforge.net/download.php](http://gparted.sourceforge.net/download.php)
Then check again with TestDisk.

---

### Post by abelthorne on 2008-03-30
As I said above, GParted 0.3.6 is unable to see any partition. Do you think the LiveCD will be able to (I guess it's the same version) ?

---

### Post by Pumalite on 2008-03-30
Try the latest version first. If that doesn't work, try version 0.3.4-0.iso

---

### Post by abelthorne on 2008-03-30
Well, same problem with 0.3.4.11 (latest LiveCD) : unallocated space on the whold disk.
0.3.4.0 can't start X (I think it doesn't recognize my laptop video modes), thus I couldn't check GParted.

I guess I'll have to ditch this seemingly faulty partition.

---

### Post by Pumalite on 2008-03-30
RescueCD has a partitioner. Give it a try:
[http://www.sysresccd.org/Download](http://www.sysresccd.org/Download)

---

### Post by louieb on 2008-03-30
It looks like sda1 is at the end of the disk and it extends beyond the end of the drive.  fdisk reports the drive has 14593 cylinders and sda1 ends in 14594.  
fdisk also shows extended partition sda4 and the logical partition sda5 end after sda1 begins.  
In fact it shows primary partition sda1 completely inside extended partition  sda4.
Also fdisk shows sda5 and sda1 occupy the same space on disk.   

GParted sees that and says I don't know and won't display anything.   

Have you tried Mandriva or PCLinuxOS Linux?  They uses a partitioner called Disk Drake.   Disk Drake can do that type of weird partition table  editing.  

[IMG]http://louboldt.com/ptwocents.gif[/IMG] GParted is not going to work with that drive and Ubuntu won't install on it.  Might give Disk Drake a try.  or you might let testdisk go ahead and deleted the partition. 
The only other option is to use fdisk  [Partitioning with fdisk]("http://tldp.org/HOWTO/Partition/fdisk_partitioning.html")- be very carefull. In fact I would not mess with partitions until I had a full drive backup.

Good reading here too from [COLOR=navy]bodhi.[/COLOR][COLOR=darkgray]zazen[/COLOR] :[HowTo: Partitioning Basics - Ubuntu Forums]("http://www.ubuntuforums.org/showthread.php?&t=282018")

---

### Post by abelthorne on 2008-03-31
> **louieb said:**
> It looks like sda1 is at the end of the disk and it extends beyond the end of the drive.  fdisk reports the drive has 14593 cylinders and sda1 ends in 14594.  
fdisk also shows extended partition sda4 and the logical partition sda5 end after sda1 begins.  
In fact it shows primary partition sda1 completely inside extended partition  sda4.
Also fdisk shows sda5 and sda1 occupy the same space on disk.
Any idea how this happened (the partition table was ok a few weeks ago) ? Ubuntu hard disk check ? Vista screwing the table ?

> GParted sees that and says I don't know and won't display anything.
Ok.

> Have you tried Mandriva or PCLinuxOS Linux?  They uses a partitioner called Disk Drake.   Disk Drake can do that type of weird partition table  editing.
I'll give a try to Mandriva.

> [IMG]http://louboldt.com/ptwocents.gif[/IMG] GParted is not going to work with that drive and Ubuntu won't install on it.  Might give Disk Drake a try.  or you might let testdisk go ahead and deleted the partition. 
The only other option is to use fdisk  [Partitioning with fdisk]("http://tldp.org/HOWTO/Partition/fdisk_partitioning.html")- be very carefull. In fact I would not mess with partitions until I had a full drive backup.
I have a backup of my data. The thing that makes me hesitate is that I'm not sure how I can get my original partitioning back with the CDs that came with the laptop.

> Good reading here too from [COLOR=navy]bodhi.[/COLOR][COLOR=darkgray]zazen[/COLOR] :[HowTo: Partitioning Basics - Ubuntu Forums]("http://www.ubuntuforums.org/showthread.php?&t=282018")
Thanks. I'll look at that.

---

### Post by louieb on 2008-03-31
Interesting . Haven't seen a fdisk quite like that.  As for how it could happen:confused: not sure but have see Disk Drake put a primary partition inside an extended one. Thats why I wondered if you has Mandriva or PCLinuxOS installed in the past.  

I suppose you could use partimage or the dd command to take a image backup of your partitions and once  you have rebuilt the partition table restore from the image backup. Don't have a Dell so haven't looked at how thier recover partition is set up. May have to use there technical support.  

on question though. 
```
/dev/sda5       229197824   234438655     2620416   dd [COLOR=Red] Inconnu[/COLOR]
/dev/sda1   *   229197824   234438655     2620416    c  W95 FAT32 (LBA)
```What does Inconnu mean (I guess it french for something)?

---

### Post by Pumalite on 2008-03-31
Unknown

---

### Post by abelthorne on 2008-03-31
Well, I've tried MandrivaOne this morning and was unable to find disk drake in the distro (and I didn't manage to setup my wi-fi internet connexion to see if it was in a repository).

Finally, I reformated the whole disk, managed to restore the Dell partitions and reinstalled Windows (which gave me more space than before because that Vista thing was not installed using all disk space this time). Then I reinstalled Ubuntu and I'm currently restoring my data from my backup.

GParted now sees my partitions as expected. I wonder what put the primary partition in an extended one at first. I hope it was not the installation of Vista SP1 (as I'll have to reinstall it next time I boot up Windows and I won't be happy if it starts again).

Anyway, the problem is (currently) no more.

---

