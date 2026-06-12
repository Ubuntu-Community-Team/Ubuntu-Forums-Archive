---
title: "Problems dual booting"
date: 2008-08-20
forum: Installation &amp; Upgrades
---

### Post by toadi on 2008-08-20
First I had Windows XP installed. With partition magic I created a second partition and installed VISTA.

Now I have intalled ubuntu on the first partition (old XP). I could not see a VISTA line in grub when starting but could mount my vista partition in ubuntu and see my files. But I was unable to boot my vista partition.

I tried Super Grub Loader and the Vista rescue CD(this could not detect VISTA). 

After doing a fdisk -l I saw the windows partition was not bootable so I added the bootable flag. Still I could not boot in windows.

fdisk -l
```


Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x83978397

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1          12       96358+  83  Linux
/dev/sda2   *        5738       14594    71136256    7  HPFS/NTFS
/dev/sda3              13         498     3903795   82  Linux swap / Solaris
/dev/sda4             499        5737    42082267+  83  Linux


```

menu.lst

```

## ## End Default Options ##

title		Ubuntu 8.04.1, kernel 2.6.24-19-generic
root		(hd0,0)
kernel		/vmlinuz-2.6.24-19-generic root=UUID=5c1b9825-75d7-49f4-b589-a0121082a74e ro quiet splash
initrd		/initrd.img-2.6.24-19-generic
quiet

title		Ubuntu 8.04.1, kernel 2.6.24-19-generic (recovery mode)
root		(hd0,0)
kernel		/vmlinuz-2.6.24-19-generic root=UUID=5c1b9825-75d7-49f4-b589-a0121082a74e ro single
initrd		/initrd.img-2.6.24-19-generic

title		Ubuntu 8.04.1, memtest86+
root		(hd0,0)
kernel		/memtest86+.bin
quiet


### END DEBIAN AUTOMAGIC KERNELS LIST

titel		VISTA
rootnotverify	(hd0,1)
makeactive
chainloader	+1


```

---

### Post by manishtech on 2008-08-20
Can you tell what error you encounter when you select Vista option in GRUB listing? I can see that Vista is there in menu.lst.

Does it show error 15 or something else. Did you play around with boot.ini of windows?

---

### Post by toadi on 2008-08-20
When I start normally I don't see the VISTA entry in my grub startup.

So I use the Super Grub Loader CD and try to manually boot:

root (hd0,1)

then it says there is no BOOTMGR

Is this the correct root? Or is something else wrong? I'm starting to doubt myself...

---

### Post by Sef on 2008-08-20
>  Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *                1          12       96358+  83  Linux
/dev/sda2   *          5738       14594    71136256    7  HPFS/NTFS


Windows needs to be on the first paritition.  If I can find a solution that does not involve reinstalling the OSes, I will post it.

---

### Post by manishtech on 2008-08-20
I caught the mistake with the menu.lst file

This is the section for Vista

>  titel             VISTA
rootnotverify   (hd0,1)
makeactive
chainloader     +1

Did you notice some mistake in it?

it should be [COLOR=Red]**title**[/COLOR] not [COLOR=Red]**titel**[/COLOR]


edit the menu.lst file and change the vista part to

>  title             VISTA
 rootnotverify   (hd0,1)
 makeactive
 chainloader     +1


Enjoy! :)

---

### Post by toadi on 2008-08-20
Reinstalling is a option I'm considering :(

But it would be nice if I knew a solution...

---

### Post by manishtech on 2008-08-20
> **Sef said:**
> Windows needs to be on the first paritition.  If I can find a solution that does not involve reinstalling the OSes, I will post it.
AFAIK Windows just needs a primary partition, not sure that it always has to be on the first partition.

GRUB chainloads the windows bootloader, so I dont think that doesnt matter much. Correct me if I am wrong.

---

### Post by toadi on 2008-08-20
Title was wrong off course that explains why I did not see the entry. But I used the suber grub bootloader to bypass this.

