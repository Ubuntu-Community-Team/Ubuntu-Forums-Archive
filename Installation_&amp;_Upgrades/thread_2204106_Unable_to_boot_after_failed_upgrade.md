---
title: "Unable to boot after failed upgrade"
date: 2014-02-06
forum: Installation &amp; Upgrades
---

### Post by sebasbas7 on 2014-02-06
Hi,

The other day I was attempting to upgrade ubuntu from 13.04 to 13.10. The way I normally go about this is by downloading the torrent and creating a live usb since its faster then downloading from the server. Ubuntu began analyzing my disks and then I chose the Upgrade ubuntu option like usual. The problem arose when it prompted me that it was unable to load a certain partition on my drive but unfortunately, I did not write it down. I'm guessing it was my efi boot partition since when I tried to boot back up I was given an error. I decided to then try boot repair since it has fixed a few boot up issues in the past but I think all it did was create a grub partition which didn't really solve my problem. It did give me a nice readout so maybe someone who is more experienced in this field can help me out. I'm not looking for a perfect fix either, I'd just like to be able to boot up someway, make a deja-dup backup, and ill just do a clean install of 13.10 after.

This is the link for a summary of my drives given by boot repair:

[http://paste.ubuntu.com/6888333/](http://paste.ubuntu.com/6888333/)

Any help will be greatly appreciated.

Thanks

---

### Post by oldfred on 2014-02-06
Did you boot in BIOS mode?
You have UEFI install and must always boot in UEFI mode. And how you boot is how it installs, so if you reinstall in wrong mode it creates confusion.
You now have two efi partitions, but can only have one. Use gparted and remove boot flag from sda2.
Then boot Boot-Repair in UEFI mode and rerun repairs. Or tick efi.

Boot-Repair said this, which is most unusual.
 This setting will restore the [(generic mbr)] MBR in sdb, and make it boot on sdd1.

The generic boot loader is a Window type boot loader that only works on same drive.

---

### Post by sebasbas7 on 2014-02-06
I attempted following your advice however I am still unable to resolve the problem. I removed the boot flag from sda2 using gparted. Then I created a seperate boot recovery usb and booted that using uefi and attempted the repairs again. It seems like I made progress but now when I try to boot up it gives me the error "Missing operating system" "BOOTMGR is missing". 

Here is a new log:

[http://paste.ubuntu.com/6888897/]("http://paste.ubuntu.com/6888333/")

Again thank you for the help.

---

### Post by oldfred on 2014-02-07
Did you post same BootInfo, it still shows two efi partitions.

Bootmgr manager missing is a Windows error. That is probably from a BIOS boot of sdb which has syslinux a Windows type boot manager that would look for bootmgr reference in partition boot sector of sdb1 which has no Windows boot files.

---

### Post by sebasbas7 on 2014-02-09
My apologies for the late reply. I thought I had removed the boot flag from sda2 but I'm guessing I didnt apply it. 

What I do remember is when I ran boot repair from the live cd of ubuntu it would not allow me to repair the boot of anything other then sdb. I ran it anyway and that is why it was constantly trying to boot from sdb and giving me the missing BOOTMGR error. So I used gparted a removed the boot flag from sdb and that fixed that problem. 

In regards to sda now, gparted is stating that there is no other boot flags except on the sda1 partition which I believe is correct. However, I am still unable to boot.

Here is a new BootInfo:

[http://paste.ubuntu.com/6906368/](http://paste.ubuntu.com/6906368/)

I don't know, but to me it seems as if there are still boot files on sda2 which is strange since that isn't what gparted shows,

[IMG]http://i.imgur.com/2rc9a6U.png[/IMG]

---

### Post by oldfred on 2014-02-09
Back to original question. I think I assumed you had UEFI install as you had gpt partitioning and first partition was FAT32 with boot flag. Is that correct? 
Original BootInfo showed one efi file in the FAT32 partition.

You now have only BIOS boot syslinux in every MBR. Syslinux is a genernic Windows type boot loader that Boot-Repair installs to fix Windows booting. 

You now have no UEFI installs as you had Boot-Repair do a BIOS type fix not a UEFI fix.

I think if you just have Boot-Repair do the full un-install of grub and reinstall grub-efi for UEFI boot in advanced options, that that should work.

---

### Post by sebasbas7 on 2014-02-09
I believe you are correct. In the beginning before all this happened I saw  my drive through the Asus bios as a uefi boot so I'm sure I had that before. However, I tried formatting that first FAT32 partition in hopes that it would fix the problem but it seems that it only made boot-repair think I had a windows install. I'll try reinstalling uefi boot through the program. The only thing is that I have searched through all the advanced options tabs and have found only a few options such as restore mbr and which type of generic MBR I want but nothing involving installation of efi.

---

### Post by oldfred on 2014-02-10
The link in my signature has links to just about everything UEFI.

I think if using Boot-Repair you have to boot in UEFI mode to see more UEFI options. I do not have UEFI so do not see those options to post a screen shot. You also have a efi box to tick and that will install in UEFI mode.

UEFI and BIOS are not compatible and work totally differently. So if you boot in one mode you cannot use grub to chain boot another system in the other mode, or install in a different mode. Only by rebooting and choosing from UEFI menu can you change to boot UEFI or change to boot BIOS as UEFI menu will list all installs whether BIOS or UEFI. Some may also require you to turn on or off UEFI or BIOS/CSM/Legacy modes.

And if secure boot is on, only secure boot systems in UEFI mode will boot. CSM has not secure boot mode.

---

