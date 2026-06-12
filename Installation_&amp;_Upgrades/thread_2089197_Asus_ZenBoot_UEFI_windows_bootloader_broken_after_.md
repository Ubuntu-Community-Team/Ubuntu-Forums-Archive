---
title: "Asus ZenBoot UEFI windows bootloader broken after Ubuntu install"
date: 2012-11-28
forum: Installation &amp; Upgrades
---

### Post by d43m on 2012-11-28
Hi all,

Not sure if I should open a new topic or if I can use this, one.. so I used this one.

I installed Ubuntu 12.10 on my Asus Zenbook ux32vd, which has two discs, one sdd of 24 Gb and another mechanical disc of 500 Gb.
I wanted to keep the previously installed Windows 8, so I installed Ubuntu on about 10-15 Gb on the ssd, with /usr on the other disc.

Of course I didn't know what I was doing, so I booted my usb key in normal mode, and not EFI. So something was already messed up when I tried to install my system on the first try. Anyway, after the installation, both Ubuntu and Windows 8 didn't boot, so I read a bit of documentation and I decided to réinstall Ubuntu at the same place with EFI.  I used the first partition of 300 megs on the first disc (sda, the 500 gb hard drive) as an EFI enabled device. 

/dev/sda1 on /boot/efi type vfat (rw)

I remember that I didn't tick the "format" option, thinking this would keep the already installed windows files.

So. 

After the installation, my Ubuntu worked fine now. Woow, this HD screen is really beautiful with Ubuntu on it !

Tried to reboot on windows, It failed. Something about windows.efi files missing.

So I tried to run Boot-repair, but nothing. Here is the result: [B][http://paste.ubuntu.com/1394829/](http://paste.ubuntu.com/1394829/)

[/B]Hope you can help !

Thanks :)

---

### Post by oldfred on 2012-11-28
Moved to your own thread.

Is your system in French or did you run the French version of Boot-Repair. I cannot quite tell what it did. My High School French was 50 years ago. :)

Grub2's os-prober has a bug. It creates the BIOS Windows boot stanza saying to boot from sda4 which does not work with UEFI. 
Boot-Repair will add the correct efi boot stanza so you can boot Windows. If you did not have it add that, run that now.

Is/was this Intel SRT configuration. Did you turn that off before installing. I think this is first with Windows 8, some others with Windows 7 SRT configurations.

        Intel Smart Response Technology
