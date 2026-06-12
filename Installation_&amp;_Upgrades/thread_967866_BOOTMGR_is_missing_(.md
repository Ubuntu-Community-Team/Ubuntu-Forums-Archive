---
title: "BOOTMGR is missing :("
date: 2008-11-02
forum: Installation &amp; Upgrades
---

### Post by Sirron on 2008-11-02
I have three hard disks;

200GB on which Vista is installed

300GB on which Ubuntu is installed in one partition, and another is used for storing music

500GB which is used for storing videos

Originally I had hardy installed. I deleted the ext3 partition, and the swap space. I left the windows partition alone.

I then installed Intrepid in a new partition in the place of the old one.

Unfortunately, although Vista shows up in grub, if I select it I get:

BOOTMGR is missing

and it asks me to restart.

I really, REALLY need vista working, as well as ubuntu (hence the dual boot), so any help would be greatly appreciated.

It's funny; I upgraded in this exact same way from gutsy to hardy and it worked fine...

---

### Post by caljohnsmith on 2008-11-02
How about opening a terminal (applications > accessories > terminal), and posting the output of:
```
sudo fdisk -lu
cat /boot/grub/menu.lst
```
Also, for each of the drives fdisk lists, like sda, sdb, etc, please post the output of:
```
sudo dd if=/dev/[COLOR="Red"]sda[/COLOR] count=1 2>/dev/null | strings | grep -ie grub -ie "missing operating system"
```
So replace "sda" above with each of your drives. And finally, for each command above that returns "GRUB", please post:
```
sudo dd if=/dev/[COLOR="Red"]sda[/COLOR] bs=1 skip=1049 count=2 2>/dev/null | hexdump
```
And replace sda with the drives that previously returned "GRUB". That will greatly clarify what your setup is like.

---

### Post by cdtech on 2008-11-02
If you just want to repair the boot sector for Vista, just download the repair disc from [[COLOR="DarkRed"]here[/COLOR]]("http://neosmart.net/blog/2008/download-windows-vista-x64-recovery-disc/"), burn the iso to disc and reboot with the disc. This will repair the Vista "BOOTMGR is missing" error easier.

Hope this helps........

---

### Post by Sirron on 2008-11-02
Will using that disc mess up grub?

---

### Post by 73ckn797 on 2008-11-02
> **Sirron said:**
> Will using that disc mess up grub?

If you can go into grub via "gksudo gedit /boot/grub/menu.lst" look for 2 lines under the Vista section at the bottom. 

If the lines show (hd0) (hd1) then (hd1) (hd0), delete those lines then save the menu.lst

I was having problems with loading XP through grub after Intrepid install. Once I deleted the 2 lines, XP loads just fine.

---

### Post by Sirron on 2008-11-02
Thanks, but all it says is:

```
# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Windows Vista/Longhorn (loader)
root		(hd0,0)
savedefault
makeactive
chainloader	+1
```

---

### Post by Sirron on 2008-11-02
> **caljohnsmith said:**
> How about opening a terminal (applications > accessories > terminal), and posting the output of:
```
sudo fdisk -lu
cat /boot/grub/menu.lst
```
Also, for each of the drives fdisk lists, like sda, sdb, etc, please post the output of:
```
sudo dd if=/dev/[COLOR="Red"]sda[/COLOR] count=1 2>/dev/null | strings | grep -ie grub -ie "missing operating system"
```
So replace "sda" above with each of your drives. And finally, for each command above that returns "GRUB", please post:
```
sudo dd if=/dev/[COLOR="Red"]sda[/COLOR] bs=1 skip=1049 count=2 2>/dev/null | hexdump
```
And replace sda with the drives that previously returned "GRUB". That will greatly clarify what your setup is like.

Ok, the fdisk one gives:

```
colin@UbuRevelation:~$ sudo fdisk -lu
[sudo] password for colin: 

Disk /dev/sda: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders, total 390721968 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xc9bec9be

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048   390719487   195358720    7  HPFS/NTFS

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x794c0630

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1            2048   976769023   488383488    7  HPFS/NTFS

Disk /dev/sdc: 300.0 GB, 300090728448 bytes
255 heads, 63 sectors/track, 36483 cylinders, total 586114704 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x00000001

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *        2048   293177343   146587648    7  HPFS/NTFS
/dev/sdc2       293186250   586099394   146456572+   5  Extended
/dev/sdc5       293186313   574114904   140464296   83  Linux
/dev/sdc6       574114968   586099394     5992213+  82  Linux swap / Solaris
colin@UbuRevelation:~$ cat /boot/grub/menu.lst
# menu.lst - See: grub(8), info grub, update-grub(8)
#            grub-install(8), grub-floppy(8),
#            grub-md5-crypt, /usr/share/doc/grub
#            and /usr/share/doc/grub-doc/.

## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not use 'savedefault' or your
# array will desync and will not let you boot your system.
default		0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout		10

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
#hiddenmenu

# Pretty colours
#color cyan/blue white/blue

## password ['--md5'] passwd
# If used in the first section of a menu file, disable all interactive editing
# control (menu entry editor and command-line)  and entries protected by the
# command 'lock'
# e.g. password topsecret
## password --md5 $1$gLhU0/$aW78kHK1QfV3P2b2znUoe/
# password topsecret

#
# examples
#
# title		Windows 95/98/NT/2000
# root		(hd0,0)
# makeactive
# chainloader	+1
#
# title		Linux
# root		(hd0,1)
# kernel	/vmlinuz root=/dev/hda2 ro
#

#
# Put static boot stanzas before and/or after AUTOMAGIC KERNEL LIST

### BEGIN AUTOMAGIC KERNELS LIST
## lines between the AUTOMAGIC KERNELS LIST markers will be modified
## by the debian update-grub script except for the default options below

## DO NOT UNCOMMENT THEM, Just edit them to your needs

## ## Start Default Options ##
## default kernel options
## default kernel options for automagic boot options
## If you want special options for specific kernels use kopt_x_y_z
## where x.y.z is kernel version. Minor versions can be omitted.
## e.g. kopt=root=/dev/hda1 ro
##      kopt_2_6_8=root=/dev/hdc1 ro
##      kopt_2_6_8_2_686=root=/dev/hdc2 ro
# kopt=root=UUID=306e681d-f6a3-4c3c-84d2-7dab09894496 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=306e681d-f6a3-4c3c-84d2-7dab09894496

## should update-grub create alternative automagic boot options
## e.g. alternative=true
##      alternative=false
# alternative=true

## should update-grub lock alternative automagic boot options
## e.g. lockalternative=true
##      lockalternative=false
# lockalternative=false

## additional options to use with the default boot option, but not with the
## alternatives
## e.g. defoptions=vga=791 resume=/dev/hda5
# defoptions=quiet splash

## should update-grub lock old automagic boot options
## e.g. lockold=false
##      lockold=true
# lockold=false

## Xen hypervisor options to use with the default Xen boot option
# xenhopt=

## Xen Linux kernel options to use with the default Xen boot option
# xenkopt=console=tty0

## altoption boot targets option
## multiple altoptions lines are allowed
## e.g. altoptions=(extra menu suffix) extra boot options
##      altoptions=(recovery) single
# altoptions=(recovery mode) single

## controls how many kernels should be put into the menu.lst
## only counts the first occurence of a kernel, not the
## alternative kernel options
## e.g. howmany=all
##      howmany=7
# howmany=all

## should update-grub create memtest86 boot option
## e.g. memtest86=true
##      memtest86=false
# memtest86=true

## should update-grub adjust the value of the default booted system
## can be true or false
# updatedefaultentry=false

## should update-grub add savedefault to the default options
## can be true or false
# savedefault=false

## ## End Default Options ##

title		Ubuntu 8.10, kernel 2.6.27-7-generic
uuid		306e681d-f6a3-4c3c-84d2-7dab09894496
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=306e681d-f6a3-4c3c-84d2-7dab09894496 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-7-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
uuid		306e681d-f6a3-4c3c-84d2-7dab09894496
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=306e681d-f6a3-4c3c-84d2-7dab09894496 ro  single
initrd		/boot/initrd.img-2.6.27-7-generic

title		Ubuntu 8.10, memtest86+
uuid		306e681d-f6a3-4c3c-84d2-7dab09894496
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Windows Vista/Longhorn (loader)
root		(hd0,0)
savedefault
makeactive
chainloader	+1
```

and the other one gives:

```
colin@UbuRevelation:~$ sudo dd if=/dev/sda count=1 2>/dev/null | strings | grep -ie grub -ie "missing operating system"
GRUB
colin@UbuRevelation:~$ sudo dd if=/dev/sda bs=1 skip=1049 count=2 2>/dev/null | hexdump
0000000 8204                                   
0000002
colin@UbuRevelation:~$ sudo dd if=/dev/sdb count=1 2>/dev/null | strings | grep -ie grub -ie "missing operating system"
Missing operating system
colin@UbuRevelation:~$ sudo dd if=/dev/sdc count=1 2>/dev/null | strings | grep -ie grub -ie "missing operating system"
GRUB 
colin@UbuRevelation:~$ sudo dd if=/dev/sdc bs=1 skip=1049 count=2 2>/dev/null | hexdump
0000000 ff04                                   
0000002
```

I hope that's good ^^, thanks for the help so far, this is encouraging

---

### Post by caljohnsmith on 2008-11-02
According to those commands, you have Grub installed into the MBR (Master Boot Record) of both your sda and sdc drives. It looks like you are booting from the sdc drive, which would be ideal. If you are booting from the sdc drive, then one of the following entries should work to boot Windows:
```
title	   Windows Vista (hd1)
root       (hd1,0)
map        (hd0) (hd1)
map        (hd1) (hd0)
chainloader +1

title	   Windows Vista (hd2)
root       (hd2,0)
map        (hd0) (hd2)
map        (hd2) (hd0)
chainloader +1
```
You can add the entries to the end of your menu.lst with:
```
gksudo gedit /boot/grub/menu.lst
```
Give it a shot and let me know how it goes. :)

