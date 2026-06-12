---
title: "problem with partitiontable"
date: 2011-09-05
forum: Installation &amp; Upgrades
---

### Post by Neutrosider on 2011-09-05
I'm trying to make a boot time comparison between about 18 operating systems (5 windows, everyting else linux)
i was able to manage all problems myself up to the point when i tried to install windows XP. i knew it would screw my mbr and my boot manager and the partition table, but thats no problem. Im able to fix them using testdisk and boot-repair. well i thought so. after the installation of windows 7 32bit and 64 bit and windows vista, this method worked and i could boot all the systems i installed so far. i then installed versions of oepnsuse and ubuntu. everything was fine up to that point. then i used gpartet to prepair a NTFS partition for windows XP (because the xp installer told me there were too many partitions, but gpartet did the job :D). well then the xp installer copied all the necessary files, and then rebooted. after the reboot it told me that the partition table is broken. so i repaired it using testdisk. i also reinstalled grub.

now im able to boot all the linux distros i installed so far, but the windows systems won't boot, the partition tools of the upcoming linux installers (like fedora and debian) are unable to detect the partitions and gparted shows the following:
[IMG]http://zload.file4u.net/ax/nichtaxdateien/gparted.png[/IMG]
[SIZE=2]**while fdisk shows the korrekt partitions:**[/SIZE]
[IMG]http://zload.file4u.net/ax/nichtaxdateien/fdisk.png[/IMG]

what can i do?

btw:

[LIST]
[*]sda1: NTFS space
[*]sda2: Ubuntu 64 bit (writing from that one atm)
[*]sda3: swap space
[*]sda4:  installed win 7 32 bit there, but its not sown as regular ntfs since xp try ( i think thas why its not booting any windows now)
[*]sda5: Windows 7 64 bit, not booting since xp try
[*]sda6: Windows Vista 32 bit, not booting since xp try
[*]sda7: OpenSuse 32 Bit (not tested, but should boot)
[*]sda8: OpenSuse 64 Bit (not tested, but should boot)
[*]sda9: Ubuntu 32 Bit (not tested, but should boot)
[*]sda10: Ubuntu 64 Bit (not tested, but should boot)
[*]sda11: LinuxMint 32 Bit (not tested, but should boot)
[*]sda12: LinuxMint 64 Bit (not tested, but shpuld boot)
[*]sda13: intended to becom the windows XP Partition
[*]sda14: i forgot what's there, some linux distro
[*]sda15: some swap space that got there because of one wrong configured install, but this partition doestn't hurt anyone
[/LIST]

---

### Post by YesWeCan on 2011-09-05
You're mad! :p
Would you mind posting: [COLOR="DarkSlateBlue"]sudo sfdisk -luS[/COLOR]
It will show the partitions by sector.

---

### Post by Neutrosider on 2011-09-05
here it is:
[IMG]http://zload.file4u.net/ax/nichtaxdateien/f.png[/IMG]

i also get an error when i try to boot one of some of the installed linux. for example, two of the 4 ubuntus and linux mint are booting. i'll test opensuse now.

---

### Post by critin on 2011-09-05
Wow!  I envy you--wish I had a disk large enough to do that.  lol
critin

---

### Post by Neutrosider on 2011-09-06
this disk has "only" 400 GB, but most of my linux partitions take only 5 GB.
i now got more strange problems. when i for example choose OpenSuse, it shows the boot-progress of OpenSuse (the scrolling text on the nice background) but then it suddenly shows the Ubuntu Boot-logo and boots ubuntu. as far as i tested, all the installations, wich btw worked perfectly before i tryed xp, wont boot properly except one of the 5 GB ubuntu and the LinuxMints. I now bootet an ubuntu i installed on my usb stick :P

well does someone know how to sovle all this? i even would reinstall most of the operating systems and do the boot-test video directly after the installation, but as i said i'm unable to intall new systems, because the intsallers won't recognize my partitions properly since the xp try, and i want to keep at least my main ubuntu and the big sda1 NTFS partition...

---

### Post by Hakunka-Matata on 2011-09-06
The **fdisk -l**  output shown in figure one has several partitions starting in the same sector and the previous partition ended in?  But of course **sfdisk -luS** does not show the errors?  

Have you tried running fsck &/or e2fsck on each partition?

sudo e2fsck /dev/sda1 (for example)  try the -c option.
```

das@1110-b1:~$ sudo e2fsck /dev/sda1
[sudo] password for das: 
e2fsck 1.41.14 (22-Dec-2010)
9.10: clean, 378305/2564096 files, 9028711/10239421 blocks
das@1110-b1:~$ sudo fsck /dev/sda1
fsck from util-linux 2.19.1
e2fsck 1.41.14 (22-Dec-2010)
9.10: clean, 378305/2564096 files, 9028711/10239421 blocks
das@1110-b1:~$ man e3fsck
No manual entry for e3fsck
das@1110-b1:~$ man e2fsck
das@1110-b1:~$ sudo fsck -c /dev/sda1
fsck from util-linux 2.19.1
e2fsck 1.41.14 (22-Dec-2010)
Checking for bad blocks (read-only test): done                                
9.10: Updating bad block inode.
Pass 1: Checking inodes, blocks, and sizes
Pass 2: Checking directory structure
Pass 3: Checking directory connectivity
Pass 4: Checking reference counts
Pass 5: Checking group summary information

9.10: ***** FILE SYSTEM WAS MODIFIED *****
9.10: 378305/2564096 files (1.9% non-contiguous), 9028711/10239421 blocks
das@1110-b1:~$ ^C
```

