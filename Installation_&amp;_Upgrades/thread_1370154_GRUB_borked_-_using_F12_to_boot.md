---
title: "GRUB borked - using F12 to boot"
date: 2010-01-01
forum: Installation &amp; Upgrades
---

### Post by natgab on 2010-01-01
I'm having trouble with my GRUB,
 
I have Ubuntu 9.04 with 3 internal HDs. 160GB w/ Ubuntu 9.04, 80GB blank, and 10GB w/ Haiku RC1.  Let me explain what I did and what is happening:

I had computer working fine with the 160GB & 80GB HDs. I added the 10GB HD for Haiku. After I added the 10GB HD, I got a "Verifying DMI pool data" error and after reading found that it meant the new HD was not recognized.  So I adjusted BIOS to get it recognized again. I booted off Ubuntu live and all three HD were recognized. I then booted Haiku CD and installed it on the 10GB.

Note, I had not yet tried to adjust GRUB yet to make it dual-boot.  I just tried to reboot to my Ubuntu HD to make sure things worked, but when it gets to GRUB on boot it only shows ```
GRUB  GRUB
``` I have to reboot and press F12 and get the boot menu that lets me choose HD from first list and then lets me choose the 160GB HD from the list of my 3 HDs. Once I get that, computer boots normal to Ubuntu 9.04

This is what I get from grub menu.lst:
```
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
default         0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).

```  I could not figure out what other information to post, if someone can let me know, hopefully I can provide more information to fix my GRUB problem. TIA

---

### Post by raymondh on 2010-01-02
>  So I adjusted BIOS to get it recognized again. I booted off Ubuntu live and all three HD were recognized. I then booted Haiku CD and installed it on the 10GB.

Where did you install the bootloader of haiku? in the MBR of the hd set to boot first in BIOS, which I assume is the 160gb?  Or, in the MBR (or partition) of the 10gb?  

Have you tried to re-install grub-legacy and then chainload haikuRC to it?

---

### Post by Moozillaaa on 2010-01-02
> I booted off [COLOR=DarkGreen]Ubuntu live[/COLOR] and all three HD were recognized. I then booted [COLOR=Red]Haiku CD[/COLOR] and installed it on the 10GB.

Between [COLOR=DarkGreen]Ubuntu live[/COLOR], and then [COLOR=Red]Haiku CD[/COLOR], did you boot Ubuntu from hard disk, and format the 10G?

Is Ubuntu GRUB loader still the default bootloader? If so, boot up Ubuntu, and post fdisk -l contents from command line terminal...

---

### Post by natgab on 2010-01-02
raymondh-- I had not yet installed the boot loader for Haiku.  The intructions tell me to add it to my Grub.  And yes, the 160GB is supposed to be first (main OS).  

When I booted with F12, after I chose my 160GB HD in the boot menu it will show ```
Grub stage 1.5
``` and then do a normal boot to the Ubuntu log-in.  I have not yet done anything so as not to make things worse. :P

Moozila-- I booted the **Ubuntu live disc** to give the 10GB HD a MSDOS partion table and then format to ext3 because it did not install when I left it as empty.

I then rebooted to **Haiku live disc** and used the installer to format 10GB HD as BFS (Be file system) and install Haiku.  Instructions say that HD is bootable, but needs to be added to Grub or another boot loader.

Here is fdisk -l contents:

```
jaleman@bebox:~$ sudo fdisk -l

Disk /dev/sda: 10.2 GB, 10242957312 bytes
255 heads, 63 sectors/track, 1245 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0006bce6

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        1245    10000431   83  Linux

Disk /dev/sdb: 81.9 GB, 81964302336 bytes
255 heads, 63 sectors/track, 9964 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System

Disk /dev/sdc: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000ed385

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1       18716   150336238+  83  Linux
/dev/sdc2           18717       19457     5952082+   5  Extended
/dev/sdc5           18717       19457     5952051   82  Linux swap / Solaris 

```
One more thing, if its too much trouble I am ok with Haiku being wiped. I do have it running ok on Virutal Box.

---

### Post by raymondh on 2010-01-02
> **natgab said:**
> raymondh-- I had not yet installed the boot loader for Haiku.  The intructions tell me to add it to my Grub.  And yes, the 160GB is supposed to be first (main OS).  

When I booted with F12, after I chose my 160GB HD in the boot menu it will show ```
Grub stage 1.5
``` and then do a normal boot to the Ubuntu log-in.  I have not yet done anything so as not to make things worse. :P

Moozila-- I booted the **Ubuntu live disc** to give the 10GB HD a MSDOS partion table and then format to ext3 because it did not install when I left it as empty.

I then rebooted to **Haiku live disc** and used the installer to format 10GB HD as BFS (Be file system) and install Haiku.  Instructions say that HD is bootable, but needs to be added to Grub or another boot loader.

Here is fdisk -l contents:

```
jaleman@bebox:~$ sudo fdisk -l

Disk /dev/sda: 10.2 GB, 10242957312 bytes
255 heads, 63 sectors/track, 1245 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0006bce6

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        1245    10000431   83  Linux

Disk /dev/sdb: 81.9 GB, 81964302336 bytes
255 heads, 63 sectors/track, 9964 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System

Disk /dev/sdc: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000ed385

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1       18716   150336238+  83  Linux
/dev/sdc2           18717       19457     5952082+   5  Extended
/dev/sdc5           18717       19457     5952051   82  Linux swap / Solaris 

```
One more thing, if its too much trouble I am ok with Haiku being wiped. I do have it running ok on Virutal Box.

After tinkering around in BIOS to have sdc 'recognized' ... have you tried to set sdc as first to boot in BIOS and then re-install grub legacy?  If so, did you encounter the same "not recognized" error for sda?

For chainloading (am curious as well for the BFS filesystem).. [here's a reference from Herman]("http://members.iinet.net.au/~herman546/p15.html#2._Chainloader").

Regards,

Raymond

---

### Post by natgab on 2010-01-03
> **raymondh said:**
> After tinkering around in BIOS to have sdc 'recognized' ... have you tried to set sdc as first to boot in BIOS and then re-install grub legacy?  If so, did you encounter the same "not recognized" error for sda?

For chainloading (am curious as well for the BFS filesystem).. [here's a reference from Herman]("http://members.iinet.net.au/~herman546/p15.html#2._Chainloader").

Regards,

Raymond

--Raymond,

I tried again editing the BIOS, and this time it seems to have accepted my 160GB Ubuntu Studio 9.04 as startup again.  

I previously had in Hard Disk boot priority:**10GB first, 80GB second and 160GB third with add-in cards last**
But if everything is working right, shouldn't the system just work its way down untill it reaches a bootable system?

Anyway, I went and changed to: **160GB first, 80GB second and 10GB third with add-in cards last** and it rebooted normal again.  I also rebooted again and checked my Grub list. Currently it just show several version of ubuntu 9.04, regular, safemode, realtime kernel, memtest.

Thanks for the tip on the grub page.  I will reread it and ask over at the Haiku forums to see who is dual-booting with Linux.  Obviously if I get it working I will write up a tutorial for both forums. :lolflag:

---

### Post by raymondh on 2010-01-03
> **natgab said:**
> --Raymond,

I tried again editing the BIOS, and this time it seems to have accepted my 160GB Ubuntu Studio 9.04 as startup again.  

I previously had in Hard Disk boot priority:**10GB first, 80GB second and 160GB third with add-in cards last**
But if everything is working right, shouldn't the system just work its way down untill it reaches a bootable system?


[COLOR="Navy"]TRUE, if you only have one OS[/COLOR]


Anyway, I went and changed to: **160GB first, 80GB second and 10GB third with add-in cards last** and it rebooted normal again.  I also rebooted again and checked my Grub list. Currently it just show several version of ubuntu 9.04, regular, safemode, realtime kernel, memtest.

Thanks for the tip on the grub page.  I will reread it and ask over at the Haiku forums to see who is dual-booting with Linux.  Obviously if I get it working I will write up a tutorial for both forums. :lolflag:

Glad you have it working.  Remember that the MBR of the HD that is set to boot first in BIOS will always be 'dominant' (/boot not withstanding).  That said, if GRUB is installed in that MBR, it will be in control and pass on the booting to the appropriate areas. 

 As an example, I am 3-booting, one of them being OSX. Grub is installed in the MBR of the HD.  OSX' bootloader (darwin) is installed in the OSX partition.... and said partition is chainloaded in grub.  So, upon start-up, GRUB is in command.  When I choose OSX, it then segues to darwin and thus loads OSX.

Happy ubuntu-ing.

---

### Post by natgab on 2010-01-03
> **raymondh said:**
> Glad you have it working.  Remember that the MBR of the HD that is set to boot first in BIOS will always be 'dominant' (/boot not withstanding).  That said, if GRUB is installed in that MBR, it will be in control and pass on the booting to the appropriate areas. 

 As an example, I am 3-booting, one of them being OSX. Grub is installed in the MBR of the HD.  OSX' bootloader (darwin) is installed in the OSX partition.... and said partition is chainloaded in grub.  So, upon start-up, GRUB is in command.  When I choose OSX, it then segues to darwin and thus loads OSX.

Happy ubuntu-ing.

---Yeah, I kinda figured it out when I started reading on the grub page. At least the part of one bootloader (grub) passing off to the other bootloader. I will read up and double check how to properly install Be on the other HD before tinkering again!

P.S. Loved the link on the grub page to the guy loading 100 OS on his computer.

---

### Post by natgab on 2010-01-04
--Raymondh,

I got the computer to dualboot Ubuntu Studio 9.04 and Haiku. Thanks to the grub info you posted and some rereading of the Haiku install instructions I got the set-up working fine.

Here is the link:

[http://ubuntuforums.org/showthread.php?t=179902&page=28](http://ubuntuforums.org/showthread.php?t=179902&page=28)

---