---

### Post by 73ckn797 on 2008-11-02
> **caljohnsmith said:**
> According to those commands, you have Grub installed into the MBR (Master Boot Record) of both your sda and sdc drives. It looks like you are booting from the sdc drive, which would be ideal. If you are booting from the sdc drive, then one of the following entries should work to boot Windows:
```
title       Windows Vista (hd1)
root       (hd1,0)
map        (hd0) (hd1)
map        (hd1) (hd0)
chainloader +1

title       Windows Vista (hd2)
root       (hd2,0)
map        (hd0) (hd2)
map        (hd2) (hd0)
chainloader +1
```You can add the entries to the end of your menu.lst with:
```
gksudo gedit /boot/grub/menu.lst
```Give it a shot and let me know how it goes. :)

I made the suggestion to delete the map drives. That fixed my problem but, then again, my system set up is different. I have partitioned the hd0 for XP and Ubuntu.

---

### Post by caljohnsmith on 2008-11-02
> **73ckn797 said:**
> I made the suggestion to delete the map drives. That fixed my problem but, then again, my system set up is different. [COLOR="Blue"]I have partitioned the hd0 for XP and Ubuntu.[/COLOR]
If Windows is on the same drive as Ubuntu, and that is the drive you are booting from on start up, then you are absolutely right about not needing the mapping lines. But it is usually necessary to include those mapping lines if Windows is on a different drive than the drive you are booting from. :)