---

### Post by Neutrosider on 2011-09-06
ok, tried this on all my partitions. then i tried booting my main ubuntu, and i worked :)
then i tried to boot OpenSuse, but as before it showed the OpenSuse boot screen, then the ubuntu boot logo and it bootet one of the 5 GB ubuntu
then i tried my main ubuntu again, but this time it didn't work. it shows me the following error:
```
mountall: Disconnected from Plymouth
```

then i tried fsck -c /dev/sda2 again, but i get the same error...

---

### Post by YesWeCan on 2011-09-06
> **Hakunka-Matata said:**
> The **fdisk -l**  output shown in figure one has several partitions starting in the same sector and the previous partition ended in?  But of course **sfdisk -luS** does not show the errors?
fdisk -l shows the partition boundaries in cylinders. There are 16065 sectors per cyclinder so the resolution is not good. That's why I asked for the sector display.

---

### Post by YesWeCan on 2011-09-06
> **Neutrosider said:**
> ok, tried this on all my partitions. then i tried booting my main ubuntu, and i worked :)
You are in some sort of boot-loader Hell. :P

When in doubt, simplify! Have you got a spare USB stick of 4GB lying around? If so, install Ubuntu to it and use it as your boot device. This way when you install new OS's or delete them your boot-loader will not be affected. This will also avoid the tedious conflicts with Windows when Grub breaks the MBR on your main disk. When you install a new linux OS try not to install Grub at all and if forced (Ubuntu's desktop installer forces it!) then install somewhere benign like the root partition.

---

### Post by Neutrosider on 2011-09-06
i have a 16 GB USB stick with ubuntu and all the programms i need installed here. a real life-saver :)

when nothing works im used to use it to fix everything^^
the bootloader doesn't seem to be the problem, but the partition table. i think so because i CAN boot my main ubuntu (after fixing the bootloader using boot-repair), wich is on sda2, but neither gparted, nor any os installer is able to recognize my partitons. only fdsk -l, the drive manager, boot-repair and testdisk are recognizing my partitions correctly

---

### Post by YesWeCan on 2011-09-06
Your partition table looks ok to me according to sfdisk.
What about Disk Utility, does it see your partitions?

Can you repost the output of sfdisk -luS but copy&paste rather than a photo, that way I can copy the numbers into a spreadsheet to check them?

Also, your GParted photo shows a red "!". What is the warning? (click the symbol)

---

### Post by Neutrosider on 2011-09-06
i think with disk utility you mean whats called Laufwerksverwaltung at my german ubuntu. it IS able to recognize the partitions.

the ! in gparted is no button, but when i doubleclick it, its the same as i would try to make a new partition. i get an error message saying.
> Partitionen ausserhalb der festplatte sind nicht möglichin english:
> partitions outside the hard drive are not possiblealthough you only need sda, i'll give you the full output. it includes sdb (a 250 GB Hard drive with one NTFS partition) and sdc (my 16 GB usb stick with an Ubuntu OS and the Ubuntu CD on it):
```
heiko@PC-Heiko:~$ sudo sfdisk -luS
[sudo] password for heiko: 

Festplatte /dev/sda: 48641 Zylinder, 255 Köpfe, 63 Sektoren/Spur
Warnung: erweiterte Partition beginnt nicht an einer Zylindergrenze
DOS und Linux werden den Inhalt unterschiedlich interpretieren.
Einheit = Sektoren von 512 Bytes, Zählung beginnt bei 0

   Gerät  boot.   Anfang      Ende  #Sektoren Id  System
/dev/sda1   *      2048 420167672  420165625   7  HPFS/NTFS
/dev/sda2     420169728 515311615   95141888  83  Linux
/dev/sda3     515313664 519503855    4190192  82  Linux Swap / Solaris
/dev/sda4     519503859 781433729  261929871   f  W95 Erw. (LBA)
/dev/sda5     519505920 561448959   41943040   7  HPFS/NTFS
/dev/sda6     561451008 592908287   31457280   7  HPFS/NTFS
/dev/sda7     592910336 605489151   12578816  83  Linux
/dev/sda8     605491200 615976959   10485760  83  Linux
/dev/sda9     615983104 625981439    9998336  83  Linux
/dev/sda10    625983488 635981823    9998336  83  Linux
/dev/sda11    635983872 645982207    9998336  83  Linux
/dev/sda12    645984256 655982591    9998336  83  Linux
/dev/sda13    655984640 666470399   10485760   7  HPFS/NTFS
/dev/sda14    682088448 777230335   95141888  83  Linux
/dev/sda15    777232384 781422575    4190192  82  Linux Swap / Solaris

Festplatte /dev/sdb: 30401 Zylinder, 255 Köpfe, 63 Sektoren/Spur
Einheit = Sektoren von 512 Bytes, Zählung beginnt bei 0

   Gerät  boot.   Anfang      Ende  #Sektoren Id  System
/dev/sdb1   *        63 488375999  488375937   7  HPFS/NTFS
/dev/sdb2             0         -          0   0  Leer
/dev/sdb3             0         -          0   0  Leer
/dev/sdb4             0         -          0   0  Leer

Festplatte /dev/sdc: 15680 Zylinder, 64 Köpfe, 32 Sektoren/Spur
Warnung: erweiterte Partition beginnt nicht an einer Zylindergrenze
DOS und Linux werden den Inhalt unterschiedlich interpretieren.
Einheit = Sektoren von 512 Bytes, Zählung beginnt bei 0

   Gerät  boot.   Anfang      Ende  #Sektoren Id  System
/dev/sdc1      15540222  32112639   16572418   5  Erweiterte
        Anfang: (c,h,s) erwartet (1023,63,32) gefunden (967,85,13)
        Ende: (c,h,s) erwartet (1023,63,32) gefunden (1023,254,63)
/dev/sdc2          2048  15538175   15536128  83  Linux
        Anfang: (c,h,s) erwartet (1,0,1) gefunden (0,32,33)
        Ende: (c,h,s) erwartet (1023,63,32) gefunden (967,52,45)
/dev/sdc3             0         -          0   0  Leer
/dev/sdc4             0         -          0   0  Leer
/dev/sdc5      15540224  17614847    2074624  82  Linux Swap / Solaris
        Anfang: (c,h,s) erwartet (1023,63,32) gefunden (967,85,15)
        Ende: (c,h,s) erwartet (1023,63,32) gefunden (1023,254,63)
/dev/sdc6      19152896  32112639   12959744   b  W95 FAT32
        Anfang: (c,h,s) erwartet (1023,63,32) gefunden (1023,254,63)
        Ende: (c,h,s) erwartet (1023,63,32) gefunden (1023,254,63)
/dev/sdc7   *  17616896  19150847    1533952   b  W95 FAT32
        Anfang: (c,h,s) erwartet (1023,63,32) gefunden (1023,254,63)
        Ende: (c,h,s) erwartet (1023,63,32) gefunden (1023,254,63)

```

