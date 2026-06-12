---
title: "Help with grub, windows"
date: 2010-08-01
forum: Installation &amp; Upgrades
---

### Post by ashwinroyan on 2010-08-01
**Summary**
I have multiple partitions on a hard drive, wish to get some advice on structure, booting and grub.

**Non summarized**
I've had for a while now lucid, xp and windows 7 on my computer,

[COLOR=Green]Filesystem[/COLOR][INDENT]dev/sda1 - windows xp
[/INDENT][COLOR=Gray][COLOR=Green]Logical partitions[/COLOR]
[/COLOR][INDENT][COLOR=Gray]dev/sda5 - swap[/COLOR]
dev/sda6 - /
dev/sda7 - /home
[COLOR=Gray]dev/sda8 - swap[/COLOR]
[COLOR=SlateGray]dev/sda9 - Media(ntfs)[/COLOR]
dev/sda10 - Windows 7
[/INDENT]Recently, i decided to do away with windows xp so i formatted the partition, and got a Missing operating system error. I then installed Lucid on sda1 and from what i can see im only using it for grub. Is there any way to get my computer to be able to boot whilst keeping sda1 a data drive? (Moving the old oses to sda1?)I dont know how to get grub to work with sda1 being nothing. Also, I lost windows 7 on my grub list and cant seem to get it back. Did i loose its boot files with xp? Do i need to fixboot and mbr?

Thanks

---

### Post by drs305 on 2010-08-01
Read all before accomplishing.

To get Grub2 working on your system, you can run the LiveCD and from the Desktop:
Mount your Ubuntu *partition* and install to the drive. This will write to the **sda** MBR and install the grub files on the partition you designate in the first command. Note you do not designate a partition in the second command:
```

sudo mount /dev/sda6 /mnt
sudo grub-install --root-directory=/mnt /dev/sda

```
Reboot and you will have your Ubuntu back; however ....

I am not a Windows guy, but I know prior to Win7 the Windows OS had to be on a primary partition with the * boot designation. I don't know if that also applies to Win7 or not. You probably lost your boot files when you got rid of XP.

The best option would be to get Windows 7 working again if it can be done from a logical partition, then install Grub. If W7 can reside on a logical partition, here is a link to restoring its ability to boot:
[How to restore the Ubuntu/XP/Vista/7 bootloader]("http://ubuntuforums.org/showthread.php?t=1014708")

Once you have recreated the W7 boot files in the proper location, install Grub2 and it should find your W7 install as well.

---

### Post by ashwinroyan on 2010-08-01
Thank you very much.

---