---

### Post by Sirron on 2008-11-02
```
title	   Windows Vista (hd1)
root       (hd1,0)
map        (hd0) (hd1)
map        (hd1) (hd0)
chainloader +1

```

Works perfectly, thanks very much! 

It's safe to remove the other option, since this one works, right?

---

### Post by caljohnsmith on 2008-11-02
> **Sirron said:**
> 
Works perfectly, thanks very much! 

It's safe to remove the other option, since this one works, right?
Yes, by all means delete the other entry; glad you can boot Vista now. Cheers and have fun. :)

---

### Post by jokerinux on 2008-11-03
caljohnsmith can you help me too?

this is my data:

i have 3 HD 1 Sata with many many partitions (with xp vista and kubuntu)
and 2 raid IDE..

i've istalled my SO in this order XP VISTA KUBUNTU, and grub returns me "bootmgr is missing" when i try to star VISTA LOADER.

this is my sudo fdisk -lu

```
Disco /dev/sda: 320.0 GB, 320072933376 byte
255 testine, 63 settori/tracce, 38913 cilindri, totale 625142448 settori
Unità = settori di 1 * 512 = 512 byte
Identificativo disco: 0x10251025

Dispositivo Boot      Start         End      Blocks   Id  System
/dev/sda1              63    83891429    41945683+   7  HPFS/NTFS
/dev/sda2   *    83891436   178273304    47190934+   7  HPFS/NTFS
/dev/sda3       178273305   625137344   223432020    5  Esteso
/dev/sda5       274743636   403681319    64468842    7  HPFS/NTFS
/dev/sda6       403681383   424164194    10241406    7  HPFS/NTFS
/dev/sda7       424164258   434397599     5116671    7  HPFS/NTFS
/dev/sda8       434397663   444920174     5261256    7  HPFS/NTFS
/dev/sda9       444920238   457209899     6144831    7  HPFS/NTFS
/dev/sda10      457209963   510465374    26627706    7  HPFS/NTFS
/dev/sda11      510465438   625137344    57335953+   7  HPFS/NTFS
/dev/sda12      178273431   197808344     9767457   83  Linux
/dev/sda13      197808408   227110904    14651248+  83  Linux
/dev/sda14      227110968   229070834      979933+  82  Linux swap / Solaris

Le voci nella tabella delle partizioni non sono nello stesso ordine del disco

Disco /dev/sdb: 163.9 GB, 163928604672 byte
255 testine, 63 settori/tracce, 19929 cilindri, totale 320173056 settori
Unità = settori di 1 * 512 = 512 byte
Identificativo disco: 0x10ad10ad

Dispositivo Boot      Start         End      Blocks   Id  System
/dev/sdb1   *          63   320159384   160079661    7  HPFS/NTFS

Disco /dev/sdc: 122.9 GB, 122942324736 byte
255 testine, 63 settori/tracce, 14946 cilindri, totale 240121728 settori
Unità = settori di 1 * 512 = 512 byte
Identificativo disco: 0x0544287c

Dispositivo Boot      Start         End      Blocks   Id  System
/dev/sdc1   *          63   240107489   120053713+   7  HPFS/NTFS

```