btw, there are 2 partitions, then an extended partition including about 11 logical partitions and after that extendet there is one ntfs partition.

---

### Post by YesWeCan on 2011-09-06
Now I see. :)

sda4 is the extended partition. It's end sector is 781433729 but the total sectors on disk are 400088457216/512 = 781422768.

The last sector in the extended partition is beyond the last available sector on the disk.

I was suspicious of sda4 because it is labelled "W95 [COLOR="Red"]Erw.[/COLOR] (LBA)" which I have not seen before. I'm sure it usually says Ext. Also, in your OP you wrote:
"sda4: installed win 7 32 bit there, but its not sown as regular ntfs since xp try ( i think thas why its not booting any windows now)".
So what did you do - did you try to install to the extended partition?


You can try fixing the extended partition "size" in the MBR partition table and see what happens. To do this, first copy the PT into a file:
[COLOR="DarkSlateBlue"]sudo sfdisk -d /dev/sda > PT.txt[/COLOR]
Then edit the file and change the size of sda4 from 261929871 to 261918717 sectors.
This should make the last sector of the ext'd 781422575 which is also the last sector of sda15.
Then copy it back into the MBR
[COLOR="DarkSlateBlue"]sudo sh -c "cat PT.txt | sfdisk /dev/sda"[/COLOR]

Then see if GParted is happier.

---

