---
title: "What would happen if I erased Ubuntu?"
date: 2010-08-28
forum: Installation &amp; Upgrades
---

### Post by Oven Glove on 2010-08-28
Presuming ubuntu was dual-booting alongside windows with GRUB, and I formatted the ubuntu partition, what would happen at startup; would I still be able to access windows, and would the option to boot ubuntu just disappear?

Purely out of interest,
Owen

---

### Post by sikander3786 on 2010-08-28
I have never done that but I think the option to boot Ubuntu will still be there unless you modify GRUB or recover MBR.

The best way around will be to format the Ubuntu partition and then recover the MBR from the Windows Installation Disc.

[COLOR="Red"][COLOR="DarkRed"]EDIT:[/COLOR][/COLOR] Also see the link below for a detailed answer.

[http://ubuntuforums.org/showthread.php?t=508927](http://ubuntuforums.org/showthread.php?t=508927)

---

### Post by Oven Glove on 2010-08-28
Ok great, thanks for your help.

---

### Post by uRock on 2010-08-28
Yes, you would have to recover the MBR, because with the Ubuntu partition being erased the grub will have no file to read to know what is where.

You can install Lilo via a LiveCD and it will fix the MBR for you.

> **presence1960 said:**
> You can repair the MBR to a windows MBR from  ubuntu or the ubuntu live CD. Install lilo by running in terminal  ```
sudo apt-get install lilo
```Ignore the warning and next run in  terminal ```
sudo lilo -M /dev/sdX mbr
```where is sdX is your  disk/device, i.e. sda, sdb,sdc, etc

---

### Post by oldfred on 2010-08-28
Grub would need the files in the /boot/grub to boot.

I think the mbrfix is older.

You can either use a windows repair to run fixMBR or BootRec.exe /fixmbr depending on version of windows or from Ubuntu or liveCD.

per meierfra. mbr.bin may cause problems in some cases better to use lilo
Restore basic windows boot loader - universe enabled from Ubuntu or liveCD
sudo apt-get install lilo
sudo lilo -M /dev/sda mbr
May show error messages about the rest of lilo missing, ignore, we just want MBR

---

### Post by Oven Glove on 2010-08-28
Thanks for all of your suggestions; I wasn't thinking of actually removing ubuntu just yet but this is still helpful. :-)

---

### Post by ex_isp on 2010-08-28
Probable easiest/best would be boot into win, get cmd line, run fdisk /mbr

**FDISK /MBR **Command used to rewrite the [Master Boot Record]("http://www.computerhope.com/jargon/m/mbr.htm"). See [CH000175]("http://www.computerhope.com/issues/ch000175.htm") for additional information.

from
[http://www.computerhope.com/fdiskhlp.htm#04](http://www.computerhope.com/fdiskhlp.htm#04)

---

### Post by coffeecat on 2010-08-28
> **Oven Glove said:**
> Thanks for all of your suggestions; I wasn't thinking of actually removing ubuntu just yet but this is still helpful. :-)

Just to add to what others have said.

Grub stage 1 is only about 400 bytes in size and this resides in the MBR, the first 512 bytes of the hard drive. It replaces the Windows MBR. The partition table occupies the rest of the MBR and comes immediately after grub stage 1 or the Windows MBR.

Grub stage 1.5 is a few kilobytes in size and occupies an otherwise unused portion of the HD immediately after the MBR.

Grub stage 2 is in /boot/grub in your Ubuntu root partition, together with the main menu/configuration file for grub - menu.lst for legacy grub and grub.cfg for grub 2.

Stage 1 calls stage 1.5 which calls stage 2. So - if you remove your Linux root partition, stages 1 and 1.5 have nowhere to go and you get an error message. Doing this is a common error with newcomers. I have seen many threads about this.

In this situation you can repair the Windows bootloader in the way others have described, or (re)install any Linux distro which will reinstall grub stages 1 and 1.5 pointing to the new grub stage 2 in the new Linux root partition.

---