and this is my cat /boot/grub/menu.lst
```
default 0                                                        
timeout 10                                                       

### BEGIN AUTOMAGIC KERNELS LIST
## lines between the AUTOMAGIC KERNELS LIST markers will be modified
## by the debian update-grub script except for the default options below

## DO NOT UNCOMMENT THEM, Just edit them to your needs

## ## Start Default Options ##
## default kernel options     
## default kernel options for automagic boot options
## If you want special options for specific kernels use kopt_x_y_z
## where x.y.z is kernel version. Minor versions can be omitted.  
## e.g. kopt=root=/dev/hda1 ro                                    
##      kopt_2_6_8=root=/dev/hdc1 ro                              
##      kopt_2_6_8_2_686=root=/dev/hdc2 ro                        
# kopt=root=UUID=1d66c058-4a2a-4d4d-aa8b-cd381a5914fc ro xforcevesa

## default grub root device
## e.g. groot=(hd0,0)      
# groot=1d66c058-4a2a-4d4d-aa8b-cd381a5914fc

## should update-grub create alternative automagic boot options
## e.g. alternative=true                                       
##      alternative=false                                      
# alternative=true                                             

## should update-grub lock alternative automagic boot options
## e.g. lockalternative=true                                 
##      lockalternative=false                                
# lockalternative=false                                      

## additional options to use with the default boot option, but not with the
## alternatives                                                            
## e.g. defoptions=vga=791 resume=/dev/hda5                                
# defoptions=quiet splash                                                  

## should update-grub lock old automagic boot options
## e.g. lockold=false                                


##      lockold=true                                 
# lockold=false                                      

## Xen hypervisor options to use with the default Xen boot option
# xenhopt=                                                       

## Xen Linux kernel options to use with the default Xen boot option
# xenkopt=console=tty0                                             

## altoption boot targets option
## multiple altoptions lines are allowed
## e.g. altoptions=(extra menu suffix) extra boot options
##      altoptions=(recovery) single                     
# altoptions=(recovery mode) single                      

## controls how many kernels should be put into the menu.lst
## only counts the first occurence of a kernel, not the     
## alternative kernel options                               
## e.g. howmany=all                                         
##      howmany=7                                           
# howmany=all                                               

## should update-grub create memtest86 boot option
## e.g. memtest86=true                            
##      memtest86=false                           
# memtest86=true                                  

## should update-grub adjust the value of the default booted system
## can be true or false
# updatedefaultentry=false

## should update-grub add savedefault to the default options
## can be true or false
# savedefault=false

## ## End Default Options ##

title Ubuntu 8.10, kernel 2.6.27-7-generic
kernel /boot/vmlinuz-2.6.27-7-generic root=UUID=1d66c058-4a2a-4d4d-aa8b-cd381a5914fc ro xforcevesa quiet splash
initrd /boot/initrd.img-2.6.27-7-generic

title Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
kernel /boot/vmlinuz-2.6.27-7-generic root=UUID=1d66c058-4a2a-4d4d-aa8b-cd381a5914fc ro xforcevesa  single
initrd /boot/initrd.img-2.6.27-7-generic

title Ubuntu 8.10, memtest86+
kernel /boot/memtest86+.bin

### END DEBIAN AUTOMAGIC KERNELS LIST

title Other operating systems:
root

title Windows Vista/Longhorn (loader)
root (hd0,1)
map (hd0) (hd2)
map (hd2) (hd0)
chainloader +1
savedefault
makeactive


```