### Post by Neutrosider on 2011-09-06
oh, not ext4 isn't windows, but ext3. and according to the image ill show  you, the extendetd partition is NOT the last partition. please check if  you're realy sure about the extended partition size:
[http://zload.file4u.net/ax/nichtaxdateien/Bildschirmfoto-2.png](http://zload.file4u.net/ax/nichtaxdateien/Bildschirmfoto-2.png)
i labled the unlabled partitions with gimp.

i forgot to label the last thing where the picture sais free space. this is windows 7 32 bit

---

### Post by YesWeCan on 2011-09-06
> **Neutrosider said:**
> oh, not ext4 isn't windows, but ext3. and according to the image ill show  you, the extendetd partition is NOT the last partition. please check if  you're realy sure about the extended partition size:
[http://zload.file4u.net/ax/nichtaxdateien/Bildschirmfoto-2.png](http://zload.file4u.net/ax/nichtaxdateien/Bildschirmfoto-2.png)
i labled the unlabled partitions with gimp.

i forgot to label the last thing where the picture sais free space. this is windows 7 32 bit
This is what the partition tables are reporting. The red number is bigger than the blue number. Partition 4 is the last primary partition and so it must end between the end of the last logical partition (sda15) and the end of the disk.

```

part #             start     end       size         gap    size GB
    1      NTFS    2048      420167672 420165625      2048 215.1
    2      Ubuntu  420169728 515311615  95141888      2056  48.7
    3      swap    515313664 519503855   4190192      2049   2.1
    4      ext'd   519503859 [COLOR="Red"]781433729[/COLOR] 261929871         4 134.1
        
    5      Vista   519505920 561448959  41943040      2061  21.5
    6      SuSE    561451008 592908287  31457280      2049  16.1
    7      SuSE    592910336 605489151  12578816      2049   6.4
    8      Ubuntu  605491200 615976959  10485760      2049   5.4
    9      Ubuntu  615983104 625981439   9998336      6145   5.1
   10      Ubuntu  625983488 635981823   9998336      2049   5.1
   11      Mint    635983872 645982207   9998336      2049   5.1
   12      Mint    645984256 655982591   9998336      2049   5.1
   13      NTFS    655984640 666470399  10485760      2049   5.4
   14      linux?  682088448 777230335  95141888  15618049  48.7
   15      swap    777232384 781422575   4190192      2049   2.1
        
  last sector on disk: [COLOR="Blue"]781422767[/COLOR]  
```

---

### Post by Neutrosider on 2011-09-06
well, thets the output of [COLOR=DarkSlateBlue]sudo sh -c "cat PT.txt | sfdisk /dev/sda"
[COLOR=Black][FONT=Verdana]```
ubuntu@ubuntu:~$ sudo sh -c "cat PT.txt | sfdisk /dev/sda"
Überprüfe, dass niemand diese Festplatte zur Zeit benutzt &#8230;
OK

Festplatte /dev/sda: 48641 Zylinder, 255 Köpfe, 63 Sektoren/Spur
Warnung: erweiterte Partition beginnt nicht an einer Zylindergrenze
DOS und Linux werden den Inhalt unterschiedlich interpretieren.
Alte Aufteilung:
Einheit = Zylinder von 8225280 Bytes, Blöcke von 1024 Bytes, Zählung beginnt bei 0

   Gerät  boot. Anfang   Ende  #Zyl.    #Blöcke   Id  System
/dev/sda1   *      0+  26154-  26155- 210082812+   7  HPFS/NTFS
/dev/sda2      26154+  32076-   5923-  47570944   83  Linux
/dev/sda3      32076+  32337-    261-   2095096   82  Linux Swap / Solaris
/dev/sda4      32337+  48641   16305- 130964935+   f  W95 Erw. (LBA)
/dev/sda5      32337+  34948-   2611-  20971520    7  HPFS/NTFS
/dev/sda6      34948+  36906-   1959-  15728640    7  HPFS/NTFS
/dev/sda7      36906+  37689-    783-   6289408   83  Linux
/dev/sda8      37690+  38342-    653-   5242880   83  Linux
/dev/sda9      38343+  38965-    623-   4999168   83  Linux
/dev/sda10     38965+  39588-    623-   4999168   83  Linux
/dev/sda11     39588+  40210-    623-   4999168   83  Linux
/dev/sda12     40210+  40833-    623-   4999168   83  Linux
/dev/sda13     40833+  41485-    653-   5242880    7  HPFS/NTFS
/dev/sda14     42458+  48380-   5923-  47570944   83  Linux
/dev/sda15     48380+  48641-    261-   2095096   82  Linux Swap / Solaris
Warnung: gegebene Größe (488375937) überschreitet maximal erlaubte Größe (1985)

sfdisk: ungültige Eingabe

```why are there all these + and - that hasn't been there before? here's a bit of translation:
[/FONT][/COLOR][/COLOR]> [COLOR=DarkSlateBlue][COLOR=Black][FONT=Verdana]Überprüfe, dass niemand diese Festplatte zur Zeit benutzt &#8230;
OK
      
Festplatte /dev/sda: 48641 Zylinder, 255 Köpfe, 63 Sektoren/Spur
Warnung: erweiterte Partition beginnt nicht an einer Zylindergrenze
DOS und Linux werden den Inhalt unterschiedlich interpretieren.
Alte Aufteilung:
Einheit = Zylinder von 8225280 Bytes, Blöcke von 1024 Bytes, Zählung beginnt bei 0 [...] [/FONT][/COLOR][/COLOR][COLOR=DarkSlateBlue][COLOR=Black][FONT=Verdana]Warnung: gegebene Größe (488375937) überschreitet maximal erlaubte Größe (1985)[/FONT][/COLOR][/COLOR][COLOR=DarkSlateBlue][COLOR=Black][FONT=Verdana]
in english:[/FONT][/COLOR][/COLOR]> [COLOR=DarkSlateBlue][COLOR=Black][FONT=Verdana]check if the hard drive is in use at the moment...
OK
      
Festplatte /dev/sda: 48641 Zylinder, 255 Heads, 63 Sektores/Spur
Warning: extended Partition does not start at an Zylindergrenze(doesn't know the english equivalent to Zylingergrenze)
DOS and Linux will interpret the content in different ways.
old seperation:
Unit = Zylinder by 8225280 Bytes, blocks by 1024 Bytes, counting from 0[/FONT][/COLOR][/COLOR][COLOR=DarkSlateBlue][COLOR=Black][FONT=Verdana] [...] Warning: given size([/FONT][/COLOR][/COLOR][COLOR=DarkSlateBlue][COLOR=Black][FONT=Verdana]488375937) [/FONT][/COLOR][/COLOR]exceeds the maximum allowed size (1985)[COLOR=DarkSlateBlue][COLOR=Black][FONT=Verdana]

Sadly gpartet isn't happier yet
[/FONT][/COLOR][/COLOR]

---

### Post by YesWeCan on 2011-09-06
BTW XP won't install to a logical partition as far as I know. I'm not sure any Windows OS will. So it is usual to keep primary partitions spare for Windows installs and make all your linux stuff logical.

In your case, I'd suggest using partitions 1 to 3 for W7, Vista and  XP OSs. Partition 4 cannot be used because it is the logical partition container. Then install all linux to logical partitions.

---

### Post by YesWeCan on 2011-09-06
Would you mind using sfdisk -luS?

---

### Post by Neutrosider on 2011-09-06
here it is:
```
heiko@PC-Heiko:~$ sudo sfdisk -luS
[sudo] password for heiko: 

Festplatte /dev/sda: 48641 Zylinder, 255 Köpfe, 63 Sektoren/Spur
Warnung: erweiterte Partition beginnt nicht an einer Zylindergrenze
DOS und Linux werden den Inhalt unterschiedlich interpretieren.
Einheit = Sektoren von 512 Bytes, Zählung beginnt bei 0

   Gerät  boot.   Anfang      Ende  #Sektoren Id  System
/dev/sda1   *      2048 420167672  420165625   7  HPFS/NTFS
/dev/sda2     420169728 515311615   95141888  83  Linux
/dev/sda3     515313664 519503855    4190192  82  Linux Swap / Solaris
/dev/sda4     519503859 781433729  261929871   f  W95 Erw. (LBA)
/dev/sda5     519505920 561448959   41943040   7  HPFS/NTFS
/dev/sda6     561451008 592908287   31457280   7  HPFS/NTFS
/dev/sda7     592910336 605489151   12578816  83  Linux
/dev/sda8     605491200 615976959   10485760  83  Linux
/dev/sda9     615983104 625981439    9998336  83  Linux
/dev/sda10    625983488 635981823    9998336  83  Linux
/dev/sda11    635983872 645982207    9998336  83  Linux
/dev/sda12    645984256 655982591    9998336  83  Linux
/dev/sda13    655984640 666470399   10485760   7  HPFS/NTFS
/dev/sda14    682088448 777230335   95141888  83  Linux
/dev/sda15    777232384 781422575    4190192  82  Linux Swap / Solaris

Festplatte /dev/sdb: 30401 Zylinder, 255 Köpfe, 63 Sektoren/Spur
Einheit = Sektoren von 512 Bytes, Zählung beginnt bei 0

   Gerät  boot.   Anfang      Ende  #Sektoren Id  System
/dev/sdb1   *        63 488375999  488375937   7  HPFS/NTFS
/dev/sdb2             0         -          0   0  Leer
/dev/sdb3             0         -          0   0  Leer
/dev/sdb4             0         -          0   0  Leer

Festplatte /dev/sdc: 15680 Zylinder, 64 Köpfe, 32 Sektoren/Spur
Warnung: erweiterte Partition beginnt nicht an einer Zylindergrenze
DOS und Linux werden den Inhalt unterschiedlich interpretieren.
Einheit = Sektoren von 512 Bytes, Zählung beginnt bei 0

   Gerät  boot.   Anfang      Ende  #Sektoren Id  System
/dev/sdc1      15540222  32112639   16572418   5  Erweiterte
        Anfang: (c,h,s) erwartet (1023,63,32) gefunden (967,85,13)
        Ende: (c,h,s) erwartet (1023,63,32) gefunden (1023,254,63)
/dev/sdc2          2048  15538175   15536128  83  Linux
        Anfang: (c,h,s) erwartet (1,0,1) gefunden (0,32,33)
        Ende: (c,h,s) erwartet (1023,63,32) gefunden (967,52,45)
/dev/sdc3             0         -          0   0  Leer
/dev/sdc4             0         -          0   0  Leer
/dev/sdc5      15540224  17614847    2074624  82  Linux Swap / Solaris
        Anfang: (c,h,s) erwartet (1023,63,32) gefunden (967,85,15)
        Ende: (c,h,s) erwartet (1023,63,32) gefunden (1023,254,63)
/dev/sdc6      19152896  32112639   12959744   b  W95 FAT32
        Anfang: (c,h,s) erwartet (1023,63,32) gefunden (1023,254,63)
        Ende: (c,h,s) erwartet (1023,63,32) gefunden (1023,254,63)
/dev/sdc7   *  17616896  19150847    1533952   b  W95 FAT32
        Anfang: (c,h,s) erwartet (1023,63,32) gefunden (1023,254,63)
        Ende: (c,h,s) erwartet (1023,63,32) gefunden (1023,254,63)

```it seems it had no effect at all. i think sda4 istn't the only partition with wrong size, may that be?

btw, windows 7 32 bit and vista 32 bit worked perfectly on the logical partitions until i tried XP

edit: at the end it also sais
> [COLOR=DarkSlateBlue][COLOR=Black][FONT=Verdana]sfdisk: ungültige Eingabe

wich means sfdisk: invalid input
[/FONT][/COLOR][/COLOR]

---

### Post by YesWeCan on 2011-09-06
please post PT.txt

---

### Post by Neutrosider on 2011-09-06
thats the edited PT.txt. as you said i changed the size of sda4. should i just try it again?
```
# partition table of /dev/sda
unit: sectors

/dev/sda1 : start=     2048, size=420165625, Id= 7, bootable
/dev/sda2 : start=420169728, size= 95141888, Id=83
/dev/sda3 : start=515313664, size=  4190192, Id=82
/dev/sda4 : start=519503859, size=261918717, Id= f
/dev/sda5 : start=519505920, size= 41943040, Id= 7
/dev/sda6 : start=561451008, size= 31457280, Id= 7
/dev/sda7 : start=592910336, size= 12578816, Id=83
/dev/sda8 : start=605491200, size= 10485760, Id=83
/dev/sda9 : start=615983104, size=  9998336, Id=83
/dev/sda10: start=625983488, size=  9998336, Id=83
/dev/sda11: start=635983872, size=  9998336, Id=83
/dev/sda12: start=645984256, size=  9998336, Id=83
/dev/sda13: start=655984640, size= 10485760, Id= 7
/dev/sda14: start=682088448, size= 95141888, Id=83
/dev/sda15: start=777232384, size=  4190192, Id=82
# partition table of /dev/sdb
unit: sectors

/dev/sdb1 : start=       63, size=488375937, Id= 7, bootable
/dev/sdb2 : start=        0, size=        0, Id= 0
/dev/sdb3 : start=        0, size=        0, Id= 0
/dev/sdb4 : start=        0, size=        0, Id= 0
# partition table of /dev/sdc
unit: sectors

/dev/sdc1 : start= 15540222, size= 16572418, Id= 5
/dev/sdc2 : start=     2048, size= 15536128, Id=83
/dev/sdc3 : start=        0, size=        0, Id= 0
/dev/sdc4 : start=        0, size=        0, Id= 0
/dev/sdc5 : start= 15540224, size=  2074624, Id=82
/dev/sdc6 : start= 19152896, size= 12959744, Id= b
/dev/sdc7 : start= 17616896, size=  1533952, Id= b, bootable
```

---

### Post by YesWeCan on 2011-09-06
Sorry - I made a mistake. I forgot the drive name so it made a PT.txt for all the drives. The command should be
[COLOR="DarkSlateBlue"]sudo sfdisk -d /dev/sda > PT.txt[/COLOR]

Then edit PT.txt to change the size of sda4 and then
[COLOR="DarkSlateBlue"]sudo sh -c "cat PT.txt | sfdisk /dev/sda"[/COLOR]

---

### Post by Hakunka-Matata on 2011-09-06
> **YesWeCan said:**
> Now I see. :)

sda4 is the extended partition. It's end sector is 781433729 but the total sectors on disk are 400088457216/512 = 781422768.

The last sector in the extended partition is beyond the last available sector on the disk.

I was suspicious of sda4 because it is labelled "W95 [COLOR=Red]**Erw**.[/COLOR] (LBA)" which I have not seen before. I'm sure it usually says Ext. Also, in your OP you wrote:
"sda4: installed win 7 32 bit there, but its not sown as regular ntfs since xp try ( i think thas why its not booting any windows now)".
So what did you do - did you try to install to the extended partition?


You can try fixing the extended partition "size" in the MBR partition table and see what happens. To do this, first copy the PT into a file:
[COLOR=DarkSlateBlue]sudo sfdisk -d > PT.txt[/COLOR]
Then edit the file and change the size of sda4 from 261929871 to 261918717 sectors.
This should make the last sector of the ext'd 781422575 which is also the last sector of sda15.
Then copy it back into the MBR
[COLOR=DarkSlateBlue]sudo sh -c "cat PT.txt | sfdisk /dev/sda"[/COLOR]

Then see if GParted is happier.

[COLOR=Red][B][COLOR=Black]@YesWeCan:[/COLOR]
[/B][/COLOR][COLOR=Red]**Erw**.  [/COLOR]probably stands for [COLOR=Red]Erweitert[/COLOR] which translates to "extended" in Englisch.

---

### Post by YesWeCan on 2011-09-06
> **Hakunka-Matata said:**
> [COLOR=Red][B][COLOR=Black]@YesWeCan:[/COLOR]
[/B][/COLOR][COLOR=Red]**Erw**.  [/COLOR]probably stands for [COLOR=Red]Erweitert[/COLOR] which translates to "extended" in Englisch.
Of course! Well spotted. :)

---

### Post by YesWeCan on 2011-09-06
> **Neutrosider said:**
> btw, windows 7 32 bit and vista 32 bit worked perfectly on the logical partitions until i tried XP
So you were able to install Vista and W7 to logical partitions? Is that right?
Interesting. I am sure someone told me Windows had to be installed to primary partitions. Perhaps it is only XP.

---

### Post by Neutrosider on 2011-09-06
ok, i'm at a live ubuntu atm. tried this, and it gives me a different output. it says:
```
ubuntu@ubuntu:~$ sudo sh -c "cat PT.txt | sfdisk /dev/sda"
Überprüfe, dass niemand diese Festplatte zur Zeit benutzt &#8230;
OK

Festplatte /dev/sda: 48641 Zylinder, 255 Köpfe, 63 Sektoren/Spur
Warnung: erweiterte Partition beginnt nicht an einer Zylindergrenze
DOS und Linux werden den Inhalt unterschiedlich interpretieren.
Alte Aufteilung:
Einheit = Zylinder von 8225280 Bytes, Blöcke von 1024 Bytes, Zählung beginnt bei 0

   Gerät  boot. Anfang   Ende  #Zyl.    #Blöcke   Id  System
/dev/sda1   *      0+  26154-  26155- 210082812+   7  HPFS/NTFS
/dev/sda2      26154+  32076-   5923-  47570944   83  Linux
/dev/sda3      32076+  32337-    261-   2095096   82  Linux Swap / Solaris
/dev/sda4      32337+  48641   16305- 130964935+   f  W95 Erw. (LBA)
/dev/sda5      32337+  34948-   2611-  20971520    7  HPFS/NTFS
/dev/sda6      34948+  36906-   1959-  15728640    7  HPFS/NTFS
/dev/sda7      36906+  37689-    783-   6289408   83  Linux
/dev/sda8      37690+  38342-    653-   5242880   83  Linux
/dev/sda9      38343+  38965-    623-   4999168   83  Linux
/dev/sda10     38965+  39588-    623-   4999168   83  Linux
/dev/sda11     39588+  40210-    623-   4999168   83  Linux
/dev/sda12     40210+  40833-    623-   4999168   83  Linux
/dev/sda13     40833+  41485-    653-   5242880    7  HPFS/NTFS
/dev/sda14     42458+  48380-   5923-  47570944   83  Linux
/dev/sda15     48380+  48641-    261-   2095096   82  Linux Swap / Solaris
Neue Aufteilung:
Einheit = Sektoren von 512 Bytes, Zählung beginnt bei 0

   Gerät  boot.   Anfang      Ende  #Sektoren Id  System
/dev/sda1   *      2048 420167672  420165625   7  HPFS/NTFS
/dev/sda2     420169728 515311615   95141888  83  Linux
/dev/sda3     515313664 519503855    4190192  82  Linux Swap / Solaris
/dev/sda4     519503859 781422575  261918717   f  W95 Erw. (LBA)
/dev/sda5     519505920 561448959   41943040   7  HPFS/NTFS
/dev/sda6     561451008 592908287   31457280   7  HPFS/NTFS
/dev/sda7     592910336 605489151   12578816  83  Linux
/dev/sda8     605491200 615976959   10485760  83  Linux
/dev/sda9     615983104 625981439    9998336  83  Linux
/dev/sda10    625983488 635981823    9998336  83  Linux
/dev/sda11    635983872 645982207    9998336  83  Linux
/dev/sda12    645984256 655982591    9998336  83  Linux
/dev/sda13    655984640 666470399   10485760   7  HPFS/NTFS
/dev/sda14    682088448 777230335   95141888  83  Linux
/dev/sda15    777232384 781422575    4190192  82  Linux Swap / Solaris
Warnung: Partition 1 endet nicht an einer Zylindergrenze

sfdisk: Mir gefallen diese Partitionen nicht &#8211; nichts geändert.
(Wenn Sie das wirklich wollen, benutzen Sie die Option --force.)

```now again a bit translation of whats new:
```
Warnung: Partition 1 endet nicht an einer Zylindergrenze

sfdisk: Mir gefallen diese Partitionen nicht &#8211; nichts geändert.
(Wenn Sie das wirklich wollen, benutzen Sie die Option --force.)
```in english:
```
warning: Partition 1 is not ending at an Zylindergrenze (as before i don't the translation of that word)

sfdisk: i don't like these partitions &#8211; nothing changed.
(if you really want it, use the option --force.)
```

EDIT:
yep, 7 and vista worked at logical partitions for me

---

### Post by YesWeCan on 2011-09-06
Zylindergrenze = cylinder boundary

I *think* sfdisk is just being cautious. The cylinder boundary is not important. The new PT it shows looks ok to me.

There is always a risk of data loss when messing with partitions, of course. So if there is anything vital on this disk you should back it up before doing anything further. Just to be on the safe side.

---

### Post by YesWeCan on 2011-09-06
> **Neutrosider said:**
> yep, 7 and vista worked at logical partitions for me
It must only be possible if Windows installs a primary "system" partition for its boot-loader, or if one already exists. Because the normal MBR code will only boot a primary partition (the one with boot flag set).

---

### Post by Neutrosider on 2011-09-06
yay, gpartet is actually recognizing my partitions again, altough not 100% right. will try to boot some linux partitions and report the result :)

