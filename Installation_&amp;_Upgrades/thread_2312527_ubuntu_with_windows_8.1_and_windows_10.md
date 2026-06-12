---
title: "ubuntu with windows 8.1 and windows 10"
date: 2016-02-05
forum: Installation &amp; Upgrades
---

### Post by Kamrul08 on 2016-02-05
I'm fully new in Ubuntu and want to learn it. I've Windows 8.1 and Windows 10 installed in my 500 GB HDD and also three extra drive with essential data. I'v downloaded ubuntu-15.10-desktop-i386 and made a drive free to install it. I want to use Ubuntu with Windows 8.1 and Windows 10. So I need help how to install Ubuntu with Windows 8.1 and Windows 10. 
Regards.

---

### Post by oldfred on 2016-02-05
Unless system is very old and probably not able to run Windows 8, you should be using the 64 bit version of Ubuntu. ubuntu-15.10-desktop-amd64 Only the 64 bit version is UEFI capable.
       
 [http://www.ubuntu.com/desktop](http://www.ubuntu.com/desktop)

Is system UEFI or BIOS. 
And is Windows installed in BIOS or UEFI boot mode?
Post this from Ubuntu live installer in live mode, terminal (boot in same mode as Windows UEFI or BIOS):
sudo parted -l

    
What brand/model system or motherboard/cpu and what video card/chip?

---

### Post by Kamrul08 on 2016-02-05
Thanks for reply. 

<<< System Summary >>>
  > Mainboard : Gigabyte G41M-Combo
  > Chipset : Intel G41
  > Processor : Intel Core 2 Duo E8400 @ 3.00   GHz
  > Physical Memory : 4096  MB DDR3-SDRAM
  > Video Card : Intel(R) G41 Express Chipset (Microsoft Corporation - WDDM 1.1)
  > Hard Disk : TOSHIBA DT01ACA050 ATA Device (500GB)
  > Monitor Type : Samsung SyncMaster - 15 inches
  > Network Card : Attansic (Now owned by Atheros) AR8151 PCIe Gigabit Ethernet Controller
  > Operating System : Windows 8.1 Enterprise Professional 6.02.9200 (64-bit)
  > UEFI : No

---

### Post by grahammechanical on 2016-02-05
> ubuntu-15.10-desktop-i386 and made a drive free to install it.

In your hardware specification you only list one hard disk = Toshiba DT01ACA50. Windows will give a partition a drive label such as C:, D:, E:. But in Linux we call drives - drives and partitions - partitions. How many hard drives do you have?

If it is only one hard drive, have you created unallocated space for the 2 Ubuntu partitions that are needed? If the motherboard does not have a UEFI boot system then it has a BIOS boot system with MBR partitioning. That means you will have a limit of 4 primary partitions. How many partitions are being used by Windows 8 & 10?

Regards.

---

### Post by oldfred on 2016-02-05
With BIOS you have to work around the 4 primary partition limit.
And you then create one primary partition as the extended partition to use as a "container" for all the logical partitions you want to make.
With both Windows 8 & Windows 10 you need to have fast start up or always on hibernation off. 
You should already have it off if dual booting two Windows.
 Fast Startup off
[http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html](http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html)
[http://www.eightforums.com/tutorials/6320-fast-startup-turn-off-windows-8-a.htmlold](http://www.eightforums.com/tutorials/6320-fast-startup-turn-off-windows-8-a.htmlold)

If you converted to Windows proprietary or  SFS/dynamic type partitions not basic then you may have bigger issues on repartitioning.
      
 My laptop already has 4 primary partitions: how can I install Ubuntu?
[http://askubuntu.com/questions/149821/my-laptop-already-has-4-primary-partitions-how-can-i-install-ubuntu](http://askubuntu.com/questions/149821/my-laptop-already-has-4-primary-partitions-how-can-i-install-ubuntu)
Good advice on how to handle all four primary partitions used. - srs5694
[http://ubuntuforums.org/showthread.php?t=1686440](http://ubuntuforums.org/showthread.php?t=1686440)
Be sure to create recovery DVD(s) first. And a Windows repair CD.
HP tools partition discussion - similar for other vendor utility partitions:
[http://h30434.www3.hp.com/t5/Notebook-Hardware/Hp-Tools-Partion/td-p/228360](http://h30434.www3.hp.com/t5/Notebook-Hardware/Hp-Tools-Partion/td-p/228360)

---

### Post by Vladlenin5000 on 2016-02-06
And use 64-bit (amd64).

---

### Post by Kamrul08 on 2016-02-06
I’ve only one HDD with three Primary partitions, two Logical Partitions and Un-allocated space for Ubuntu. For your kind information I added screenshot with [**GParted**]("https://4.bp.blogspot.com/-Yy7mPqwuKng/VrYZ1o6kYhI/AAAAAAAAOYI/1vX6otY5SCQ/s1600/Partition-List-With-Gparted.png") and [**AOMEI partition Tool**]("https://3.bp.blogspot.com/-yTdZSsJENH8/VrYZ1unAs5I/AAAAAAAAOYE/qjAHQkWuK-0/s1600/Partition-List-With-AOMEI.png"). Probably my Motherboard supports UEFI but I won’t go to UEFI. I tried few times to install Ubuntu by this time. I’m in hesitation with **Install Ubuntu alongside Windows 10 (***I don’t know why only windows 10 here but not windows 8.1*) and **Something else** Options. I’ve got screenshots by this time. **[Screenshot 1]("https://2.bp.blogspot.com/-2HKKAbcVy1Q/VrYZ1J0W3uI/AAAAAAAAOYA/FdS9aSuAlvU/s1600/Installation-Type1.png"), [Screenshot 2]("https://3.bp.blogspot.com/-csNyJ6YNf7o/VrYZ0_PA1FI/AAAAAAAAOX4/xa2bMgd3_nM/s1600/Alongside-Windows.png"), [Screenshot 3]("https://1.bp.blogspot.com/-f1xoBYjKxfw/VrYZ06qEu7I/AAAAAAAAOX8/ZApn9WyQQlg/s1600/Installation-Type.png")**. Here is also my [**Power buttong settings**]("https://3.bp.blogspot.com/-4tDG1kijpgI/VrYa22cVH-I/AAAAAAAAOYQ/s9UI1oqIBQ0/s1600/My-Power-button-Settings.png"). 

I’ve some query.

[LIST=1]
[*]I want boot menu with three OS (Windows 8.1, Windows 10 and Ubuntu). Is it possible?
[*]Do I need three partition for Ubuntu (Root, Home, Swap) or not ? Is it Logical or Primary?
[*]Is there any advanced instruction for safety during installation?
[/LIST]

---

### Post by Vladlenin5000 on 2016-02-06
Let's start with your questions:

1. Yes, it's possible.
2. No, you don't need three, just two (Root and Swap) and Swap, although usually recommended to have some (2-4GB), arguably you're fine without it provided the system has enough RAM, let's say 8GB.
3. Yes, reason and common sense.


Additional comments:

1. Gigabyte G41M-Combo is BIOS only, therefore
1.1 - Windows can be installed in MBR partitioning only whereas Ubuntu don't care, therefore
1.2 - > With BIOS you have to work around the 4 primary partition limit.
2 - You have reached that limit already and because of that the unallocated space appears as "unusable".

I suggest you use a more streamlined partition scheme instead. With two Windowses (in BIOS mode) you need three partitions, a small shared boot partition (@oldfred, please correct me if this is wrong) plus one for each OS. It makes sense to have a separated (NTFS formated) data partition that can be shared by all, including Ubuntu but you can have more provided they're inside an extended partition. All partitions required for Ubuntu can be logical, i.e., live inside an extended (primary) partition whereas the ones for Windows must be primary.

---

### Post by Kamrul08 on 2016-02-06
> **Vladlenin5000 said:**
> Let's start with your questions:

1. Yes, it's possible.
2. No, you don't need three, just two (Root and Swap) and Swap, although usually recommended to have some (2-4GB), arguably you're fine without it provided the system has enough RAM, let's say 8GB.
3. Yes, reason and common sense.


I assumed it. Thanks.

> **Vladlenin5000 said:**
> 
[COLOR=#000000][I]With BIOS you have to work around the 4 primary partition limit.
[/I]
[/COLOR]
[COLOR=#000000]You have reached that limit already and because of that the unallocated space appears as "unusable".[/COLOR]

I've a primary partition (Drive **"other"** in screenshot above) with important data only. I don't care it is primary or logical. I can easily convert it to logical anytime. I need primary partitions only for Windows 8.1 and 10. So I can create two more primary partitions.

I've read [Elementary OS Freya In Dual Boot With Windows guide]("http://itsfoss.com/guide-install-elementary-os-luna/"). It recommends logical drive for swap and root and ext4 file system for root. I'm confused a bit. Which is better for my Ubuntu, Logical or primary? What about ext4?

---

### Post by Vladlenin5000 on 2016-02-06
As I mentioned before, Ubuntu/Linux doesn't care about primary or logical, Windows does. As such, Windows is the "limiting factor" you should account for.
EXT4 is the file system and it's the recommended one indeed. Again, Ubuntu/Linux is much more "versatile" than the other OS in a sense that it can be installed in a variety of different file systems (except proprietary ones) but the current consensus points to EXT4.

---

### Post by Kamrul08 on 2016-02-06
> **Vladlenin5000 said:**
> As I mentioned before, Ubuntu/Linux doesn't care about primary or logical, Windows does. As such, Windows is the "limiting factor" you should account for.
EXT4 is the file system and it's the recommended one indeed. Again, Ubuntu/Linux is much more "versatile" than the other OS in a sense that it can be installed in a variety of different file systems (except proprietary ones) but the current consensus points to EXT4.

Thanks a lot. 
So I decided to install Ubuntu in primary partition as you mentioned [COLOR=#000000]**streamlined partition scheme**.
[/COLOR]
The size of my [COLOR=#000000]Un-allocated space[/COLOR] is 24 GB. I'll make 4GB swap and rest will be root with primary and EXT4 formatted. If I'm wrong please rectify me. I'll feedback my result tomorrow after installed. [COLOR=#000000]

[/COLOR]

---

### Post by oldfred on 2016-02-06
Windows does not require the separate primary NTFS boot partition, but all default installs since Windows 7 include that.
The requirement is that Windows can only boot from a primary NTFS partition with the boot flag.

You will not be able to boot both Windows directly from grub's menu unless both Windows installs are in primary partitions and you copy/repair install each install so each install has boot files.
You will be able to boot Windows boot partition and from Windows choose which Windows to boot.

If you want to directly boot each Windows and they both are in primary partitions, you need bootmgr & /boot/BCD in both installs. That is what grub looks for to find a bootable Windows. Windows uses the boot flag to find the bootable Windows.

You probably do not have to reinstall Windows, but have to move boot flag & repair it to add boot files to second install.
 To get each MS to have its own boot loader make a primary NTFS partition and set its boot flag on, then install the 2nd product in it. Multibooters, Pictures here worth 1000+ words
[http://www.multibooters.co.uk/multiboot.html](http://www.multibooters.co.uk/multiboot.html)
A user who installed two windows & it worked to boot from grub directly
[http://ubuntuforums.org/showthread.php?t=1271600](http://ubuntuforums.org/showthread.php?t=1271600)

---

### Post by Kamrul08 on 2016-02-07
Thanks all, many many thanks. 
I could successfully installed **ubuntu-15.10-desktop-i386** alongside Windows 8.1 and Windows 10. But I've some question about boot menu editing as well as some basic information as I'm new Ubuntu user. Should I make new thread or Can I write here?

---

### Post by Vladlenin5000 on 2016-02-07
*I'm new Ubuntu user* and *boot menu editing* usually don't go well together ;-)

But you can ask, of course. Then I can tell you whether or not it's advisable.

---

### Post by Kamrul08 on 2016-02-07
> **Vladlenin5000 said:**
> *I'm new Ubuntu user* and *boot menu editing* usually don't go well together ;-)

But you can ask, of course. Then I can tell you whether or not it's advisable.


Thanks [Vladlenin5000]("http://ubuntuforums.org/member.php?u=1468732"). Now my boot menu is showing Windows 8.1 and 10 together in a menu, named **Windows 10 (loader); **attached screenshot with. After pressing on **Windows 10 (loader)** menu it goes to Windows boot menu to select Windows 8.1 and 10. Of course both windows are booting properly as well as Ubuntu. But  I want to edit boot menu to recreate it. 

For Example my boot menu will be like bellow.

1. Windows 8.1
2. Windows 10
3. Ubuntu

My Windows 8.1 partition contains **bootmgr** & **/boot/BCD** but Windows 10 contains only **bootmgr**, no /boot/BCD.

---

### Post by oldfred on 2016-02-07
This is the 32 bit version, is that what you intended? ubuntu-15.10-desktop-i386
The 64 bit version is ubuntu-15.10-desktop-amd64.

When you installed Windows 10 it put its boot files into the Windows boot partition or the NTFS with the boot flag. So Windows 8 boot files were overwritten.
You probably can copy /Boot/BCD to Windows 10 and grub2's os-prober will give you two boot options. Both may say Windows 10 in grub and BCD being same will show both. But then you can edit BCD to have one entry in each Windows install. Best to backup Windows boot files just in case.

---

### Post by Kamrul08 on 2016-02-07
> **oldfred said:**
> This is the 32 bit version, is that what you intended? ubuntu-15.10-desktop-i386
The 64 bit version is ubuntu-15.10-desktop-amd64. I've installed Ubuntu 32bit.


> **oldfred said:**
> 
[COLOR=#000000]You probably can copy /Boot/BCD to Windows 10 [/COLOR][COLOR=#000000]and grub2's os-prober will give you two boot options.[/COLOR]
 I copied [COLOR=#000000]/Boot/BCD to Windows 10 partition. But no changes, same boot menu I'm getting. [/COLOR]How to edit menu label or default booting?

> **oldfred said:**
> 
[COLOR=#000000]But then you can edit BCD to have one entry in each Windows install.[/COLOR]
 Should I edit it from windows or Ubuntu?

---

### Post by oldfred on 2016-02-07
You can only edit BCD from Windows.

Did you run this to update grub menu?
sudo update-grub

If you have two entries, but different boot stanzas you can copy those boot stanzas into 40_custom and edit at will the description, not boot details. Then if each works, you can turn off os-prober to eliminate the older entries.

       Copy the  entries from this:
sudo cp -a /boot/grub/grub.cfg /boot/grub/grub.cfg.backup
gedit /boot/grub/grub.cfg
Copy Windows boot stanzas to and edit descriptions you want:
gksudo gedit /etc/grub.d/40_custom
or:
sudo nano /etc/grub.d/40_custom
Then do:
sudo update-grub

Once you reboot and test entires to know they work:

   gksudo gedit /etc/default/grub
#Add this line:
GRUB_DISABLE_OS_PROBER=true
sudo update-grub

To edit files you can use sudo nano or gksudo gedit.

---

### Post by Kamrul08 on 2016-02-08
> **oldfred said:**
> You can only edit BCD from Windows.

I’ve edited Windows 8.1\boot\bcd and separated Windows 10 from Windows Boot menu. I’ve created same Windows 10\boot\bcd. So now I have single boot loader for each Windows (Windows 8.1 and 10). Finally I tested. When I press **Windows 10 loader** menu Windows 8.1 runs directly without showing Windows 10 option. That means, I could edit bcd successfully and my Windows 10 \boot\bcd will work also if I can add command to boot\grub\grub.cfg.

> **oldfred said:**
> 
[COLOR=#000000]Did you run this to update grub menu?[/COLOR]
[COLOR=#000000]sudo update-grub[/COLOR]

[COLOR=#000000]If you have two entries, but different boot stanzas you can copy those boot stanzas into 40_custom and edit at will the description, not boot details. Then if each works, you can turn off os-prober to eliminate the older entries.[/COLOR]

[COLOR=#000000]Copy the entries from this:[/COLOR]
[COLOR=#000000]sudo cp -a /boot/grub/grub.cfg /boot/grub/grub.cfg.backup[/COLOR]
[COLOR=#000000]gedit /boot/grub/grub.cfg[/COLOR]
[COLOR=#000000]Copy Windows boot stanzas to and edit descriptions you want:[/COLOR]
[COLOR=#000000]gksudo gedit /etc/grub.d/40_custom[/COLOR]
[COLOR=#000000]or:[/COLOR]
[COLOR=#000000]sudo nano /etc/grub.d/40_custom[/COLOR]
[COLOR=#000000]Then do:[/COLOR]
[COLOR=#000000]sudo update-grub[/COLOR]

I’m advanced user for Windows but fully new in Ubuntu. So I’m telling with shame that, I could do nothing you wrote above. But I copied **boot\grub\grub.cfg** file and attached it for you as a text file. Would please make me the file with the menu like below as well as tell me how to replace boot\grub\grub.cfg file?

[COLOR=#000000]1. Windows 8.1 (Default)[/COLOR]
[COLOR=#000000]2. Windows 10[/COLOR]
[COLOR=#000000]3. Ubuntu
[/COLOR]
I worked with syslinux.cfg, isolinux.cfg and made bootable ISO with graphical boot menu ([Screenshot]("http://4.bp.blogspot.com/-H7XZzpIPHts/VSKEcpr03tI/AAAAAAAANf8/E8NagkheGlk/s1600/Menu.png")). Is it possible make a boot menu like my screenshot?

---

### Post by oldfred on 2016-02-08
You do not (normally) edit grub.cfg.
> #
# DO NOT EDIT THIS FILE
#
# It is automatically generated by grub-mkconfig using templates


When you run sudo update-grub it recreates it overwriting any edits anyway. And that update is run on kernel or grub updates to system also.

But you edit 40_custom which is one of the script files that the sudo update-grub uses. And you can edit parameters in /etc/default/grub which also are used when you update-grub.

So in terminal run the commands posted.
But open both grub.cfg in editor and scroll down to find the Windows boot stanza(s). Be sure to include the last line in the stanza the is }. 
Then open the other editor in administrative or super user mode and paste the two Windows boot stanza into 40_custom. Change description which is before the leading { but do not edit anything between { and } unless otherwise directed.
Then run this to add new entries to grub.cfg. You should then have 4 Windows entries, the os-prober versions & your new edited versions at bottom of menu.
sudo update-grub

You can post just 40_custom after your edits if desired. Just be sure to use code tags or the # icon in advanced forum editor.

Your current grub.cfg only shows one Windows boot stanza?  If you have both bootmgr & /Boot/BCD in the other install os_prober should find both installs. Did you rerun sudo update-grub? 
Difference in boot stanza would be partition & UUID which we can manually edit but easier not to if os-prober can do it automatically.

---

### Post by Kamrul08 on 2016-02-09
> **oldfred said:**
> You can only edit BCD from Windows.

Did you run this to update grub menu?
sudo update-grub

If you have two entries, but different boot stanzas you can copy those boot stanzas into 40_custom and edit at will the description, not boot details. Then if each works, you can turn off os-prober to eliminate the older entries.

       Copy the  entries from this:
sudo cp -a /boot/grub/grub.cfg /boot/grub/grub.cfg.backup
gedit /boot/grub/grub.cfg
Copy Windows boot stanzas to and edit descriptions you want:
gksudo gedit /etc/grub.d/40_custom
or:
sudo nano /etc/grub.d/40_custom
Then do:
sudo update-grub

Once you reboot and test entires to know they work:


I applied the command and it showed successful massage. Now there are two "Windows 10 Loader" titles in my boot menu (attached screenshot). Windows 10 (loader) (on /dev/sda1) runs Windows 8.1 successfully but Windows 10 (loader) (on /dev/sda2) shows "**ntldr missing**" problem. I can't understand what is the problem. 

"**Windows 10 (loader) (on /dev/sda2)**" command is copied here.
[PHP]menuentry 'Windows 10 (loader) (on /dev/sda2)' --class windows --class os $menuentry_id_option 'osprober-chain-01D12924B7D1DA80' {    insmod part_msdos    insmod ntfs    set root='hd0,msdos2'    if [ x$feature_platform_search_hint = xy ]; then      search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos2 --hint-efi=hd0,msdos2 --hint-baremetal=ahci0,msdos2  01D12924B7D1DA80    else      search --no-floppy --fs-uuid --set=root 01D12924B7D1DA80    fi    parttool ${root} hidden-    drivemap -s (hd0) ${root}    chainloader +1}[/PHP]

---

### Post by oldfred on 2016-02-09
Make sure boot flag is on sda2 & run chkdsk on sda2 from Windows repair console.

The NTFS partition has a boot sector or PBR. That must have boot info in it, and chkdsk will usually repair that.
See previous link on a 1000+ words for graphical explanation.

---

### Post by Kamrul08 on 2016-02-10
> **oldfred said:**
> Make sure boot flag is on sda2 & run chkdsk on sda2 from Windows repair console.

The NTFS partition has a boot sector or PBR. That must have boot info in it, and chkdsk will usually repair that.
See previous link on a 1000+ words for graphical explanation.

I read the threads you advised and applied chkdsk command. But same result. Any better advice please?

---

### Post by oldfred on 2016-02-10
In testdisk is an option to create a new BS - boot sector or PBR.
[http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step#NTFS_Boot_sector_recovery](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step#NTFS_Boot_sector_recovery)
See #12 Boot_Sector recovery for screen you need to get to.

I believe that is the old XP type (ntldr), but then running chkdsk on that partition updates it to the newer version (bootmgr). 
Make sure boot flag is on that partition.

I actually ran chkdsk from a Windows 7 repair console on my XP install and that converted my XP's NTFS PBR to bootmgr. In testdisk you can compare backup BS to current BS and on 2nd page you could see bootmgr or ntldr in clear text, plus some other differences. I had to run chkdsk again from XP to fix it.

---

### Post by Kamrul08 on 2016-02-12
> **oldfred said:**
> In testdisk is an option to create a new BS - boot sector or PBR.
[http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step#NTFS_Boot_sector_recovery](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step#NTFS_Boot_sector_recovery)
See #12 Boot_Sector recovery for screen you need to get to.

I believe that is the old XP type (ntldr), but then running chkdsk on that partition updates it to the newer version (bootmgr). 
Make sure boot flag is on that partition.

I actually ran chkdsk from a Windows 7 repair console on my XP install and that converted my XP's NTFS PBR to bootmgr. In testdisk you can compare backup BS to current BS and on 2nd page you could see bootmgr or ntldr in clear text, plus some other differences. I had to run chkdsk again from XP to fix it.

At last I could fix the problem. Actually fixing boot issue in windows is very easy. But it's with Windows bootmgr. I wanted different one like Grub. Now I'm with Ubuntu Boot menu.

My procedure was-
1. I deleted Ubuntu at 1st with partition tool. 
2. I made Windows 10 partition active and applied "rebuild mbr" with partition tool.
3. Then I ran Windows repair with Windows 10 disk.
4. I installed Ubuntu. 
5. At last I modified grub.cfg to re-arrange and change menu titles. 

If you don't mind I want to ask again- how to change Ubuntu [Boot menu]("http://ubuntuforums.org/attachment.php?attachmentid=267208&d=1455037568") theme, like Font size and background color or image?

---

### Post by Nuno_Abreu on 2016-02-12
> **Kamrul08 said:**
> If you don't mind I want to ask again- how to change Ubuntu [Boot menu]("http://ubuntuforums.org/attachment.php?attachmentid=267208&d=1455037568") theme, like Font size and background color or image?
If you like to do this the GUI way, there's Grub Customizer for that. It's very simple to use. Run these commands in the Terminal:
```
[COLOR=#333333][FONT=Monaco]sudo add-apt-repository ppa:danielrichter2007/grub-customizer
[/FONT][/COLOR][COLOR=#333333][FONT=Monaco]sudo apt-get update
[/FONT][/COLOR][COLOR=#333333][FONT=Monaco]sudo apt-get install grub-customizer
```[/FONT][/COLOR][COLOR=#333333][FONT=Monaco]
[/FONT][/COLOR]

---

### Post by oldfred on 2016-02-12
I am not a fan of customizer. For a user who only wants a gui and some simple changes it may be ok. But it creates new scripts and modifies those. 
 Customizer has backups of original files
[http://ubuntuforums.org/showthread.php?t=2279347&page=3](http://ubuntuforums.org/showthread.php?t=2279347&page=3)

But to do it manually you have to edit files.

 How to: Create a Customized GRUB2 Screen that is Maintenance Free.- Cavsfan
[https://help.ubuntu.com/community/MaintenanceFreeCustomGrub2Screen](https://help.ubuntu.com/community/MaintenanceFreeCustomGrub2Screen)
[https://help.ubuntu.com/community/Grub2/CustomMenus](https://help.ubuntu.com/community/Grub2/CustomMenus)
[http://ubuntuforums.org/showthread.php?t=2076205](http://ubuntuforums.org/showthread.php?t=2076205)
[https://help.ubuntu.com/community/Grub2/Displays](https://help.ubuntu.com/community/Grub2/Displays)
Colors only edit
gksudo gedit  /lib/plymouth/themes/default.grub
sudo update-grub

---

### Post by Kamrul08 on 2016-02-13
> **oldfred said:**
> I am not a fan of customizer. For a user who only wants a gui and some simple changes it may be ok. But it creates new scripts and modifies those. 
 Customizer has backups of original files
[http://ubuntuforums.org/showthread.php?t=2279347&page=3](http://ubuntuforums.org/showthread.php?t=2279347&page=3)

But to do it manually you have to edit files.

 How to: Create a Customized GRUB2 Screen that is Maintenance Free.- Cavsfan
[https://help.ubuntu.com/community/MaintenanceFreeCustomGrub2Screen](https://help.ubuntu.com/community/MaintenanceFreeCustomGrub2Screen)
[https://help.ubuntu.com/community/Grub2/CustomMenus](https://help.ubuntu.com/community/Grub2/CustomMenus)
[http://ubuntuforums.org/showthread.php?t=2076205](http://ubuntuforums.org/showthread.php?t=2076205)
[https://help.ubuntu.com/community/Grub2/Displays](https://help.ubuntu.com/community/Grub2/Displays)
Colors only edit
gksudo gedit  /lib/plymouth/themes/default.grub
sudo update-grub

Thanks oldfred. Important links. I've successfully changed background wallpaper. But for font size, Terminal shows command not found (screenshot attached).

> **Nuno_Abreu said:**
> If you like to do this the GUI way, there's Grub Customizer for that. It's very simple to use. Run these commands in the Terminal:
```
[COLOR=#333333][FONT=Monaco]sudo add-apt-repository ppa:danielrichter2007/grub-customizer
[/FONT][/COLOR][COLOR=#333333][FONT=Monaco]sudo apt-get update
[/FONT][/COLOR][COLOR=#333333][FONT=Monaco]sudo apt-get install grub-customizer[/FONT][/COLOR]
```[COLOR=#333333][FONT=Monaco]
[/FONT][/COLOR]
Thanks. I didn't use it as a new user. But I'll try.

---

### Post by oldfred on 2016-02-13
I do not edit grub, other than adding my own custom entries and changing timeout so it only shows for 3 seconds. And for 3 seconds on screen not in my mind worth a lot of changes.

---

### Post by Kamrul08 on 2016-02-14
> **oldfred said:**
> I do not edit grub, other than adding my own custom entries and changing timeout so it only shows for 3 seconds. And for 3 seconds on screen not in my mind worth a lot of changes.

Yes, You are right. I'm pleased on that.

Please give me some useful links or eBooks to learn Ubuntu advanced. Basically I need how to install software offline/online, about command line, how to use bat file, various file extension & it's work etc. Though I'm advance user in Windows, but fully new in Ubuntu. I installed Ubuntu 1st time but don't know what to do, how to do?

---

### Post by oldfred on 2016-02-14
Some places to look, can be overwhelming at first. 
I was a major user of XP and did a lot of customizing, making boot slightly faster etc.
It took a while to learn new commands and new ways. 
I did find most of my Google searches on ways to fix or do things was here in forum. And I still click on threads with topic I know little about to learn more. So hanging out in forum can be useful, if you have time.

 A master thread on learning/books/terminal/bash/Linux etc
Linux Command Line Learning Resources - cortman
[https://help.ubuntu.com/community/CommandLineResources](https://help.ubuntu.com/community/CommandLineResources)
[http://ubuntuforums.org/showthread.php?t=1909108](http://ubuntuforums.org/showthread.php?t=1909108)
[https://help.ubuntu.com/community/UsingTheTerminal](https://help.ubuntu.com/community/UsingTheTerminal)
[http://blog.jdpfu.com/2014/12/28/learning-linux](http://blog.jdpfu.com/2014/12/28/learning-linux)
Lots of links on scripting in this thread
[http://ubuntuforums.org/showthread.php?t=1893106](http://ubuntuforums.org/showthread.php?t=1893106)
[http://lifehacker.com/learn-basic-linux-commands-with-this-downloadable-cheat-1552019180](http://lifehacker.com/learn-basic-linux-commands-with-this-downloadable-cheat-1552019180)
[http://www.nixtutor.com/linux/all-the-best-linux-cheat-sheets/](http://www.nixtutor.com/linux/all-the-best-linux-cheat-sheets/)
[http://linuxcommand.org/tlcl.php](http://linuxcommand.org/tlcl.php)

---

### Post by Kamrul08 on 2016-02-15
> **oldfred said:**
> Some places to look, can be overwhelming at first. 
I was a major user of XP and did a lot of customizing, making boot slightly faster etc.
It took a while to learn new commands and new ways. 
I did find most of my Google searches on ways to fix or do things was here in forum. And I still click on threads with topic I know little about to learn more. So hanging out in forum can be useful, if you have time.

 A master thread on learning/books/terminal/bash/Linux etc
Linux Command Line Learning Resources - cortman
[https://help.ubuntu.com/community/CommandLineResources](https://help.ubuntu.com/community/CommandLineResources)
[http://ubuntuforums.org/showthread.php?t=1909108](http://ubuntuforums.org/showthread.php?t=1909108)
[https://help.ubuntu.com/community/UsingTheTerminal](https://help.ubuntu.com/community/UsingTheTerminal)
[http://blog.jdpfu.com/2014/12/28/learning-linux](http://blog.jdpfu.com/2014/12/28/learning-linux)
Lots of links on scripting in this thread
[http://ubuntuforums.org/showthread.php?t=1893106](http://ubuntuforums.org/showthread.php?t=1893106)
[http://lifehacker.com/learn-basic-linux-commands-with-this-downloadable-cheat-1552019180](http://lifehacker.com/learn-basic-linux-commands-with-this-downloadable-cheat-1552019180)
[http://www.nixtutor.com/linux/all-the-best-linux-cheat-sheets/](http://www.nixtutor.com/linux/all-the-best-linux-cheat-sheets/)
[http://linuxcommand.org/tlcl.php](http://linuxcommand.org/tlcl.php)

Thanks oldfred. Very useful links. I've to give the time. I marked the thread **solved**.

---