and finally

```
marco@Soggiorno:~$ sudo dd if=/dev/sda count=1 2>/dev/null | strings | grep -iegrub -ie "missing operating system"
GRUB
marco@Soggiorno:~$ sudo dd if=/dev/sda bs=1 skip=1049 count=2 2>/dev/null | hexdump
0000000 ff0b
0000002
marco@Soggiorno:~$ sudo dd if=/dev/sdb count=1 2>/dev/null | strings | grep -iegrub -ie "missing operating system"
GRUB
GRUB
marco@Soggiorno:~$ sudo dd if=/dev/sdb bs=1 skip=1049 count=2 2>/dev/null | hexdump
0000000 820b
0000002
marco@Soggiorno:~$ sudo dd if=/dev/sdc count=1 2>/dev/null | strings | grep -iegrub -ie "missing operating system"
Missing operating system
GRUB
marco@Soggiorno:~$ sudo dd if=/dev/sdc bs=1 skip=1049 count=2 2>/dev/null | hexdump
0000000 ff00
0000002
```

thank you so much!

---

### Post by caljohnsmith on 2008-11-03
Jokerinux, are you booting off the sda drive on start up? If you are, first open your menu.lst with:
```
kdesu kate /boot/grub/menu.lst
```
And then replace your existing Vista entry with the following two entries at the bottom of menu.lst:
```
title	   Windows Vista (hd1)
root       (hd1,0)
map        (hd0) (hd1)
map        (hd1) (hd0)
chainloader +1

title	   Windows Vista (hd2)
root       (hd2,0)
map        (hd0) (hd2)
map        (hd2) (hd0)
chainloader +1
```
Reboot, try each one, and if neither work, then at the Grub menu press "c" to get the command line, and type:
```
grub> find /boot/grub/stage1
```
And let me know what that returns. Otherwise let me know how it goes. :)