---

### Post by Neutrosider on 2011-09-06
ok. gparted detects my partitions, thats good. i think installing new operating systems SHOULD now work. i can also boot linux mint now. the other systems are still unbootable ^^

---

### Post by YesWeCan on 2011-09-06
It may be time to run [http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
and post RESULTS.txt

---

### Post by Hakunka-Matata on 2011-09-06
[B]W95 Ext'd (LBA), often appears in partition tables, is that a *bad *sign.  
[/B]

And in Linux systems it appears as "**/dev/sda4     140004+ 238474  98471- 100833281    5  Extended**".

**IS **then the W95 Ext'd (LBA) a bad sign in itself?  What partitioner(s) labels the Extended partition (W95 Ext'd (LBA)?

it's one of those "I wonder if xxx"  because so often posters with partition table problems, show the W95 style label???

---

### Post by Neutrosider on 2011-09-06
thats a long file :) so here it is:
[http://zload.file4u.net/ax/nichtaxdateien/RESULTS.txt](http://zload.file4u.net/ax/nichtaxdateien/RESULTS.txt)

@Hakunka-Matata: Im german, your post is confusing me a bit, but if i got you right you want to know what the extended partition is labled. well you should be able to see yourself :) as you know i already psoted some partition configurations, and the extended partition is /dev/sda4

