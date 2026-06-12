---
title: "How to remove GRUB."
date: 2013-06-24
forum: Installation &amp; Upgrades
---

### Post by sseba15 on 2013-06-24
Dear all,

I know that this question could be strange but I need to remove GRUB. Let me explain. I have 1 drive which is divded on 4 partition's.
1. partition - Windows 7 boot files (NTFS)
2. partition - windows 7 files (NTFS)
3. partition - ubuntu with GRUB (EXT3)
4. partition - swap

I need to encrypt whole drive using TrueCrypt but TC doesn't support encrypting whole drive with multiboot. So I need to use Windows loader to starting linuks. But my problem is that some can get access to computer using ubuntu GRUB. So in that case i need to.

1. Remove GRUB from Ubuntu
2. Add linux boot to windows bootloader (I know how to do this.)

I heard that ubuntu for servers have possibility to not install GRUB. But this is desktop version and it need to be desktop version.

I hope you know what I want to do and could help me with this. I am newbie with ubuntu so please be patient for me :)

---

### Post by grahammechanical on 2013-06-24
Please do not take me to be an expert on this. I am not. But here is the risk as I see it. Grub is in the MBR of the hard disk. If you remove Grub from the MBR you will not or you may not be able to boot into Windows to install another boot loader.

I may be wrong but I think that if you install the Windows boot loader first then it will overwrite the Grub data in the MBR and that will have effectively removed Grub from the MBR.

So, I suggest that first make sure that you can boot into Windows with the Windows boot loader. Then add Linux boot to the Windows boot loader. Replace one boot loader with another one, is the way to do it.

Regards.

---

### Post by oldfred on 2013-06-24
I do not know encryption. Those that use EasyBCD install grub2's boot loader to the Ubuntu PBR or partition boot sector. That compromises grub2 as it now does not really fit into a PBR and converts to blocklists or hard coded addresses for the rest of grub in the Ubuntu partition. If an update changes the address then you break booting and have to reinstall grub to the partition.

But I am not sure you can do that with Windows encryption. One user's workaround was just to install grub2's boot loader to a flash drive. Then from BIOS if he booted flash drive, it would load install on hard drive. He was just using MBR on flash drive, but could also store data on that drive.
If flash drive is sdb, from your working install on the hard drive.
       sudo grub-install /dev/sdb

Then if you boot from flash drive it will boot install on hard drive. I actually install grub to all my flash drives, but have it loading a grub.cfg from a /boot/grub on the flash drive. I have to manually create the grub.cfg, but can then configure it to boot hard drive, or ISO on flash drive to do repairs.


        
 Restore lost partiiton that was truecrypt
[http://ubuntuforums.org/showthread.php?t=1874260](http://ubuntuforums.org/showthread.php?t=1874260)
[http://worldsmostsecret.blogspot.com/2012/04/how-to-activate-trim-on-luks-encrypted.html](http://worldsmostsecret.blogspot.com/2012/04/how-to-activate-trim-on-luks-encrypted.html)

---

### Post by sseba15 on 2013-06-25
As I said in first post the GRUB is not installed on MBR but on the linuks partition 3. So standard MBR is not touched by linuks. I found this command which could be use:
ubiquity -b
But i need to test it first.

---

### Post by sseba15 on 2013-06-25
There is othere soltuion which I found. 

To install ubuntu 12.4 LTS you need to start ubuntu from live cd then go to terminal and start with sudo:
sudo ubiquity -b

In that case you are able to install Ubuntu without the bootloader.

But if you want to 2 system one windows 7 and one ubuntu encrypted whole drive using TrueCrypt it is not possible. :)

---