[http://www.intel.com/p/en_US/support/highlights/chpsts/imsm](http://www.intel.com/p/en_US/support/highlights/chpsts/imsm)
Intel SRT - Dell XPS
[http://ubuntuforums.org/showthread.php?t=2038121](http://ubuntuforums.org/showthread.php?t=2038121)
[http://ubuntuforums.org/showthread.php?t=2036204](http://ubuntuforums.org/showthread.php?t=2036204)
[http://ubuntuforums.org/showthread.php?t=2020155](http://ubuntuforums.org/showthread.php?t=2020155)
Some info on re-instating 
[http://ubuntuforums.org/showthread.php?t=2038121](http://ubuntuforums.org/showthread.php?t=2038121)
[http://ubuntuforums.org/showthread.php?t=2070491](http://ubuntuforums.org/showthread.php?t=2070491)
Disable the RAID, for me it was using the Intel rapid management thingy and telling it to disable the acceleration or the use of the SSD. If you have a different system, just disable the RAID system then install Ubuntu. Once installed you can then re-enable it.

---

### Post by d43m on 2012-11-28
Thank you for your answer. I'm from Switzerland (french part), so I installed my Ubuntu in French, sorry :)

I used (and reused) boot-repair in recommended mode, nothing better so far.

At the end of the boot-repair programm, it says something like "Don't forget to update your BIOS to boot on sda1/EFI/ubuntu/grubx64.efi". Well, grub loads well, just windows doesn't load.

My installer recognized my issd very well, I didn't have to do anything special to create a new partition on it. I didn't see any options in the bios (UEFI should I say?) to disable the Smart Response technology...

Is there a way to boot windows without using Grub at all ? Just to see if it's grub or my windows files directly..

---

### Post by oldfred on 2012-11-28
UEFI is like having multiple hard drives in BIOS and setting to boot from Windows on sda and Ubuntu on sdb. Which ever you set as default in BIOS becomes the boot. 
With UEFI you should have a UEFI menu (somewhere?) that gives you a choice of ubuntu or windows. And it will boot into that each time you reboot. 

Boot repair should add a Windows entry to 25_custom before the os-prober entries.

If you look at grub config or 25_custom you can see the entry. It should look like this but will have your efi UUID (edited to yours):

       From Boot-Repair```

menuentry "Windows UEFI recovery" {
search --fs-uuid --no-floppy --set=root  8E12-C4DE
chainloader (${root})/EFI/Microsoft/boot/bootmgfw.efi
}
    
```I know Boot-Repair was updated to fix efi installs on two drives, but I think that was with efi partitions on both drives. Perhaps since you only have the efi partition on the Windows drive it is not updating.

You can add an entry to 40_custom and see if it works. Copy menuentry above into your 40_custom

       #Add menu entry to 40_custom
gksudo gedit /etc/grub.d/40_custom

#update grub menu
sudo update-grub

If that works you can also turn off os-prober so you do not get the incorrect entries. You can turn it back on later if you reconfigure by changing true to false.

#Turn off prober
gksudo gedit /etc/default/grub
#Add this line
GRUB_DISABLE_OS_PROBER=true

Another suggested efi entry 

> menuentry "Windows 7 UEFI" {
  search --file --no-floppy --set=root /efi/Microsoft/Boot/bootmgfw.efi
  chainloader (${root})/efi/Microsoft/Boot/bootmgfw.efi
}

    

---

### Post by d43m on 2012-11-28
Thanks. 

I tried to add both entries in 40_custom, and when I selected one of them as I reboot, the whole screen just seems to refresh.

sorry :/

EDIT: Is that because I use the same partition for /boot/uefi than for the windows boot ?

Mmh... the recovery should work in that case..


EDIT2: For information, When I go to the bios set up to "Boot override", I can choose to boot directly to :

Windows Boot Manager (PO: Hitachi HTS...)
Windows (PO: Hitachi HTS....)
ubuntu (PO: Hitachi HTS..
ubuntu (PO: Hitachi HTS..


Yes, Ubuntu is listed twice. When I launch the windows boot manager, it opens Grub. When I choose Windows (the second), the screen gets black for a fraction of a second but it stays on the same page, and when I choose both of the Ubuntu entries, it opens grub as well.

Also: I tried to change your uuid in recovery to the uuid that I found on via gparted, it didn't help.

Here is a new paste: [http://paste.ubuntu.com/1395307/](http://paste.ubuntu.com/1395307/)

---

### Post by oldfred on 2012-11-28
Neither of these entries in the grub menu should work as they are from os-prober and are the old style BIOS boot stanza.

> Windows Recovery Environment (loader) (sur /dev/sda2)
Windows 8 (loader) (sur /dev/sda4)
But both of the UEFI entries you added to 40_custom should work. 
Does Windows boot directly from UEFI?

Also your sdb1 was not shown as an efi partition in your first BootInfo, and it is large for an efi partition. Now it is flagged as an efi partition and has the label INTELRST which has to do with the Intel SRT system? That may conflict? I really do not know how the Intel system works. Links above had comments by some who have the Intel SRT system.

---

### Post by d43m on 2012-11-28
You're maybe right. I installed the root partition on sdb, which, from a windows point of view, was only a partition containing nothing. They were 2 partition, one that I kept, (4 Go) and another one, that I replaced with my Ubuntu  installation. I guess the second partition is missing. So it can't boot.

The two menu entries above seem to work, but I have a Blue Screen of Death saying that Windows needs to be recovered using an external device or something. I don't have that :/

---

### Post by d43m on 2012-11-28
For those who are interested, I found this on SRT: [http://www.overclockers.com/forums/showthread.php?t=684542](http://www.overclockers.com/forums/showthread.php?t=684542)

If the problem comes from RI clearly need a Windows Access to be able to repair or disable it. 

In my case, I think I will have to delete my linux partition, and if the boot on windows works, then I'll be able to 1) deactivate RST or 2) install Linux somewhere on the 500 Gb harddrive.

If the boot on windows doesn't work, I'll have to find a repair disc...

---

### Post by oldfred on 2012-11-28
Some info on reinabling SRT but you have to have a working Windows.

       Some info on re-instating 
[http://ubuntuforums.org/showthread.php?t=2038121](http://ubuntuforums.org/showthread.php?t=2038121)
[http://ubuntuforums.org/showthread.php?t=2070491](http://ubuntuforums.org/showthread.php?t=2070491)

    
Not sure how to do this unless you have access to another Windows 8 computer.

       Windows 8 UEFI repair USB must be FAT32
[http://social.msdn.microsoft.com/Forums/en-US/samsungpcgeneral/thread/e7ed293e-b565-44ee-a536-166dddf32205/](http://social.msdn.microsoft.com/Forums/en-US/samsungpcgeneral/thread/e7ed293e-b565-44ee-a536-166dddf32205/)

I was able to use Ubuntu to create a Windows 7 repairCD and then use that CD to create a bootable flash drive using the Windows commands from the repairCD to configure & copy itself to the flash drive.

---

### Post by YannBuntu on 2012-11-29
Hello

**@fred:** there is no localized version of Boot-Repair. There are some parts of the log in French because the system locale was French:
- some that i can't force to English (all GUI strings, eg the final "The boot has been successfully repaired" message), 
- and some other parts that i just forgot to convert to English (fdisk and df), but i will fix this.

**@d43m:**
- your log shows that you have no Windows efi files:
```
/EFI/Boot/bootx64.efi /EFI/Boot/bootx64.efi.grb 
                       /EFI/ubuntu/grubx64.efi 
                       /EFI/Microsoft/Boot/bootmgfw.efi 
                       /EFI/Microsoft/Boot/bootmgfw.efi.grb 
                       /EFI/Microsoft/Boot/bootx64.efi 
                       /EFI/Microsoft/Boot/bootx64.efi.grb
```
(because *.efi.grb files indicate that the corresponding *.efi file is a copy of grubx64.efi made by Boot-Repair.)

- currently you are booting Ubuntu in UEFI mode so either your computer came with no Windows efi file but booted Windows in Legacy mode (some firmware default to Legacy mode when no efi file is detected), or you erased these files by mistake.

- if i were you, i would:

1) use a Windows disk this way: [https://help.ubuntu.com/community/RestoreUbuntu/XP/Vista/7Bootloader](https://help.ubuntu.com/community/RestoreUbuntu/XP/Vista/7Bootloader) , until you get direct access to Windows. Then use Boot-Repair to recover the GRUB menu.
2) if still not good, please indicate the new URL that will appear.

---

### Post by oldfred on 2012-11-29
Because it is gpt partitioning Windows has to be in UEFI mode.

Is not this a Windows boot file? I thought only the .grb were the backups Boot-Repair made.

> /EFI/Microsoft/Boot/bootmgfw.efi As I understand it this is really part of UEFI as both Windows & Ubuntu provide it.
> 
/EFI/Boot/bootx64.efi

---

### Post by YannBuntu on 2012-11-29
@OldFred: please read [http://ubuntuforums.org/showthread.php?p=12379441#post12379441](http://ubuntuforums.org/showthread.php?p=12379441#post12379441)

---

### Post by d43m on 2012-11-29
Thank you, so Ubuntu removed the windows boot files, without me to say whatsoever...

I still have my recovery and my restore partitions, containing EFI  files.  But when I boot directly on these partitions, I have a  magnificent BSOD (or almost) saying that my windows is broken. So I  guess it's no use that I copy the efi files from there to my /boot/efi  partition.
It looks like I have 2 problems:

1) My original efi files don't exist anymore, so it can't boot
2)  Even if I boot my recovery partition it doesn't work, I guess that's  because I messed up the ssd cache partition - Intel® RST (sdb1)

In any case, I will need a windows 8 repair cd / iso. And I didn't created it before... this thing is unfindable on the internet, so I'll have to go to the store I guess.

---

### Post by YannBuntu on 2012-11-29
First try with a Windows7 64bit cd, you can download one from here: [https://help.ubuntu.com/community/RestoreUbuntu/XP/Vista/7Bootloader#Windows_Vista_or_7](https://help.ubuntu.com/community/RestoreUbuntu/XP/Vista/7Bootloader#Windows_Vista_or_7)

(AFAIK Win7 and Win8 use the same bootloader)

---

### Post by d43m on 2012-11-29
Oh, that's good to know.

I'll try that.

---

### Post by d43m on 2012-11-30
Status update: WIndows 7 repair disc didn't work. It said that the detected OS was not corresponding.

However. I managed to find a Windows8 install disc (USB Key). So I tried to repair it, but it doesn't work. It looks like my windows8 usb key is not in GPT format (When I plug in my sony usb key with Ubuntu on it, it says "UEFI: Sony Storage..." in the BIOS and it's not the case for the Windows usb key). 

I even tried to install Windows on the sda4 partition with this USB Key, doesn't work.

I guess that's not Ubuntu-related anymore...

---

### Post by YannBuntu on 2012-11-30
> **d43m said:**
> I guess that's not Ubuntu-related anymore...

Yes.
If i were you, i would:
1) backup documents on external disk (or DVDs)
2) then reinstall Windows8 (this may erase Ubuntu)
3) then (if Ubuntu has not been erased) recover the GRUB menu via Boot-Repair

---

### Post by oldfred on 2012-11-30
I saw that the  typical Windows repair USB is NTFS, but to repair UEFI systems it needs the FAT partition  as a repair. Then you should get the option to boot in either UEFI or the old BIOS mode to install or repair.

UEFI only boots from FAT partitions. The standard is FAT32 on internal devices. Small removable devices can use FAT16.

       Windows 8 UEFI repair USB must be FAT32
[http://social.msdn.microsoft.com/Forums/en-US/samsungpcgeneral/thread/e7ed293e-b565-44ee-a536-166dddf32205/](http://social.msdn.microsoft.com/Forums/en-US/samsungpcgeneral/thread/e7ed293e-b565-44ee-a536-166dddf32205/)

---

### Post by d43m on 2012-12-01
I'm going to reinstall Windows8 not in GPT, but on a standard oldschool filesystem. I saw some posts from Zenbook Dualboot users and this should work fine. I'm thinking about installing Windows on the 500Gb HD, and Linux on the 24 Gb issd, even though the performance is not as good as on a real SSD.

Thanks for your help anyway Fred and Yann !

---