---

### Post by YesWeCan on 2011-09-06
> **Hakunka-Matata said:**
> [B]W95 Ext'd (LBA), often appears in partition tables, is that a *bad *sign.  
[/B]

And in Linux systems it appears as "**/dev/sda4     140004+ 238474  98471- 100833281    5  Extended**".

**IS **then the W95 Ext'd (LBA) a bad sign in itself?  What partitioner(s) labels the Extended partition (W95 Ext'd (LBA)?

it's one of those "I wonder if xxx"  because so often posters with partition table problems, show the W95 style label???
See: [http://en.wikipedia.org/wiki/Extended_boot_record](http://en.wikipedia.org/wiki/Extended_boot_record)
> The partition type of an extended partition is 0x05 (CHS addressing) or 0x0F (LBA addressing).[3] Linux supports the concept of a second extended partition chain with type 0x85 — this type is hidden (unknown) for other operating systems supporting only one chain.[4]
I think the question is why does linux use type 5 when it should be using F?

---

### Post by Hakunka-Matata on 2011-09-06
Entschuldigen Sie mich, bitte schön.  Ich will nicht, Ihre Arbeit zu unterbrechen.

---

### Post by YesWeCan on 2011-09-06
> **Neutrosider said:**
> thats a long file :) so here it is:
[http://zload.file4u.net/ax/nichtaxdateien/RESULTS.txt](http://zload.file4u.net/ax/nichtaxdateien/RESULTS.txt)

@Hakunka-Matata: Im german, your post is confusing me a bit, but if i got you right you want to know what the extended partition is labled. well you should be able to see yourself :) as you know i already psoted some partition configurations, and the extended partition is /dev/sda4
Ok. You have some problems due to duplicated partition UUIDs:
```
"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/sda1        12B48119B4810109                       ntfs       
/dev/sda10       da1cfbba-3825-4475-b90d-eebabf6e1f1b   ext4       Ubuntu 64 Bit
/dev/sda11       a69a7f3b-1d57-42eb-b5bc-19e6e4334052   ext4       LinuxMint 32 Bit
/dev/sda12       d849006a-3a47-4dce-99fe-939af1fb0089   ext4       LinuxMint 64 Bit
/dev/sda13       E04C4F954C4F64FE                       ntfs       
/dev/sda14       [COLOR="red"]84c74611-da1a-46cc-ac73-1e07c5ad75bf[/COLOR]   ext4       
/dev/sda15       [COLOR="Blue"]35ceab21-4917-4293-a5e5-9c2137028acf[/COLOR]   swap       
/dev/sda2        [COLOR="red"]84c74611-da1a-46cc-ac73-1e07c5ad75bf[/COLOR]   ext4       
/dev/sda3        [COLOR="blue"]35ceab21-4917-4293-a5e5-9c2137028acf[/COLOR]   swap       
/dev/sda5        417C9C2629B0C3C1                       ntfs       7 64bit
/dev/sda6        38D90E303CEAD81A                       ntfs       vista 32bit
/dev/sda7        c1c0e884-a66d-414b-a55d-9b33dec7b6b5   ext4       OPENSuse 32 Bit
/dev/sda8        75996ef3-5c43-434c-95e5-dc2b70f6f924   ext4       OPENSuse 64 Bit
/dev/sda9        a6a860b0-638c-4fbb-8130-844c84e257a0   ext4       Ubuntu 32 Bit
/dev/sdb1        EA94106F9410410D                       ntfs       
/dev/sdc2        67d43861-efac-4df9-888e-a6e41924083e   ext4       
/dev/sdc5        cc5b01fe-95e1-451c-91f7-f1aaf36c8ef2   swap       
/dev/sdc6        A6D9-2768                              vfat       
/dev/sdc7        cddd07aa-35db-40a7-b2d8-c75b6ccd4f6d   ext4  
```

