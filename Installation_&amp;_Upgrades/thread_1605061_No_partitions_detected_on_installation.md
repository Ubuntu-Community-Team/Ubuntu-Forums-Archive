---
title: "No partitions detected on installation"
date: 2010-10-24
forum: Installation &amp; Upgrades
---

### Post by Cezzare on 2010-10-24
Hi! Currently I'm a user of Ubuntu 10.04 (gnome) but I wanted to install Xubuntu 10.10. I have win XP and Ubuntu 10.04 in my 80GB hard drive. Ok, so, I booted from the livecd, no problems there, then in the part of the installation process when the disc gives the option to manually configure the partitions, the disc didn't recognize any partition and only showed the whole drive with no partitions in it, when I already had two systems installed. As a curious fact I tried to see the partition table with Gparted in the live cd and couldn't find any partition either. After that I logged in my ubuntu 10.04 and ran fdisk, I have the following output:

```

Disco /dev/sda: 80.0 GB, 80026361856 bytes
255 cabezas, 63 sectores/pista, 9729 cilindros
Unidades = cilindros de 16065 * 512 = 8225280 bytes
Tamaño de sector (lógico / físico): 512 bytes / 512 bytes
Tamaño E/S (mínimo/óptimo): 512 bytes / 512 bytes
Identificador de disco: 0xcd56d451

Dispositivo Inicio    Comienzo      Fin      Bloques  Id  Sistema
/dev/sda1   *           1        7116    57159238+   7  HPFS/NTFS
/dev/sda2            7117        9729    20988513+   5  Extendida
/dev/sda5            7117        9548    19532800   83  Linux
/dev/sda6            9548        9730     1457152   82  Linux swap / Solaris
cezzare@cezzare-laptop:~$ 


```

In the live cd the only thing I could see was the /dev/sda unit but not the partitons. Back in ubuntu, I installed gparted and I still couldn't see any partition, but from the file manager I can access and edit them normally. I also recall this happening a few days ago when I tried to install ubuntu 10.10 (gnome) from a live cd in a friend's laptop with win 7 on it, the problem as exactly the same: No partitions listed, and that time I thought it was probably that either the live cd or the laptop's hard drive were damaged, but now I'm having that issue myself, so I don't know if there's a workaround for this. Also I don't want to simply install xfce and choose at boot, right now I need a fresh installation. However thank you so much for your time I hope somebody can help me a bit with that, If there's any additional info you might need just ask me, thanks again in advance : D

---

### Post by oldfred on 2010-10-24
Awhile back I used gparted and it took forever and then did not even see my sda drive which has XP. My XP seemed to boot ok, but I ran chkdsk anyway and then gparted saw the sda drive without any issue.

I would try runing windows chkdsk on the NTFS partition. And rerun until there are no errors, it does not fix everything in one pass.

XP CHKDSK info:
The chkdsk command checks the specified drive and repairs or recovers the drive if the drive requires it. The command also marks any bad sectors and it recovers readable information.
chkdsk drive: /p /r
chkdsk c: /r
You can use the following options:
/p Does an exhaustive check of the drive and corrects any errors.
/r Locates bad sectors and recovers readable information.
[http://www.microsoft.com/resources/documentation/windows/xp/all/proddocs/en-us/chkdsk.mspx?mfr=true](http://www.microsoft.com/resources/documentation/windows/xp/all/proddocs/en-us/chkdsk.mspx?mfr=true)
[http://support.microsoft.com/kb/927392](http://support.microsoft.com/kb/927392)

---

### Post by srs5694 on 2010-10-24
Please post the output of "sudo fdisk -lu". Also, please post it between a [noparse]```
[/noparse] string and a [noparse]
```[/noparse] string; this will preserve the columnar output of the utility, making it easier to read. Note that the -u option is important, since that changes the units from the imprecise cylinder values to more precise sector values.

---

### Post by psusi on 2010-10-25
Your swap partition extends beyond the end of the extended partition that contains it, and the entire disk.  Use fdisk to delete it.

---

### Post by srs5694 on 2010-10-25
> **psusi said:**
> Your swap partition extends beyond the end of the extended partition that contains it, and the entire disk.  Use fdisk to delete it.

I recommend checking the output with "sudo fdisk -lu" first. With only cylinder precision, it's hard to be sure if that's a real problem or just a difference in how the end cylinder value is rounded for logical vs. extended partitions.

---

### Post by Cezzare on 2010-10-27
Thanks to everyone! Late that same night I ran a disk analysis from XP with a partition managing application, and repaired disc errors. The analysis threw some results, among these it was that the linux ext3 partition was a logic partition. Now this was something even I didn't know, cause I remember configuring that partition as a primary one back six months ago when I installed 10.04.

Suposedly the disc errors were repaired but I still couldn't see the partitions with the live cd nor Gparted. Digging a bit deeper in the forum threads, I found that Gparted tended to have problems recognzing logic partitions, and that there are some requirements that a partition needs to met in order to be recognized at the installation time. What I ended up doing was deleting the swap and linux partitons from XP with a partitioning program. After that I attempted to install xubuntu again, and this time the application recognized properly the ntfs partition and the unallocated disk space, allowing me to install xubuntu along with XP. 

However after reinstalling I ran fdisk -l:

```

Disco /dev/sda: 80.0 GB, 80026361856 bytes
255 cabezas, 63 sectores/pista, 9729 cilindros
Unidades = cilindros de 16065 * 512 = 8225280 bytes
Tamaño de sector (lógico / físico): 512 bytes / 512 bytes
Tamaño E/S (mínimo/óptimo): 512 bytes / 512 bytes
Identificador de disco: 0xcd56d451

Dispositivo Inicio    Comienzo      Fin      Bloques  Id  Sistema
/dev/sda1   *           1        7116    57159238+   7  HPFS/NTFS
/dev/sda2            7117        9548    19530752   83  Linux
/dev/sda3            9548        9730     1459201    5  Extendida
/dev/sda5            9548        9730     1459200   82  Linux swap / Solaris

```

and fdisk -lu

```

Disco /dev/sda: 80.0 GB, 80026361856 bytes
255 cabezas, 63 sectores/pista, 9729 cilindros, 156301488 sectores en total
Unidades = sectores de 1 * 512 = 512 bytes
Tamaño de sector (lógico / físico): 512 bytes / 512 bytes
Tamaño E/S (mínimo/óptimo): 512 bytes / 512 bytes
Identificador de disco: 0xcd56d451

Dispositivo Inicio    Comienzo      Fin      Bloques  Id  Sistema
/dev/sda1   *          63   114318539    57159238+   7  HPFS/NTFS
/dev/sda2       114319360   153380863    19530752   83  Linux
/dev/sda3       153382910   156301311     1459201    5  Extendida
/dev/sda5       153382912   156301311     1459200   82  Linux swap / Solaris

```

This time at installing I checked not to put the linux partiton as a logic one and ran again gparted, this time it recognized all partitions without problems. I'm not quite sure why is that. My only clue was the logic partion thing, but is a bit too vague to take it as an explanation. 

Again thanks to everyone!

---

### Post by srs5694 on 2010-10-27
It's impossible to tell now what happened, but given your description, if I had to place a bet, I'd put it on the swap partition extending beyond the end of the extended partition, as psusi suggests. (As I wrote in my earlier post, the use of cylinder numbering obscures things a bit, but it's a likely cause and your actions would have fixed it.)

Linux is happy on either a primary or an extended partition, so its status as either of those was certainly *not* the cause of your problem.

---