Stil it does not work. I know you can remap the drives with: [http://www.gnu.org/software/grub/manual/html_node/map.html](http://www.gnu.org/software/grub/manual/html_node/map.html)

But I can't seem to get it working for my setup:

<CODE>
title              VISTA
root               (hd1,0)
savedefault
makeactive
map                (hd0) (hd1)
map                (hd1) (hd0)
chainloader        +1
</CODE>

Probalby I'm doing it wrong ;)

EDIT: Well it is wrong. this is to map master and slave disks. Not something I need... Still wondering what is wrong :(

---

### Post by manishtech on 2008-08-20
```
title              VISTA
root               (hd1,0)
savedefault
makeactive
map                (hd0) (hd1)
map                (hd1) (hd0)
chainloader        +1
```I dont know what significant can be achieved by remapping drives.

Check this
[http://lifehacker.com/software/troubleshooting/vista-tip--repair-bootmgr-is-missing-error-251733.php](http://lifehacker.com/software/troubleshooting/vista-tip--repair-bootmgr-is-missing-error-251733.php)
for fixing missing BOOTMGR

just make that typo correct in menu.lst, rest all is correct, now problem is in windows bootloader. GRUB is working fine as far as I can understand

---

### Post by toadi on 2008-08-20
Think I will need to reinstall both os. Tried the VISTA rescue CD and it can't find a vista installation to repair. An I'm sure it exists because I can mount it in linux...

---

### Post by sandysandy on 2008-08-20
> **toadi said:**
> When I start normally I don't see the VISTA entry in my grub startup.

So I use the Super Grub Loader CD and try to manually boot:

root (hd0,1)

then it says there is no BOOTMGR

Is this the correct root? Or is something else wrong? I'm starting to doubt myself...

with super grub cd, how are the partitions shown

regards

---

### Post by manishtech on 2008-08-20
> **toadi said:**
> Think I will need to reinstall both os. Tried the VISTA rescue CD and it can't find a vista installation to repair. An I'm sure it exists because I can mount it in linux...
Relax Mate! Don't give up so early....
I think that there is some problems in Vista bootloader, some important system files are corrupted...

---

### Post by toadi on 2008-08-20
Last resort is to destroy the linux partitions and add them to the vista partition and then run VISTA rescue again and hope it will detect the vista installation.

If not reinstall else I just need to reinstall linux...

---

### Post by manishtech on 2008-08-20
> **toadi said:**
> Last resort is to destroy the linux partitions and add them to the vista partition and then run VISTA rescue again and hope it will detect the vista installation.

If not reinstall else I just need to reinstall linux...
Do you think merging partitions and then running rescue has to do anything with **getting vista detected**?

---

### Post by toadi on 2008-08-20
No it doesn't. If it is the BOOTMGR that is missing. Tonight I will download it from my desktop PC (which has same version of VISTA) and copy it to the one on my laptop.

Hopefully this does the trick.

---

### Post by manishtech on 2008-08-20
> **toadi said:**
> No it doesn't. If it is the BOOTMGR that is missing. Tonight I will download it from my desktop PC (which has same version of VISTA) and copy it to the one on my laptop.

Hopefully this does the trick.
This could be a nice trick. Let us know about your progress when done with it.

---

### Post by toadi on 2008-08-20
Well I have exhausted everything.

Tried the VISTA rescue CD and do a 

```
Bootrec /RebuildBCD
```

which gives an error that the volume does not contain a recognized filesystem.

I can dir c:\ 

So I run 

```
chkdsk /f c:
```

which says the filesystem is ok.

I downloaded testdisk which does a segmentation fault when I try the Repair MFT in the advanced menu.

So I'm ready to throw the towel in :(

---

### Post by manishtech on 2008-08-20
Am still unable to understand how Ubuntu is able to corrupt the filesystem of windows when it does not change anything in it during install? 

Experts! Is it possible?

Apart from this, how could it say filesystem is ok and then not recognize it?

---

### Post by toadi on 2008-08-20
Don't think ubuntu did it. It appears Vista is on a logical partition for the moment and that doesn't work very well.

Also it does not have a bootloader I think because it was installed in the XP or MBR part. 

Anyway I'm deleting linux making vista to one big partition and pray this will help me to boot VISTA. 

If not I will need to reinstall both OS'ses. Finally did a backup ;)

---

### Post by manishtech on 2008-08-20
> **toadi said:**
> Don't think ubuntu did it. It appears Vista is on a logical partition for the moment and that doesn't work very well.

Also it does not have a bootloader I think because it was installed in the XP or MBR part. 

Anyway I'm deleting linux making vista to one big partition and pray this will help me to boot VISTA. 

If not I will need to reinstall both OS'ses. Finally did a backup ;)
If you  delete ubuntu, then you could loose stage 2 of GRUB and you couldnt boot any OS. GRUB would show error 17 every time you open your system.

Now if you want to get over this Error 17, then boot from Vista DVD to rescue mode and then type
**fixboot**
followed by
**fixmbr **
and reboot. It will boot directly into Vista provided you can boot from Vista DVD to rescue mode

---

