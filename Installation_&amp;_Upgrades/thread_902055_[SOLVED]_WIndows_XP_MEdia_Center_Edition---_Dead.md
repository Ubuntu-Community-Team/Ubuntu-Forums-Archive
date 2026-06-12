---
title: "[SOLVED] WIndows XP MEdia Center Edition--- Dead???"
date: 2008-08-26
forum: Installation &amp; Upgrades
---

### Post by metaleroheaded on 2008-08-26
Ok today I decided to turn my HP Pavillion SLimline into a multi OS machine... It came with Windows XP Media Center Edition 2005... I Installed Ubuntu 8.04 and everything seemed fine...Until I tried to access windows (Oh I miss Guitar Pro 5!!!) and the GRUB lead me to a screen that says "Starting UP..." but It will stay that for hours... Is there any way to make Windows work again??? By the way, every single file is alright, I checked my music in Linux and more than 20 GB are working just fine so I don't know where the problem is.. Can you help me?
PS Sorry about my english I'm a spanish native speaker but the spanish forum is not working... lol

---

### Post by Sef on 2008-08-27
With the Live CD:

System > Applications > Terminal

Copy and paste or type in this code:

```
sudo fdisk -l
``` Small L

Copy and paste the results here.

---

### Post by metaleroheaded on 2008-08-27
Disco /dev/sda: 250.0 GB, 250059350016 bytes
255 cabezas, 63 sectores/pista, 30401 cilindros
Unidades = cilindros de 16065 * 512 = 8225280 bytes
Identificador de disco: 0xcab10bee

Disposit. Inicio    Comienzo      Fin      Bloques  Id  Sistema
/dev/sda1   *           1       23778   190996753+   7  HPFS/NTFS
/dev/sda2           29286       30401     8958600    c  W95 FAT32 (LBA)
La partición 2 no termina en un límite de cilindro.
/dev/sda3           23779       29006    41993910   83  Linux
/dev/sda4           29007       29285     2241067+  82  Linux swap / Solaris

I'm sorry it's in spanish ....

---

### Post by metaleroheaded on 2008-08-28
OK... I did something really stupid (or wise I don't know yet...)
I did a PC Recovery from HP Recovery partition... It set Widnows back to when I buy my PC... Now Linux won't load...
I set the Live CD and everything seemed normal, there was a Partition (43.3GB) that belongs to Linux and the other one that is Windows... How can I set the GRUB again??? is that difficult? Will I have to reinstalkl Linux Ubuntu again???
Hel please I need this working as soon as possible

---

### Post by Cresho on 2008-08-28
you totally hosed your system.  First off, you do not own windows; they own you.  secondly, you do not own a valid windows operating system.  Thirdly, you will need to buy a windows cd to fix your hardrive issue.

You can restore your partition with the ubuntu cd you created.  Just hose all partitions and create a blank one.  Make sure you do not hose your windows media center partition for restoration.

---

### Post by Bakon Jarser on 2008-08-28
> **Cresho said:**
> you totally hosed your system.  First off, you do not own windows; they own you.  secondly, you do not own a valid windows operating system.  Thirdly, you will need to buy a windows cd to fix your hardrive issue.

You can restore your partition with the ubuntu cd you created.  Just hose all partitions and create a blank one.  Make sure you do not hose your windows media center partition for restoration.

You seem to have no idea what you are talking about.  He seems to have a legitimate copy of windows that came with his pc and it seems that he got windows working again.  It probably overwrote all the data on the disk and ubuntu will probably have to be installed again.  Hard to tell exactly what's going on though.

---

### Post by Cresho on 2008-08-28
HERE!  read this and apoligize
[http://www.hardforum.com/archive/index.php/t-921659.html](http://www.hardforum.com/archive/index.php/t-921659.html)
JESUS~!

Even this guy knows what I'm talking about...he stated this in the link provided

Dan_D
07-01-2005, 02:07 PM
HP's don't come with any software disks for the OS. Not unless its really old. You access the recovery partition by pressing F10 at the POST screen. It guides you through the rest. You need to choose the "advanced" tab in order to tell the system to format the drive. That way you get a clean install. The recovery is basically a disk image. So all your drivers are covered as well.

If you've replaced the hard drive with another aftermarket drive, you'd need to contact HP for the disks. The product key fixed to the outside of the unit will not work on normal retail copies of Windows XP.

---

### Post by metaleroheaded on 2008-08-29
Ok so it was simple after all... Well not that simple... I reinstalled Windows with the HP Recover Partition (I didn't touch that while installing Linux) then it wouldn't let me access Linux so I just reinstalled the GRUB and my new computer is working just as new :P I lost all my files but no one died you know, so I'm fine (even though I lost near 30 GB of music... :( )

---

### Post by Sef on 2008-08-29
Thank you for posting your fix.   Glad you were able to fix your system, and in the future keep current back ups of your data.  I have lost  data too for failing to do that.

---

### Post by Bakon Jarser on 2008-08-30
Glad to hear your system isn't "completely hosed" and that I'm not anywhere close to owing cresho an apology.

---

### Post by metaleroheaded on 2008-08-30
you don't own him an apolopgy he owns you one!
just in case how do I back up 30GB of music????
in a bunch of dvds???
Is there a simple way to do that?

thanks, linux is working as well as windows so I'm happy with my new double-system computer :)

---

### Post by Bakon Jarser on 2008-08-30
> **metaleroheaded said:**
> you don't own him an apolopgy he owns you one!
just in case how do I back up 30GB of music????
in a bunch of dvds???
Is there a simple way to do that?

thanks, linux is working as well as windows so I'm happy with my new double-system computer :)

That's how I did it but it would be faster and easier to use a usb hard drive.  If you had a usb hard drive that you kept connected you could use ubuntu's backup program (I think it's called simple backup) to automatically backup your music folder every time it sees a change.

---