---

### Post by jokerinux on 2008-11-03
> Jokerinux, are you booting off the sda drive on start up? If you are, first open your menu.lst with:

mmm this questions means : which HD is the first on the bootlist of Bios the asnwer is no..the first is sdc..my sata disk!

and then: i tried all the 2 solution and nothing..

the command : find /boot/grub/stage1 aswered me (hd0,11)

thank you

---

### Post by caljohnsmith on 2008-11-03
> **jokerinux said:**
> mmm this questions means : which HD is the first on the bootlist of Bios the asnwer is no..the first is sdc..my sata disk!

and then: i tried all the 2 solution and nothing..

the command : find /boot/grub/stage1 aswered me (hd0,11)

thank you
Something doesn't seem right, because if that Grub find command returned (hd0,11), that would mean sda is the first in the BIOS boot order. You did run that find command from the Grub command line on start up, and not from your Kubuntu install? Also, I misunderstood your first post: which partition is Vista and XP on? Is XP on sda1 and Vista on sda2?

---

### Post by jokerinux on 2008-11-03
i run find command after pressing "c" on boot...

and that is my hd configuration:

i have 3 hd, one sata (sdc) connected directy to the MB and then 2 IDE connected through a raid controller.

In the bios the boot option is: 1st dvd 2nd dvd and then sata HD (sdc) when are present all the partition of the OS. 

sdc1 XP sdc2 VISTA sda12 ROOT sda13 HOME

sda and sdb are two HD used only for data...

thank you so much for helping me.. i love kde4 and appreciate kubuntu..but sometime i need also a M$ SO (for 100% with doc for my thesis for the graduation..) and i cannot restore every time the windows mbr..
thank you

---

### Post by caljohnsmith on 2008-11-03
[QUOTE=jokerinux]sdc1 XP sdc2 VISTA sda12 ROOT sda13 HOME[/QUOTE]
If you look at the fdisk output from your post #13, it shows all those partitions above on the 320 GB sda drive, not sdc. Your fdisk output shows the 123 GB sdc drive as having only one NTFS partition. 

Anyway, if you can pull up your menu.lst again, how about adding the following entries at the end for XP and Vista:
```
title Windows XP/Vista
root (hd0,0)
chainloader +1

title Windows Vista partition
root (hd0,1)
chainloader +1
```
But a word of caution: most likely what happened when you installed Vista after XP is that Vista put its boot files in the XP partition and took over the boot process. That means when you select the "Windows XP/Vista" entry above, you will most likely get the Windows Vista boot screen where you can choose Vista or XP. And choosing the "Windows Vista partition" entry will probably give you a "bootmgr" missing error. Try the above entries though and let me know exactly what happens when you try each of them from the Grub menu.

---

### Post by jokerinux on 2008-11-03
it works!

Thank you very very very very much!

As you notice with the second choose i have the same bootmgr error, but with the first one i finally see the Vista bootloader!

thank you!

---

### Post by caljohnsmith on 2008-11-03
That's great news it worked. Cheers and have fun. :)

---

### Post by 73ckn797 on 2008-11-03
> **caljohnsmith said:**
> If Windows is on the same drive as Ubuntu, and that is the drive you are booting from on start up, then you are absolutely right about not needing the mapping lines. But it is usually necessary to include those mapping lines if Windows is on a different drive than the drive you are booting from. :)

The mapping lines were what Intrepid entered during installation. When XP would not boot after Intrepid install and Super Grub did not help, I deleted the lines and fixed the problem. More of a noob process of elimination.

---

### Post by ukblacknight on 2008-11-07
Hi guys,

I'm getting this "BOOTMGR is missing" error.  I've tried to follow the instructions on this thread and kind of got half way, I'm now getting Error 13: Invalid or unsupported executable format."

