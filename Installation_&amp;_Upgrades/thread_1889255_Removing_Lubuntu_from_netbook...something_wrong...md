---
title: "Removing Lubuntu from netbook...something wrong.."
date: 2011-12-01
forum: Installation &amp; Upgrades
---

### Post by FrankGun on 2011-12-01
Hello guys
I have a big problem.
I had Lubuntu 11.10 on my netbook N150 but yesterday I had to remove it (ahhh, my wife...).
So, I put in Ubuntu Live from Usb, I went in Gparted and I deleted every partition, changing in NFTS (I don´t know if it is the reason..).
Anyway, I closed it and I restarted the machine with XP on Usb..
But, the problem raised after that.
After the Samsung Logo, the netbook stops at this screen:

error: unknown filesystem.
grub rescue>

I cannot do anything, I tried with a XP on usb, with Ubuntu Live but nothing. I always see this words...
What do I have to do?
I have to come back to XP but now I don´t know how to solve this big problem.

I tried to digit 
[FONT=Verdana]sudo fdisk -l[/FONT]

[FONT=Verdana]but the system tells me "sudo command unknown"...

Please, help me !

Many thanks,
Francesco.


[/FONT]

---

### Post by papibe on 2011-12-01
Your netbook is still trying to boot from the hard drive. In order to boot from the USB, you either have to get into 'boot options' or change the boot order on the BIOS.

I hope it helps,
Regards.

---

### Post by FrankGun on 2011-12-01
The problem is that I cannot switch options for boot when I push "esc" on start up.
Because after Samsung Logo, appears that script...
I have no chance to change Boot for Usb..

---

### Post by papibe on 2011-12-01
I see. You should get into the BIOS then. There set the USB device as primary and then reboot again.

Regards.

---

### Post by pahfect@yahoo.com on 2011-12-01
Hi,had such a problem earlier this week.i ran the ubuntu 11 live cd and installed ubuntu 11 so as to be able to access my windos 7 OS...it worked...u cn simply install ubuntu,then format ur computer with windows xp then later intall ubuntu inside windows or on a separate partition.

---

### Post by FrankGun on 2011-12-01
> **papibe said:**
> I see. You should get into the BIOS then. There set the USB device as primary and then reboot again.

Regards.


Hi,
for my netbook I have to push Esc to switch device booter.
and when I do it, I have that string.

---

### Post by FrankGun on 2011-12-01
> **pahfect@yahoo.com said:**
> Hi,had such a problem earlier this week.i ran the ubuntu 11 live cd and installed ubuntu 11 so as to be able to access my windos 7 OS...it worked...u cn simply install ubuntu,then format ur computer with windows xp then later intall ubuntu inside windows or on a separate partition.

I cannot do anything, I have the same problem with both of USB live (Ubuntu and XP).

---

### Post by pahfect@yahoo.com on 2011-12-01
have u tried running it from a cd?

---

### Post by FrankGun on 2011-12-01
> **pahfect@yahoo.com said:**
> have u tried running it from a cd?

my netbook has not CD...only USB...

---

### Post by mastablasta on 2011-12-01
again, as it was mentioned above you need to enter into BIOS (and change the boot order there) not just device booter.
 
what happened here is that Ubuntu's bootloader is still installed on the disk. once you boot to windows install you can remove it using windows console. or with a windows install it will get overwritten.

---

### Post by FrankGun on 2011-12-01
> **mastablasta said:**
> again, as it was mentioned above you need to enter into BIOS (and change the boot order there) not just device booter.
 
what happened here is that Ubuntu's bootloader is still installed on the disk. once you boot to windows install you can remove it using windows console. or with a windows install it will get overwritten.


So guys,
This evening is a great evening.
I was able to enter in this Ubuntu Live, there are some problems (like Firefox not working, screenshot not working,) but I can see in Gparted and I have the terminal.
So, I post here what I see in Gparted:


/dev/sda1                   (!) Blue square ntfs          48.83GiB   ---         ----              boot
/dev/sda3                   (!) Blue square ntfs          99.23GiB   ---         ----           
(- in a black circle) /dev/sda2     (key)extended                   1012.00MiB   --         -----
/dev/sda5                                 (key)linux-swap                 1012.00MiB  ---         -----

---

### Post by FrankGun on 2011-12-02
up

---

### Post by papibe on 2011-12-02
What do you want to do?

Install Ubuntu or XP?

Regards.

---

### Post by FrankGun on 2011-12-02
> **papibe said:**
> What do you want to do?

Install Ubuntu or XP?

Regards.


XP...
I want to install it alone.

---

### Post by papibe on 2011-12-02
Then I wouldn't worry about the disk partitions, just reformat the whole drive while installing XP.

Again, you need to boot into a USB stick or external USB CD containing the XP installation software.

If you see the grub prompt, it is too late. You need to press an special key (check your manual or search the Internet) to either get into the machine's 'boot options', or into the BIOS itself.

Regards.

---

### Post by FrankGun on 2011-12-03
Hi Guys,
this is the fdisk just did, if u need:

                       [LEFT]To run a command as administrator (user "root"), use "sudo <command>".[/LEFT]
    [LEFT]See "man sudo_root" for details.[/LEFT]
        [LEFT]lubuntu@lubuntu:~$ sudo fdisk -l[/LEFT]
        [LEFT]Disco /dev/sda: 160.0 GB, 160041885696 byte[/LEFT]
    [LEFT]255 testine, 63 settori/tracce, 19457 cilindri[/LEFT]
    [LEFT]Unità = cilindri di 16065 * 512 = 8225280 byte[/LEFT]
    [LEFT]Sector size (logical/physical): 512 bytes / 512 bytes[/LEFT]
    [LEFT]I/O size (minimum/optimal): 512 bytes / 512 bytes[/LEFT]
    [LEFT]Identificativo disco: 0x0007a3ee[/LEFT]
        [LEFT]Dispositivo Boot      Start         End      Blocks   Id  System[/LEFT]
    [LEFT]/dev/sda1   *           1        6375    51200000    7  HPFS/NTFS[/LEFT]
    [LEFT]/dev/sda2           19329       19458     1036289    5  Esteso[/LEFT]
    [LEFT]/dev/sda3            6375       19329   104051712    7  HPFS/NTFS[/LEFT]
    [LEFT]/dev/sda5           19329       19458     1036288   82  Linux swap / Solaris[/LEFT]
        [LEFT]Le voci nella tabella delle partizioni non sono nello stesso ordine del disco[/LEFT]
        [LEFT]Disco /dev/sdb: 1006 MB, 1006632960 byte[/LEFT]
    [LEFT]255 testine, 63 settori/tracce, 122 cilindri[/LEFT]
    [LEFT]Unità = cilindri di 16065 * 512 = 8225280 byte[/LEFT]
    [LEFT]Sector size (logical/physical): 512 bytes / 512 bytes[/LEFT]
    [LEFT]I/O size (minimum/optimal): 512 bytes / 512 bytes[/LEFT]
    [LEFT]Identificativo disco: 0xb94dd873[/LEFT]
        [LEFT]Dispositivo Boot      Start         End      Blocks   Id  System[/LEFT]
    [LEFT]/dev/sdb1   *           1         123      983008+   b  W95 FAT32[/LEFT]
    [LEFT]La partizione 1 ha diversi elementi finali fisici/logici:[/LEFT]
    [LEFT]     phys=(121, 254, 63) logico=(122, 97, 39)[/LEFT]
    [LEFT]lubuntu@lubuntu:~$ [/LEFT]

---

### Post by amjjawad on 2011-12-03
Hi,

Please follow the instructions in this link:

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

then post the output her but please wrap up the text with "CODE" tags:

[IMG]http://ubuntuforums.org/picture.php?albumid=2161&pictureid=8148[/IMG]

---

