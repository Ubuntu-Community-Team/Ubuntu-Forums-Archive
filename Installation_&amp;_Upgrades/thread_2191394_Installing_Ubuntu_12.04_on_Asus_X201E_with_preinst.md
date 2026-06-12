---
title: "Installing Ubuntu 12.04 on Asus X201E with preinstalled Windows 8"
date: 2013-12-02
forum: Installation &amp; Upgrades
---

### Post by miniKOX on 2013-12-02
Hello.

I have just bought a brand new Asus X201E and I want to install Ubuntu 12.04.3 LTS on it.

First I must say that I had a problem with botting a LiveUSB: there was nothing but a black screen instead Ubuntu loading screen. Finally i managed to run a session, when I disabled a Secure Boot and CMS(or something like that) in BIOS - then there was a "black screen" again, but it was enough to hit ENTER and the system loaded fine.

I manually partitioned disk in this order:

```

/
/home
swap

```

but at the end of installation, such a information apeared:
```

grub-efi-amd64-signed' package failed to install into /target/. Without the GRUB boot loader, the installed system will not boot.

```

I read a lot about this: one sorces say that I should make a EFI(?) partition, the other - like here [https://help.ubuntu.com/community/UEFI#Creating_an_EFI_partition](https://help.ubuntu.com/community/UEFI#Creating_an_EFI_partition)

> 
If your disk already contains an EFI partition (eg if your computer had  Windows8 preinstalled), it can be used for Ubuntu too. Do not format it.  It is strongly recommended to have only 1 EFI partition per disk.

say - as far as I understand - that there is no need of creating such one. 

I tough that this is a problem with a GRUB, that GRUB has no place to install. In fact, when I am commiting an installation process, on partitioning step there is a drop-down list, that says where to put a "bootloader program". On this drop lists there are a partitions that I made myself and a Windows partitions. As I did not know with one to choose, i followed this thread: [http://ubuntuforums.org/showthread.php?t=1626263](http://ubuntuforums.org/showthread.php?t=1626263) - and left the "bootloader program" on: sda(without number)...

Can someone tell me and put in in a simple words - how should I install Ubuntu?

My only problem is this mentioned above, that at the end of installation an error apears, saying: 

```

grub-efi-amd64-signed' package failed to install into  /target/. Without the GRUB boot loader, the installed system will not  boot.

```

What am I doing bad, that the system can not be installed?

---

### Post by oldfred on 2013-12-02
Lets see details.
 Post the link to the BootInfo report that this creates. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)
Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration and diagnose advanced problems.

Did you turn off fast boot in Windows?
Do you have secure boot on or off?

Review links in the link in my signature especially the first three.

---

### Post by miniKOX on 2013-12-02
Yes. When I was installing I first turned off: fast boot in Windows Control Panel\Energy, fast boot and launch CSM both disabled in my BIOS.
Secure Boot Control in BIOS was disabled, Secure Boot state was shown in BIOS as disabled.

This is the link, that Boot-Repair has generated:

[http://paste.ubuntu.com/6511347/](http://paste.ubuntu.com/6511347/)

When I started Boot-Repair, it told, that "EFI partition was found. Here is a screen of my partitions:

[img]http://imageshack.com/a/img854/3179/45oy.png[/img]

---

### Post by oldfred on 2013-12-02
Your Linux partitions now are missing? Swap became sda10 but now there is no sda7, 8 & 9??

You can partition in advance from gparted and then from Installer use the Something Else or manual install and choose / (root) for your root partition and ext4, /home as ext4. If swap exists it will auto find that. Grub will auto install to sda's efi partition if you are installing from an UEFI boot and select sda. If you happen to boot in BIOS mode then you also have to have a bios_grub partition and grub installs to the protective MBR that gpt drives have. Drives with gpt partitioning still have an MBR, with one partition entry for gpt so old tools like fdisk do not offer to reformat without at least showing the one gpt partition table entry.

If grub does not correctly install Boot-Repair should be able to fix it.

---

### Post by miniKOX on 2013-12-02
No. I deleted them, for I tough that there is something wrong with them and I wanted to create a "eufi/boot"(or something like that)  partition, thinking that it help - as I read about it on forum, but I don't remember the topic, when I find it, I will post it to prove :D.

> Grub will auto install to sda's efi partition if you are installing from an UEFI boot and select sda - so I do not need to make a new partition with "EFI...something"?

>  If you happen to boot in BIOS mode then you also have to have a  bios_grub partition and grub installs to the protective MBR that gpt  drives have. - sorry, it may sound silly, but what do you mean by "boot in BIOS mode"? I always choose in BIOS, to boot from USB when I am installing Ubuntu. So I must additionaly make a partition with is "bios-grub", and from drop-down list saying: where to install a bootloader also choose "sda" - do I understood you good?

---

### Post by oldfred on 2013-12-02
With UEFI there now are two ways to boot - UEFI or BIOS(CSM).
 UEFI Compatibility Support Module (CSM), which emulates a BIOS mode 

And how you boot is how it installs. You now have switches in UEFI to turn on secure boot, UEFI, boot or CSM/BIOS/Legacy boot. Some UEFI clearly have switches for each. Others just have UEFI with secure boot on or off and when boot will try to boot from an efi partition and if no boot files found will boot from MBR in BIOS mode. 
UEFI and BIOS are not compatible, so once you start booting in one mode you cannot change. You have to go back into UEFI menu to boot another system in different boot mode.

With BIOS, there is only one MBR, so only one install controls boot as BIOS jumps to MBR to boot. 
With UEFI you have an efi partition with as many folders for each operating systems as you may want. From UEFI meny you can boot any of them, but from grub you can chain back to efi partition to boot Windows or another install if not directly in grub menu.

More details in link in my signature. (lots of info)

This shows both screens. Purple BIOS, grub menu for UEFI.
      
 Shows install with screen shots for both BIOS & UEFI, so you know which you are using.
[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

---

### Post by miniKOX on 2013-12-02
As I mentioned I have CSM and Secure Boot disabled - it means that I boot in UEFI, therefore I must also make a bios-grub partition, to make Ubuntu work? Sorry but I completly do not realize the sense of existing UEFI - it was easier when all you had to do was to plug USB and make 3 partittions. Is it possible to make installation simple again? How do I turn off this UEFI? I do not see such option in my BIOS to simply turn it off.

---

### Post by oldfred on 2013-12-02
Only if you want to install in BIOS mode do you need a bios_grub partition, not with UEFI.
UEFI uses the efi partition for booting.

UEFI is the new way of booting and Microsoft complicated it a lot with secure boot. Many with just standard boot are able to just install with UEFI like we did with BIOS.

---

### Post by miniKOX on 2013-12-03
> Grub will auto install to sda's efi partition if you are installing from an UEFI boot and select sda

My  Ubuntu 12.04 is 64bit version and it boots with black, not purple  screen(the purple screen apears later, when session is loading).

I  once created(with secure boot disabled) 3 partitions(/,home and swap). I  am booting my pendrive in EFI mode(in BIOS/Boot I can choose wether to  boot from disk, or USB EFI...something. I choose "sda" for bootloader to  install, and always this grub error apears. So after installing Ubuntu with this error I should use a Boot-Repapir and fix this, yes?

I read in the thread, that is in your signature:
> Use Windows Disk Tools to shrink Windows main partition, but not to  create any new partitions, if installing on same drive. Reboot after  shrink so it can run its repairs to its new size.


So I should - working in Windows - shrink the partition  with Windows, and of this shrinked area make a ext4 "/" partition for  Ubuntu?

> Backup efi partition and Windows partition before Install of Ubuntu
How do I know, with one partition is EFI in my case? Could you tell me, as you have got my Boot Repair log and a screenshoot?

And yet here:

>  As of 12.04.2 or later, it is possible to install on UEFI systems with  Secure Boot enabled (using signed versions of Shim, GRUB, and the Linux  kernel). This is only currently set up for Ubuntu (desktop, alternate,  and server) and Edubuntu images due to pressures of time; we expect to  enable it across the entire Ubuntu family for 12.04.3.
 
Installing Grub for UEFI secure boot is only possible if you have booted  your system using EFI with secure boot on. And some systems will only  boot with UEFI and secure boot on or with CSM if secure boot is off.  Best to test system to see which modes it boots in. In secure boot mode  it will only show/allow systems that have secure boot.

I must then turn on Secure Boot in BIOS and CSM and then install Ubuntu?
I am getting lost in all of this...:/

---

### Post by oldfred on 2013-12-03
Generally best not to use secure boot. But if your system will only let Ubuntu install in that mode you can.

Your sda1 is the system partition with the boot flag. In gpt partitioning the boot flag is really just the setting that says that is the efi or ESP partition.

Your parted -l in Boot info report also showed this:

>  Partition    Start Sector    End Sector  # of Sectors System
/dev/[COLOR=#ff0000]sda1[/COLOR]           2,048       616,447       614,400 [COLOR=#ff0000]EFI System partition[/COLOR]



you have already made the unallocated and the Linux partitions. If you did not reboot Windows it has not done its chkdsk repairs yet. Best to boot Windows before the install. Once you get grub working it can only boot a working install of Windows and sometimes  even Windows needs repairs, so having a Windows repair CD or flash drive is highly recommended.

---

### Post by ralic on 2013-12-04
I'm experiencing the same problem with an ASUS X202E and Ubuntu 12.04.3 LTS.

When the error is thrown, /dev/sda1 (the efi partition) is mounted at /target/boot/efi
The directory structure is as follows:
/target/boot/efi/EFI/ASUS
/target/boot/efi/EFI/Boot
/target/boot/efi/EFI/Microsoft

ASUS and Microsoft contain various files and directories, whereas Boot contains just one file, bootx64.efi

Is it possible to find out what the installer is trying to do at this point, so as to try and understand what is causing the error?
I've reviewed the files in /var/log as well as /target/var/log and don't see anything useful, except that according to apt's history.log, the package being installed when the error is thrown is 'shim-signed'.

---

### Post by miniKOX on 2013-12-04
>  I'm experiencing the same problem with an ASUS X202E and Ubuntu 12.04.3 LTS.

Good to hear that I am not alone with my problem...

>  you have already made the unallocated and the Linux partitions.
But I deleted them all - shall I make them again, of these 185.20GB of unallocated space?


> 
 If you  did not reboot Windows it has not done its chkdsk repairs yet.

And the chkdsk must be done by Windows, after I create these partitions, yes?(I run Ubuntu, make 3 partitions with Gparted and run Windows again so it will make its chkdsk??
> Best to  boot Windows before the install 
Why? To make a partitions for Linux under Windows?

> 
When the error is thrown, /dev/sda1 (the efi partition) is mounted at /target/boot/efi

So installing this "bootloader..." on sda1 will not be a good solution?

> 
Once you get grub working it can only  boot a working install of Windows and sometimes  even Windows needs  repairs, so having a Windows repair CD or flash drive is highly  recommended.


So even if I somehow - I do not know how - manage to install GRUB without error, there will be only Windows entry on the list?

Sorry for my stupid questions...

---

### Post by ralic on 2013-12-04
> **miniKOX said:**
> So installing this "bootloader..." on sda1 will not be a good solution?
It made no difference in my case.
I get the same error result whether I choose /dev/sda or /dev/sda1 as "Device for boot loader installation:".

In both cases, /dev/sda1 is mounted at /target/boot/efi. So the correct efi location is identified, but something prevents successful installation. I checked the basics, there's 242M available and 'sudo touch /target/boot/efi/EFI/test' succeeded, so I'd like to step through the install script to see if I can establish where it fails...

---

### Post by ralic on 2013-12-04
@miniKOX
If you boot the USB installer and run option 'Check disc for defects', do you also get 'errors found in 3 files' in the summary at the end?

---

### Post by ralic on 2013-12-04
Ok, so in my case (and hopefully yours) the grub-efi-amd64-signed deb file's name got mangled somewhere along the way.

Put your USB install device in another computer and navigate to: \pool\main\g\grub2-signed
If there is a file in there named 'grub-efi-amd64-signed_1.9~ubuntu12.04.4+1.99-21ubuntu3.10_amd.deb', rename it to 'grub-efi-amd64-signed_1.9~ubuntu12.04.4+1.99-21ubuntu3.10_amd**64**.deb' (modification highlighted in bold) and retry the installation.

Mine no longer chokes while trying to install grub-efi-amd64-signed and the installation completed successfully and on reboot I had a wonderfully familiar grub boot loader.

As to how this happened, the iso I downloaded passed md5 check, so it's either already a problem in there, or the universal usb installer did something funky in the conversion.

---

### Post by oldfred on 2013-12-04
I filed a bug report on that missing 4 at end of string/name with 12.04.2 and now it says confirmed.
Please go out and add that you have the same issue but with the newer version.

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1172065](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1172065)

---

### Post by miniKOX on 2013-12-04
> 
Mine no longer chokes while trying to install grub-efi-amd64-signed and  the installation completed successfully and on reboot I had a  wonderfully familiar grub boot loader.

And where have you put a bootloader? On sda or sda1?

>  I filed a bug report on that missing 4 at end of string/name with 12.04.2 and now it says confirmed.
Please go out and add that you have the same issue but with the newer version.

I followed the link and added a comment in with I described my problem - is it a correct bug report or will it be considered so?

---

### Post by oldfred on 2013-12-04
I think with confirmed it just means that more than one user has reported the same issue. The maintainer originally said the original files on the server were ok, so they need to track down where it loses the last character. I suspect in making the ISO it cannot handle the long string somehow. But I do not really know.

If you install in BIOS mode, you always install to MBR or sda, but if installing in UEFI mode the boot loader goes into the FAT32 efi partition which may vary. I think with UEFI it automatically finds the efi partition on the drive you specify. So sda should work in both cases.

---

### Post by ralic on 2013-12-04
> **miniKOX said:**
> And where have you put a bootloader? On sda or sda1?
I used /dev/sda but be warned, the grub bootloader does not boot Windows 8 after this installation. There is an entry for it, but it throws an error. I have to look into this further.

You can still boot Windows 8 afterwards using the BIOS entry, so its not a problem for me, but if you are unable to get into the BIOS on your system without first booting Windows 8, then you may want to reconsider whether this is a wise idea.

---

### Post by miniKOX on 2013-12-04
And if I will install bootloader on sda1? Will it be good?

---

### Post by ralic on 2013-12-04
> **oldfred said:**
> The maintainer originally said the original files on the server were ok, so they need to track down where it loses the last character. I suspect in making the ISO it cannot handle the long string somehow. But I do not really know.
Added my 2c to the bug report. Seems the filename differs depending on the OS used to mount/view the iso.
[edit]
Note, this was a virtual mount (same thing UUI would reference I expect) on Win7 64bit ,but not sure if dumping the iso to physical media would make a difference or not.
[/edit]

---

### Post by ralic on 2013-12-04
> **miniKOX said:**
> And if I will install bootloader on sda1? Will it be good?
I doubt it. From my earlier investigation, the installer treats a bootloader destination of /dev/sda (the whole device) exactly the same as /dev/sda1 (the first partition [efi in our case] of the device). So it doesn't matter which one you choose, they are exactly the same and so I would expect the same result.

---

### Post by miniKOX on 2013-12-04
>  You can still boot Windows 8 afterwards using the BIOS entry, so its not  a problem for me, but if you are unable to get into the BIOS on your  system without first booting Windows 8, then you may want to reconsider  whether this is a wise idea.

So Ubuntu installation crashes boot of Windows? Maybe the Boot-repair will be useful then to fix it?

---

### Post by oldfred on 2013-12-04
If you have one of the few systems that only boots Windows, then you have to run the "buggy" repair from Boot-Repair.
You will want to make a full backup of the efi partition, before & after changes.
Boot-Repair renames shim to be the Windows file name, so UEFI thinks it is booting Windows. And then from grub you can boot the renamed Windows file. But updates to Windows later may cause issues, so have both a Windows repair flash drive and your Ubuntu live install handy at all times.

This is what it does:
 Then renamed /EFI/microsoft/boot/shimx64.efi to bootmgfw.efi
Actual Windows boot file, originally bootmgfw.efi.
/EFI/Microsoft/Boot/bkpbootmgfw.efi

   With the renamed file you cannot directly boot Windows from UEFI menu as it really is shim.

   To undo & to rename files to their original names, you just need to tick the "Restore EFI backups" option of Boot-Repair.

---

### Post by miniKOX on 2013-12-04
Ok...I can backup efi partition simply by mounting it and copying the files elsewhere, or do I need a special program?

>  You will want to make a full backup of the efi partition, before & after changes.
Why do I need to make a backup of this efi partition after Ubuntu installs? Does this installation MAY or may NOT cause problem?

---

### Post by oldfred on 2013-12-04
You can backup just the files, no special program. 
Having backups is one of the most important things you can do with any computer system. 
You already have backed up Windows? And have procedures to regularly backup your data? whether Windows or Linux.

 If you install your own system you are the system admin
Sysadmins: Everything they told you about backup WAS A LIE
[http://www.theregister.co.uk/2013/07/12/storagebod_monomyth/](http://www.theregister.co.uk/2013/07/12/storagebod_monomyth/)

      
 Backup windows before install - post by Mark Phelps
[http://ubuntuforums.org/showthread.php?t=2137439&p=12611710#post12611710](http://ubuntuforums.org/showthread.php?t=2137439&p=12611710#post12611710)
[http://www.macrium.com/reflectfree.asp](http://www.macrium.com/reflectfree.asp)
Another suggestion by srs5694
[http://www.runtime.org/driveimage-xml.htm](http://www.runtime.org/driveimage-xml.htm)

---

### Post by miniKOX on 2013-12-05
So I should backup my EFI partition, just in case if something, somehow would crash? If will crash, then run a liveUSB and paste previously copied files, and everything will return to previous, "normal" state, as it was before I installed Grub and made a mess, yes?

---

### Post by oldfred on 2013-12-05
That is why we have backups. :)

---

### Post by ralic on 2013-12-06
> **miniKOX said:**
> So Ubuntu installation crashes boot of Windows? Maybe the Boot-repair will be useful then to fix it?
Yes, what I observed is exactly as described in [Bug #1024383]("https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1024383") referred to from the [Community UEFI]("https://help.ubuntu.com/community/UEFI") page.

Boot-Repair did resolve the situation for me by creating the necessary efi entries to allow booting Windows 8 from grub.

---

### Post by ralic on 2013-12-06
> **oldfred said:**
> Boot-Repair renames shim to be the Windows file name, so UEFI thinks it is booting Windows. 

This is what it does:
 Then renamed /EFI/microsoft/boot/shimx64.efi to bootmgfw.efi
Actual Windows boot file, originally bootmgfw.efi.
/EFI/Microsoft/Boot/bkpbootmgfw.efi

Thanks for this.
Like a twit, I didn't make a backup of my EFI beforehand and while I appreciate that Boot-Repair corrected the situation for me, I'm happier now understanding what it did to solve it.

---

### Post by oldfred on 2013-12-06
I am not sure what logic Boot-Repair uses to run the "buggy" UEFI rename funtion, but seem to be seeing a lot of users that have it renamed and do not need it. Later when Windows updates its file the rename will have to be done again, so if rename not really required, best not to use it.

Rename is only required for those UEFI that have internally been hard coded to only boot the Windows efi file. That is against the UEFI standard and considered (by Linux community) bad practice. It does not seem to be a Microsoft requirement. Some vendors are updating UEFI/BIOS, so newer vendor UEFI may fix it also.

If you can directly boot the ubuntu entry in UEFI menu with secure boot on or off, then undo the rename. The rename is only for those that only boot Windows from UEFI menu. When files are renamed you boot the Windows entry but get grub menu.

       To undo & to rename files to their original names, you just need to tick the "Restore EFI backups" option of Boot-Repair.


 Windows UEFI install should  have backup of bootmgfw.efi here:
C:\Windows\Boot\EFI\bootmgfw.efi from a working Windows x86_64 installation.

---

### Post by miniKOX on 2013-12-07
Hello.

I have got yet one stupid question about EFI partitition. Oldfred, you have told, that is enough for me to copy the files from EFI partition in case of problems with booting systems after Ubuntu is installed.

>  You can backup just the files, no special program.

The quesstion that I have got is: how do I mount the EFI partiton, if there is no such option in Gparted?

>  To undo & to rename files to their original names, you just need to tick the "Restore EFI backups" option of Boot-Repair.


 Windows UEFI install should  have backup of bootmgfw.efi here:
C:\Windows\Boot\EFI\bootmgfw.efi from a working Windows x86_64 installation. 

Or is it enough to show a Boot-Repair a "bootmgfw.efi" file location to restore default Windows EFI partition?

---

### Post by oldfred on 2013-12-08
You should just be able to use Nautilus or the file manager. If efi partition not mounted it should show in left panel, but may not say efi partition. I go back and label all partitions so they mount by label, otherwise default mounts may be size, UUID or something else. 
I try to remember to label when I create partitions with gparted, but often forget that step and then use Disk Utility or now its is Disks in newer versions. I prefer gparted over the new disks tool for other partition changes.

I do not know if you have run Boot-Repairs backups or not. It tries to run backups whenever you do anything with it, so users have a way to recover. But I do not think it backs up the entire efi partition, just key boot files.

You can look in /var/log/boot-sav to see what Boot-Repair has saved.

---

### Post by miniKOX on 2013-12-15
>  You should just be able to use Nautilus or the file manager. If efi  partition not mounted it should show in left panel, but may not say efi  partition. I go back and label all partitions so they mount by label,  otherwise default mounts may be size, UUID or something else.

My EFI has a label, but I do not see this partition in Nautilus

---

### Post by oldfred on 2013-12-15
One work around is to use gparted or Disks (also as Disk Utility in some versions) to mount it. Then you will see it in Nautilus.  Parted shows it as boot, gdisk by ef00 and blkid shows labels.
Or manually mount it.
sudo parted -l
```
Number  Start   End     Size    File system  Name     Flags
 1      1049kB  316MB   315MB   fat32                 boot

```

sudo gdisk /dev/sda -l
```
Number  Start (sector)    End (sector)  Size       Code  Name
   1            2048          616447   300.0 MiB   EF00  

```
Mine is labeled so blkid will show labels and if mounted already
sudo blkid -c /dev/null -o list
      ```
 device     fs_type label    mount point    UUID
-------------------------------------------------------------------------------
/dev/sdd1  vfat    EFI      (not mounted)  7B30-5ACA

    
```

It may be mounted by fstab already as efi, so do not remount if mounted as it will not work
       sudo mkdir /mnt/myefi

 sudo mount /dev/sda1 /mnt/myefi
to list files & folders
ls -l /mnt/myefi

---

### Post by miniKOX on 2014-02-23
Hello and thank you all very much for help!

I finally managed to  successfully install Ubuntu, everything works fine, but I cannot boot  Windows. I copied the EFI partition as oldfred told, pluged Ubuntu USB  and run a Boot-Repair from this USB, with recommended options.
 My problem is, that I still can not boot Windows.

Could someone help me to fix this?

---

### Post by oldfred on 2014-02-23
Post link:
       Post the link to the Create BootInfo report. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)
Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration and diagnose advanced problems.

Do not say yes to "buggy" UEFI if Boot-Repair suggests that. Only if you have a system that will not boot anything but Windows is that required.

---

### Post by miniKOX on 2015-02-17
Thank You all for help.

I finally managed to make Windows and Ubuntu bootable: in Boot-Repair in advanced options I checked to "Reinstall GRUB", and as GRUB location I have choosen "sda" .

I do not remember if I checked somethinh else, as it was long time ago, but after that I have additional entry in GRUB with is "uefiboot.img" or something like that, from where I can boot Windows :D.

Once agian thank You all for help, thread is [SOLVED]

---