fdisk -lu
```

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x082a3b4a

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1            2048   320608255   160303104    7  HPFS/NTFS
/dev/sda2       320609205   322601264      996030   82  Linux swap / Solaris
/dev/sda3       322601265   342730709    10064722+  83  Linux
/dev/sda4   *   342730710   488392064    72830677+  83  Linux

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x000f114b

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *          63   976768064   488384001    7  HPFS/NTFS

Disk /dev/sdc: 123.5 GB, 123522416640 bytes
255 heads, 63 sectors/track, 15017 cylinders, total 241254720 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x9c3ebc67

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *          63   241248104   120624021    7  HPFS/NTFS

Disk /dev/sdd: 8086 MB, 8086617600 bytes
255 heads, 63 sectors/track, 983 cylinders, total 15794175 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1              44    15679439     7839698    b  W95 FAT32


```

menu.lst file (excluding the stuff from the top)
```

title		Ubuntu 8.10, kernel 2.6.27-7-generic
uuid		202aa0c6-349f-45a0-8acb-2156b695a907
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=202aa0c6-349f-45a0-8acb-2156b695a907 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-7-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
uuid		202aa0c6-349f-45a0-8acb-2156b695a907
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=202aa0c6-349f-45a0-8acb-2156b695a907 ro  single
initrd		/boot/initrd.img-2.6.27-7-generic

title		Ubuntu 8.10, memtest86+
uuid		202aa0c6-349f-45a0-8acb-2156b695a907
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdc1
title	   	Windows Vista (hd1)
root       	(hd1,3)
map        	(hd0) (hd1)
map        	(hd1) (hd0)
chainloader 	+1


title		Windows Vista (hd2)
root		(hd1,3)
savedefault
makeactive
map		(hd0) (hd2)
map		(hd2) (hd0)
chainloader	+1


```

grub> find /boot/grub/stage1
```

hd(1,3)

```

The Vista partition is on sda1, which is a SATA drive.  The boot drive is sdc1, which is an PATA drive.  It worked fine before the update.  Not sure which numbers to put into the menu.lst file!!

Hope someone can help :)

Cheers in advance. :)

---

### Post by caljohnsmith on 2008-11-07
Ukblacknight, so I'm curious, why are booting off the sdc drive when your Linux drive is sda? So you are saying that Grub is in the MBR of sdc?

How about trying the following entries for Vista:
```
title Windows Vista (hd0)
root (hd0,0)
chainloader +1

title Windows Vista (hd1)
root (hd1,0)
map        (hd0) (hd1)
map        (hd1) (hd0)
chainloader +1

title Windows Vista (hd2)
root (hd2,0)
map        (hd0) (hd2)
map        (hd2) (hd0)
chainloader +1

title Windows Vista (hd3)
root (hd3,0)
map        (hd0) (hd3)
map        (hd3) (hd0)
chainloader +1
```
One of those entries should work to boot Vista. If not, let me know exactly what happens when you choose each one from the Grub menu. :)

---

### Post by ukblacknight on 2008-11-07
I know it's a strange configuration, but that's the only way my motherboard will allow it.  The PATA drive has to be the first boot drive, otherwise Vista or Ubuntu wouldn't install, the SATA drives wouldn't even be visible! So, the MBR HAD to go on there... which makes life that little bit more difficult!

The first option worked!!! Thank you so much, I can get back on Battlefield 2 and CoD4 now :)

Such a simple solution too... I feel like such a n00b :)

---

### Post by caljohnsmith on 2008-11-07
> **ukblacknight said:**
> I know it's a strange configuration, but that's the only way my motherboard will allow it.  The PATA drive has to be the first boot drive, otherwise Vista or Ubuntu wouldn't install, the SATA drives wouldn't even be visible! So, the MBR HAD to go on there... which makes life that little bit more difficult!

The first option worked!!! Thank you so much, I can get back on Battlefield 2 and CoD4 now :)

Such a simple solution too... I feel like such a n00b :)
I'm glad it worked and that it turned out to be a simple problem. Cheers and have fun on the battlefield. :)

---