You must have copied/cloned these partitions. They must not have the same UUIDs or Grub and the linux mounter will get confused.

To change the UUID of a linux partition (not Windows),
[COLOR="DarkSlateBlue"]sudo tune2fs -U random /dev/sdxy[/COLOR]

But you need to then change the UUID references in the fstab and the grub.cfg files of the associated OSs.

---

### Post by Neutrosider on 2011-09-06
remeber the picture where i wrote "dont remember where this comes from, looks like another ubuntu"?

these were sda14 and 15. sda 2 and 3 are my original main ubuntu, and sda 14 & 5 are looking like a copy of sda 2 & 3. so 14 & 15 have no right to exist, i have no idea why they exist anyway.

---

### Post by YesWeCan on 2011-09-06
14 & 15 are the same size and type as 2 & 3 and their fstab files are identical so they are very likely exact clones! How did you do this? ;) :P

You might want to keep the clones and delete the 2 & 3 so you free up two primary partitions for Windows installations. Why not change the UUIDs of 2 & 3 and then boot sda (into Ubuntu in sda9) and run
[COLOR="DarkSlateBlue"]sudo update-grub[/COLOR]
to make sure Ubuntu sda14 is in the menu, then reboot into sda14 and check everything looks ok before deleting sda2 and sda3.

