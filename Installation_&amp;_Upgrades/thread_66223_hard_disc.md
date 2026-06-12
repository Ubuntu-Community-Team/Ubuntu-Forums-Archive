---
title: "hard disc"
date: 2005-09-16
forum: Installation &amp; Upgrades
---

### Post by Jahmon on 2005-09-16
Hi,

I'm totally new to linux and i choose to start my linux experience with (k)Ubuntu.
I have 2 hard disks 
the 1st one is divided in 3 partitions 1 with windows and 2 with files
the 2nd is with linux divided in 2 i think ( i selected that linux could use the complete drive)

The installation was OK but now when i want to open my hard disk containing files i get :
```

Could not mount device.
The reported error was:
mount: ne peut repérer /dev/hda5 dans /etc/fstab ou /etc/mtab
```
(sorry it's a bit in french )

What can i do to be able to open it?
i tried opening /etc/fstab with "Kate"  and i saw hdaX weren't in the file but i dont seem to have write permission/acces...

can someone help me??
i've been searching for a while but since i'm totally new to linux i have some difficulties... i'm not stupid but linux isn't easy when you're totally new to it, specialle all those "root" acces super user etc ...


Thanks already for even reading me

---

### Post by angkor on 2005-09-16
Welcome to Ubuntu!

try:

sudo gedit /etc/fstab (you will be asked to enter your *user* password)

to edit the file.

Also read [http://www.ubuntuguide.org](http://www.ubuntuguide.org)

---

### Post by Jahmon on 2005-09-16
ok thank you but what do i have to write in this file in order to see my partitions...

---

### Post by Jahmon on 2005-09-16
i do :
run command -> options run in terminal window

i get :

sudo: gedit: command not found

---

### Post by bsussman on 2005-09-16
since you are using KDE, you can use kate to edit the file - substitute 'kate' for gedit' in the above.
 
 as far as the appropriate entry:
 
```
 /dev/hda5   /mnt/hda5     ext3	defaults,errors=remount-ro 0	 1
``` 

would be a good generic start.

you need to:

 ```
sudo mkdir /dev/hda5
``` 

if it does not exist already - this is the mount point

at the command line you can:


 ```
> mount /mnt/hda5
> cd /mnt/hda5
> ls
``` 

to prove it is all there.

you can mount anywhere so if you would rather have the disk at /home/you/otherdisk that is ok - just mkdir that and put it in the fstab file instead of /mnt/hda5

/mnt is where casually mounted volumes are supposed to go according to standards.

---

### Post by mlomker on 2005-09-16
You can open Kate with superuser permissions by typing **kdesu kate** on the Run Command line.

To find the partition number for your drive, open a Konsole terminal.

```

sudo fdisk -l

```

One of the listed partitions will be the drive that you can't see.  You'll need to create a directory for it, such as /mnt/newdrive and then add a line to that /etc/fstab file.

If you post the output from that fdisk command and your /etc/fstab then I could tell you the steps.

---

### Post by Jahmon on 2005-09-16
[QUOTE=bsussman]since you are using KDE, you can use kate to edit the file - substitute 'kate' for gedit' in the above.
[/QUOTE]

i tried this but it doesn't seem to work... :???: 

```
Error: "/var/tmp/kdecache-laurent" is owned by uid 1000 instead of uid 0.
Link points to "/var/tmp/kdecache-root"
kate: ERROR: Communication problem with kate, it probably crashed.
```

[edit]
it's ok i tried typing kdesu kate on the Run Command line.
and i can edit the file now...
i'm waiting for your help on how to edit the file...

---

### Post by Jahmon on 2005-09-16
[QUOTE=mlomker]
If you post the output from that fdisk command and your /etc/fstab then I could tell you the steps.[/QUOTE]

here is the Fdisk Command ( a part of it is in french)
```

Disque /dev/hda: 251.0 Go, 251000193024 octets
255 têtes, 63 secteurs/piste, 30515 cylindres
Unités = cylindres de 16065 * 512 = 8225280 octets

Périphérique Amorce    Début         Fin      Blocs    Id  Système
/dev/hda1   *           1        3647    29294496    7  HPFS/NTFS
/dev/hda2            3648       30515   215817210    5  Extended
/dev/hda5            3648       16413   102542863+   b  W95 FAT32
/dev/hda6           16414       30515   113274283+   b  W95 FAT32

Disque /dev/hdb: 15.3 Go, 15367790592 octets
255 têtes, 63 secteurs/piste, 1868 cylindres
Unités = cylindres de 16065 * 512 = 8225280 octets

Périphérique Amorce    Début         Fin      Blocs    Id  Système
/dev/hdb1   *           1        1788    14362078+  83  Linux
/dev/hdb2            1789        1868      642600    5  Extended
/dev/hdb5            1789        1868      642568+  82  Linux swap / Solaris

Disque /dev/sda: 1040 Mo, 1040187392 octets
16 têtes, 32 secteurs/piste, 3968 cylindres
Unités = cylindres de 512 * 512 = 262144 octets

Périphérique Amorce    Début         Fin      Blocs    Id  Système
/dev/sda1   *           1        3968     1015792    6  FAT16
```

this is the /etc/fstab file:
```

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hdb1       /               ext3    defaults,errors=remount-ro 0       1
/dev/hdb5       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 ro,user,noauto  0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0 
```






i tried ```
sudo mkdir /dev/hda5
``` and it says it already exists but it's not a directory...
here is a print screen of it..[http://users.skynet.be/limbort/fun/dev_hdX.jpg](http://users.skynet.be/limbort/fun/dev_hdX.jpg)

---

### Post by angkor on 2005-09-16
Did you read the Ubuntu guide in the link I posted?

try this:

[http://www.ubuntuguide.org/#automountfat](http://www.ubuntuguide.org/#automountfat)

Just follow the steps and post any problem you might encounter.

Bookmark the Ubuntu Starter Guide cause it'll be your best friend discovering Ubuntu.

Edit: Note that the guide explains things when doing it from the command line. Open up a terminal by going to Applications -> System Tools-> Terminal and type the commands you read in the Ubuntuguide. Just substitute the /dev/hda1 in the guide with your /dev/hda5.

---

### Post by Jahmon on 2005-09-16
i DID look at the guide you posted, i'd love to be a linux user but i don't know why, every thing seems to go wrong....

i tried the link you posted for hda1 ntfs and Fat and got for both this error:

```
laurent@ubuntu:~$ sudo mount -a
Password:
mount: wrong fs type, bad option, bad superblock on /dev/hda1,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

laurent@ubuntu:~$
```

this is what i did to change hda1 into ntfs:

```

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda1       /media/windows  ntfs    nlf=utf8,umask02222 0 0
/dev/hdb1       /               ext3    defaults,errors=remount-ro 0       1
/dev/hdb5       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 ro,user,noauto  0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0
``` 

i created a /media/windows directory

---

### Post by mlomker on 2005-09-16
It looks like you're pretty close.  I would have made the directory under /mnt/windows but it doesn't really matter.

```

/dev/hda1  /media/windows  ntfs  defaults,umask=0222 0 2

```

**sudo mount /dev/hda1** should mount it.

---

### Post by Jahmon on 2005-09-17
[QUOTE=mlomker]
```

/dev/hda1  /media/windows  ntfs  defaults,umask=0222 0 2

```

**sudo mount /dev/hda1** should mount it.[/QUOTE]

Great it worked !

I understood how to mount the 2 other ( fat32 ) partitions \\:D/ 
Is it normal i still have some partitions left that i'm not using ?

---