You also need to do a lot of "weeding" to get rid of all these swap partition references. As you know, you only need one swap partition on the disk that all linux OSs can share.

```
=============================== sda14/etc/fstab: ===============================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda7 during installation
UUID=84c74611-da1a-46cc-ac73-1e07c5ad75bf /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=35ceab21-4917-4293-a5e5-9c2137028acf none            swap    sw              0       0
# swap was on /dev/sda6 during installation
UUID=45756b58-c6d4-465c-9119-95d35f76bf49 none            swap    sw              0       0
# swap was on /dev/sda8 during installation
UUID=857459d3-a442-48d0-a2a4-c346ec1dcf5d none            swap    sw              0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
--------------------------------------------------------------------------------
```

---

### Post by Neutrosider on 2011-09-06
hmm..
as my partition table works since we fixed the size of the extended partition, and since i have to reinstall most of the systems anyway (luckily my main ubuntu works just fine) i wil delete sda4-sda15 and install one system after another. After every installation i will make the boot test video and delete the system after that. i think im on the safe side doing that^^

at least i learned some things by trying to install 18 operating systems :)

thx for your help, i will take a shower now :)

---

### Post by YesWeCan on 2011-09-06
You're welcome. Hey, you are the OS King!
Don't forget to mark this as solved in [COLOR="Red"]Thread Tools[/COLOR] when you are ready.

---

### Post by Neutrosider on 2011-09-06
ok, is marked as solved :)

ill post the video with the boot time comparison in a couple of days, when im done :)

---

