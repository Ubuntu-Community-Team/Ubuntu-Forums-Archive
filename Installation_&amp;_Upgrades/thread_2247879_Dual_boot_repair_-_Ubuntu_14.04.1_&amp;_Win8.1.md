---
title: "Dual boot repair - Ubuntu 14.04.1 &amp; Win8.1"
date: 2014-10-11
forum: Installation &amp; Upgrades
---

### Post by A4Skyhawk on 2014-10-11
I have been working on this for a few days after MUCH searching and T&E.  I am sooooo close, but need some help here.
I have a Lenovo C260 w/ pre-installed Win 8.1.  I shrunk the Win partition w/ Gparted to make room for 2 Ubuntu partitions (root and swap), and left the other 5 Windows partitions untouched.  I installed Ubuntu w/ Windows in UEFI status and Secure Boot enabled.  After installation, and a number of attempts at boot-repair, and after disabling the Secure Boot, I now get the Grub2 menu on computer bootup.  Both "Ubuntu" and "Windows Boot Manager (on /dev/sda2)" are shown, as well as "Advanced Options for Ubuntu" and "System Setup" are shown.  Ubuntu, Advanced Options, and System work as expected.  But when Windows is selected, there is a quick flash of the screen, followed by the reappearance of the Grub menu.  I know the Windows OS is OK as I was able to boot it many times in previous attempts during my T&E activities.
 Here is my latest Boot-repair report --- [http://paste.ubuntu.com/8537129](http://paste.ubuntu.com/8537129)
 and this is what the edit screen looks like for the Windows option on the Grub menu (couldn't figure how to get a screen shot, so this is my transcript of the contents):
 setparams 'Windows Boot Manager (on /dev/sda2)
           insmod part_gpt

       insmod fat

           set root = 'hdo,gpt2'

       if [ x$feature-platform-search-hint = xy ]; then

            search - -no-floppy - -fs-uuid - -set = root - -hint -bios=hd0,gpt2 - -hint-efi=hd0,gpt2 - -hint-

            baremetal=ahci0,gpt2 1879-D46B

       else

                     search - -no-floppy - -fs-uuid - -set = root 1879-D46B

           fi

           chainloader /EFI/Microsoft/Boot/bootmgfw.efi

 END
 TIA,
 A4Skyhawk

---

### Post by fantab on 2014-10-11
```
sda2: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  Windows 8/2012: FAT32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /EFI/Boot/bkpbootx64.efi /EFI/Boot/bootx64.efi 
                       /EFI/ubuntu/MokManager.efi /EFI/ubuntu/grubx64.efi 
                       /EFI/ubuntu/shimx64.efi 
                       /EFI/Microsoft/Boot/bkpbootmgfw.efi 
                       /EFI/Microsoft/Boot/bootmgfw.efi 
                       /EFI/Microsoft/Boot/bootmgr.efi 
                       /EFI/Microsoft/Boot/bootx64.efi 
                       /EFI/Microsoft/Boot/memtest.efi

sda3: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  Windows 8/2012: FAT32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /EFI/Boot/bootx64.efi /EFI/ubuntu/grubx64.efi 
                       /EFI/Microsoft/Boot/bootmgfw.efi 
                       /EFI/Microsoft/Boot/bootx64.efi

```
You have two ESP [Efi system partitions], only one ESP per HDD is recommended.
Either delete one ESP preferably [sda3] or just remove the 'boot' flag from the partition.

Run boot-repair again with selected option to '*Restore EFI backups*'. Then
Go to 'advanced menu - Grub Location, and select 'separate /boot/EFI partition' -- choose your sda2 partition.

Don't forget to boot your Ubuntu DVD/USB in EFI mode only: [https://help.ubuntu.com/community/UEFI#Identifying_if_the_computer_boots_the_Ubuntu_DVD_in_EFI_mod]("https://help.ubuntu.com/community/UEFI#Identifying_if_the_computer_boots_the_Ubuntu_DVD_in_EFI_mode")e

---

### Post by A4Skyhawk on 2014-10-11
According to gParted, sda3 has only a "hidden" flag.  Looks like I have to "delete one ESP"?  How to do this?

[http://imgur.com/Rz3z8PJ](http://imgur.com/Rz3z8PJ)

TIA,
A4Skyhawk

---

### Post by oldfred on 2014-10-11
Some systems hide a recovery esp/efi partition. I think your sda3 as LRS_ESP is ok as is, but really should not have grub installed into it. But  you also have sda7 showing as an efi partition.

With UEFI & gpt, gparted uses the boot flag to determine which partition is the efi or ESP partition. With BIOS and MBR it has a totally different meaning as which partition does Windows have more boot code and is an actual flag in the MBR's partition table.
Use gparted and remove boot flag from sda7. The UEFI spec supposedly allows multiple efi partitions, but have not seen any that work, yet. Only one efi partition per device or hard drive.

You also used Boot-Repair's rename.  That was used a lot for those UEFI that only boot Windows entry and before grub was updated to create a correct efi boot entry. But when rename was done Boot-Repair would create a new 25_custom Windows boot entry to boot the renamed Windows efi file. You do not have that, and grub is correctly finding the Windows entry which now is really grub, so you have a loop. 

       Always say no until proven that you only can boot Windows entry from UEFI menu.
buggy-kernel detected. Do you want to activate [Backup and rename Windows EFI files]? yes (if any choice fails, please retry with the other)

To undo & to rename files to their original names, you just need to tick the "Restore EFI backups" option of Boot-Repair.

Your original Windows efi file was renamed to this:

 /EFI/Microsoft/Boot/bkpbootmgfw.efi

But grub is booting the standard name, which Boot-Repair made a copy of grub.

 /EFI/Microsoft/Boot/bootmgfw.efi

---

### Post by A4Skyhawk on 2014-10-11
I used GParted and changed the flag for sda7 to msftdata.
I selected 'Backup and rename EFI files' in boot-rrepair.
Currently, the computer boots directly to Win.
If I hit F12 during a bootup, I get the 'Startup Device Menu' which shows options for Ubuntu and Windows Boot Mgr.  Selecting the later lauches Win as expected, and selecting Ubuntu
takes me to the Grub menu, where all options work as expected.
Praise all progress!  Now how can I get the Grub menu first on bootup???
BTW, I did the boot-repair with the 'Secure Boot' checked and unchecked and I see no difference in the bootup sequences.
Latest boot-repair report at 
  [http://paste.ubuntu.com/8541635/](http://paste.ubuntu.com/8541635/)
TIA,
A4Skyhawk

---

### Post by oldfred on 2014-10-11
It does not look like you have the secure boot kernels installed. But there is/was? a bug where with secure boot on, you could not boot Windows from grub menu. 
Normally if you check the secure boot in Boot-Repair it downloads the secure boot kernels and you boot with shim which has the same signing key as Windows.

I think Lenovo's will let you set Ubuntu as default. Some like HP & Sony require work arounds or can only boot from UEFI menu or one time boot key like you currently are using. 

Starting at line 9232, you see the boot options, I think it shows several as one is secure boot, one is UEFI, and one is one time boot only. Not sure if UEFI shows BIOS boot as options from its menu or not.

If you cannot change/choose ubuntu as first in UEFI menu boot options somewhere, you may be able to use efibootmgr. Note that Windows also resets on a regular basis or any maintenance to make it first.

Similar to Boot-Repairs output.
       modprobe efivars
sudo efibootmgr -v

 [http://linux.dell.com/cgi-bin/gitweb/gitweb.cgi?p=efibootmgr.git;a=blob_plain;f=README;hb=HEAD](http://linux.dell.com/cgi-bin/gitweb/gitweb.cgi?p=efibootmgr.git;a=blob_plain;f=README;hb=HEAD)
[http://software.intel.com/en-us/articles/efi-shells-and-scripting/](http://software.intel.com/en-us/articles/efi-shells-and-scripting/)


 You would first type sudo efibootmgr -v to get a list of boot options. Note the number associated with the Ubuntu entry -- for instance, it might be Boot0005. You'd then type sudo efibootmgr -o 5 to make "Ubuntu" (actually GRUB) the default boot loader. (You can specify a set of boot loaders to be tried in order, as in sudo efibootmgr -o 5,1,2 to use 5, then 1 if that fails, then 2 if both 5 and 1 fail.)

Other work arounds. Many seem to use the rename of bootx64.efi in the /efi/Boot folder. Some like rEFInd, but it is another boot loader to install and update, and some use the BCDedit, but then Windows uses the UEFI one time boot and reboots into Ubuntu.
      
 [http://ubuntuforums.org/showthread.php?t=2234019](http://ubuntuforums.org/showthread.php?t=2234019)
[http://askubuntu.com/questions/486752/dual-boot-win-8-ubuntu-loads-only-win/486789#486789](http://askubuntu.com/questions/486752/dual-boot-win-8-ubuntu-loads-only-win/486789#486789)
[http://askubuntu.com/questions/507013/windows-8-1-changes-boot-order](http://askubuntu.com/questions/507013/windows-8-1-changes-boot-order)

Not sure how similar your Lenovo is to others. Vendors often are very similar across similar models. Most posts are laptops, but internals may be very similar?
      
 Some Lenovos comes with a physical switch that enables you to select which graphics adapter to use.
 Lenovo Z510 Laptop & Ubuntu 
[http://ubuntuforums.org/showthread.php?t=2232124](http://ubuntuforums.org/showthread.php?t=2232124)
Installing GNU/Linux on a 2014 Lenovo Thinkpad X1 Carbon UEFI/BIOS suspend to RAM issue
[http://mako.cc/copyrighteous/installing-gnulinux-on-an-2014-lenovo-thinkpad-x1-carbon](http://mako.cc/copyrighteous/installing-gnulinux-on-an-2014-lenovo-thinkpad-x1-carbon)
Lenovo IDEAPAD Y410P -  In My BIOS I set Boot Legacy Support But i set Boot UEFI First. 
[http://askubuntu.com/questions/455503/dual-boot-windows-8-and-ubuntu-problem-uefi?noredirect=1#comment599330_455503](http://askubuntu.com/questions/455503/dual-boot-windows-8-and-ubuntu-problem-uefi?noredirect=1#comment599330_455503)
Lenovo s440
[http://ubuntuforums.org/showthread.php?t=2189531](http://ubuntuforums.org/showthread.php?t=2189531)
Lenovo Yoga 11s (Intel i5/Intel HD 4000)
Needed this: acpi_backlight=vendor 
[http://ubuntuforums.org/showthread.php?t=2188199](http://ubuntuforums.org/showthread.php?t=2188199)
[http://ubuntuforums.org/showthread.php?t=1911972](http://ubuntuforums.org/showthread.php?t=1911972)&
Yoga2
[http://bregmatter.wordpress.com/2014/01/16/the-future-looks-very-small/](http://bregmatter.wordpress.com/2014/01/16/the-future-looks-very-small/)
Lenovo Community Bios Access
[http://forums.lenovo.com/t5/IdeaPad-Y-U-V-Z-and-P-series/z580-can-t-access-bios-setup-or-boot-menu-after-changing-to/td-p/812737/page/2](http://forums.lenovo.com/t5/IdeaPad-Y-U-V-Z-and-P-series/z580-can-t-access-bios-setup-or-boot-menu-after-changing-to/td-p/812737/page/2)
Lenovo Active Protection System&#8482; &#8211; for hard drive
 [SOLVED] Lenovo Y580 with working bumblebee on 12.10 - NVIDIA 660M
[http://ubuntuforums.org/showthread.php?t=2137318](http://ubuntuforums.org/showthread.php?t=2137318)
screen brightness was 0 during installation, use f12
Lenovo Z580 laptop
[http://ubuntuforums.org/showthread.php?t=2112271](http://ubuntuforums.org/showthread.php?t=2112271)
[http://ubuntuforums.org/showthread.php?t=1543006&p=12710212#post12710212](http://ubuntuforums.org/showthread.php?t=1543006&p=12710212#post12710212)

---

### Post by A4Skyhawk on 2014-10-11
Thanks.  I have some reading to do!  Will have to resume this tomorrow morning.
I'm installing Ubuntu on my wife's new computer as the primary OS.  She will not be using the Win partition ever (and I have it on my dual boot computer, if Win is ever needed) - I'm just trying to preserve it since it is already 'there'.  I have the sense that there is not a one-time permanent fix that keeps Grub first.  Is that correct?

---

### Post by oldfred on 2014-10-11
If not using Windows, you should be able to make it permanent. Or as permanent as anything with Computers is.

And it depends a lot on vendor & model of system. Each seems a bit different even though UEFI is  a 'standard'.

I would still backup Windows completely just in case. And make a Windows repairCD or flash drive.
Some more reading for you. :)

       Backup windows before install - post by Mark Phelps
[http://ubuntuforums.org/showthread.php?t=2137439&p=12611710#post12611710](http://ubuntuforums.org/showthread.php?t=2137439&p=12611710#post12611710)
[http://www.macrium.com/reflectfree.asp](http://www.macrium.com/reflectfree.asp)
Another suggestion by srs5694
[http://www.runtime.org/driveimage-xml.htm](http://www.runtime.org/driveimage-xml.htm)


 Windows 8 UEFI repair USB must be FAT32, not for reinstall, just repairs
[http://www.eightforums.com/tutorials/2855-system-repair-disc-create-windows-8-a.html](http://www.eightforums.com/tutorials/2855-system-repair-disc-create-windows-8-a.html)
[http://www.winhelp.us/create-a-recovery-drive-in-windows-8.html#USB](http://www.winhelp.us/create-a-recovery-drive-in-windows-8.html#USB)
[http://social.msdn.microsoft.com/Forums/en-US/samsungpcgeneral/thread/e7ed293e-b565-44ee-a536-166dddf32205/](http://social.msdn.microsoft.com/Forums/en-US/samsungpcgeneral/thread/e7ed293e-b565-44ee-a536-166dddf32205/)
[http://www.ghacks.net/2012/11/01/how-to-create-a-windows-8-system-repair-disc/](http://www.ghacks.net/2012/11/01/how-to-create-a-windows-8-system-repair-disc/)

One user who only uses Ubuntu, buys a system with a hard drive and even before booting and configuring Windows, uninstalls hard drive and installs a SSD for Ubuntu. Then later reinstalls the Windows drive to sell computer with new Windows and no worry about any of his data on it.

---

### Post by A4Skyhawk on 2014-10-13
I tried modprobe efivars and sudo efibootmgr -v and still could not get the Grub2 menu first.  Here is my latest report  --  [http://paste2.org/ndfF4PxO](http://paste2.org/ndfF4PxO)
As I mentioned in a previous post, this computer/OS is for my wife and needs to be set up so that it boots to Ubuntu w/ minimal operator intervention.
In retrospect, that's how it was performing at the time of my OP.  The boot repair report is shown here  --  [URL="http://paste.ubuntu.com/8537129"]http://paste.ubuntu.com/8537129
What do I need to do to return to that setup?  
TIA,
A4Skyhawk
[/URL]

---

### Post by oldfred on 2014-10-13
You still show sda7 as efi partition. Is that a new summary report from Boot_repair?
If it is you need to remove boot flag from sda7 with gparted.

---

### Post by A4Skyhawk on 2014-10-14
Yes, that was a new report.
I changed the flag for sda7 (Ubuntu) to msftdata, then ran boot-repair.  
Boot-up goes directly to Win.  Here is the report from the boot-repair following change of sda7 flag:
[http://paste.ubuntu.com/8553129/](http://paste.ubuntu.com/8553129/)
TIA,
A4Skyhawk

---

### Post by oldfred on 2014-10-14
Can you choose ubuntu entry from UEFI boot choice or one time boot key?
You may see two ubuntu entries. One is grub and the other is shim.

Windows does like to reset itself as default and with any Windows maintenance it will then reset UEFI boot order to Windows first.

Some systems also require work arounds to even get ubuntu to boot. Those vendors have modified UEFI to only boot an UEFI entry that says Windows. But they will boot hard drive in UEFI mode, so a work around is copying grub and renaming bootx64.efi. If you cannot boot directly I can post or link to more details.

Boot-Repair did run the efibootmgr list, there are several. There is UEFI, UEFI secure boot, one time boot, not sure which listing is which.
BootOrder: 0000,0002,2001,2002,2003
Boot[COLOR=#ff0000]0000[/COLOR]* Windows Boot Manager
Boot0002* Windows Boot Manager
Boot0004* UEFI Generic Boot
Boot0005* UEFI IPV6 Network Boot
Boot0006* UEFI IPV6 Network Boot
Boot0007* Windows Boot Manager
Boot0008* UEFI Generic Boot

BootOrder: [COLOR=#ff0000]0001[/COLOR],0000,0002,2001,2002,2003
Boot0000* Windows Boot Manager
Boot0002* Windows Boot Manager
Boot0004* UEFI Generic Boot
Boot0005* UEFI IPV6 Network Boot
Boot0006* UEFI IPV6 Network Boot
Boot0007* Windows Boot Manager
Boot0008* UEFI Generic Boot
Boot0001* [COLOR=#ff0000]ubuntu.[/COLOR]

---

### Post by A4Skyhawk on 2014-10-14
When I boot the computer, it goes directly to Win8.1, unless I press F12 after the "Lenovo" screen.
Pressing F12 takes me to the Startup Device Menu shown here:  [http://imgur.com/Og1gF3F&bJt5CPd&T90buny#0](http://imgur.com/Og1gF3F&bJt5CPd&T90buny#0)
Selecting the first WBM lauches Win.
Selecting the first Ubuntu takes me to the GNU Grub menu shown here:  [http://imgur.com/Og1gF3F&bJt5CPd&T90buny#2](http://imgur.com/Og1gF3F&bJt5CPd&T90buny#2)
Selecting the second WBM or Ubuntu takes me to here:  [http://imgur.com/Og1gF3F&bJt5CPd&T90buny#1](http://imgur.com/Og1gF3F&bJt5CPd&T90buny#1)
At this screen I enter Exit, and the computer boots to Win and does not respond to F12.
At the GNU Grub screen, all 4 options work as expected.
TIA,
A4Skyhawk

---

### Post by oldfred on 2014-10-14
Cannot read error message.

In UEFI boot menu can you use arrow to move ubuntu entry that works to first in menu?
Even if you can Windows may reset it regularly.

Do not remember if other Lenovo users had to use efi file rename or were able to reset ubuntu entry as first. Did you check links posted to see how users did it?

---

### Post by A4Skyhawk on 2014-10-14
The Bios Startup Tab shows USBFDD, USBKEY, USBCDROM, CDROM, HDD:ST....., HDD:WBM, HDD:Ubuntu, HDD:WBM, HDD:Ubuntu, Network1.
The 4 lines HDD:WBM, HDD:Ubuntu, HDD:WBM, HDD:Ubuntu move up/down w/ the arrows as a block.

I read all the links here and at Lenovo.community re dual booting Lenovo and did not see any that addressed issues similar to mine.
However, this setup would be ideal for my needs:  
"After the installation, I was left with an option for Ubuntu and an option for Windows at the GRUB menu .
I tried the Ubuntu option and it worked fine.
I tried the Windows options and it didn't work.
I searched for what the problem might be and decided to try pressing F12 at startup before the GRUB menu popped up.
This gave me a different option to boot into Windows which was successful."  
This comes from post # 213, p22 of this thread:  [http://ubuntuforums.org/showthread.php?t=1911972&page=22](http://ubuntuforums.org/showthread.php?t=1911972&page=22)

---

### Post by oldfred on 2014-10-14
You can copy grubx64.efi into the /efi/Boot folder and rename bootx64.efi and make grub the bootx64.efi file. Then that should be one of the hard drive UEFI boot entries and you should be able to make it a default.

Some of the alternatives, some work better with some systems. But many seem to find the rename of bootx64.efi works.

 [http://ubuntuforums.org/showthread.php?t=2234019](http://ubuntuforums.org/showthread.php?t=2234019)
[http://askubuntu.com/questions/486752/dual-boot-win-8-ubuntu-loads-only-win/486789#486789](http://askubuntu.com/questions/486752/dual-boot-win-8-ubuntu-loads-only-win/486789#486789)
[http://askubuntu.com/questions/507013/windows-8-1-changes-boot-order](http://askubuntu.com/questions/507013/windows-8-1-changes-boot-order)

   **Systems that only boot Windows from UEFI. Work arounds -Often Sony & HP, maybe others**
Backup entire efi partition before making changes.
**A:** Manually rename files efi boot files in efi partition

 **a1**: Rename /efi/boot/bootx64.efi, copy shim or grub into /efi/boot and name it bootx64.efi  Then boot harddrive entry in UEFI menu.
**a2:**(this is the same as what Boot-Repair does in B:. Windows updates will cause issues and require redoing.
Rename /efi/Microsoft/Boot/bootmgfw.efi and copy grub or shim into /efi/Microsoft/Boot and name it bootmfgw.efi  Then boot Windows entry to boot to grub menu. You have to manually add a grub menu entry to boot renamed Windows efi file. Grub2's os-prober entry boots bootmfgw.efi entry which is now just grub, so it will not work.

    Users who manually moved efi files around see post #6
[http://ubuntuforums.org/showthread.php?t=2101840](http://ubuntuforums.org/showthread.php?t=2101840)
[http://ubuntuforums.org/showthread.php?t=2219452](http://ubuntuforums.org/showthread.php?t=2219452)
[http://ubuntuforums.org/showthread.php?t=2221498&p=13012109#post13012109](http://ubuntuforums.org/showthread.php?t=2221498&p=13012109#post13012109)

   **B:**Boot_Repair renames Windows bootmgfw.efi. But cannot boot Windows from UEFI only from grub menu  with bkpbootmgr.efi entry
Always say no until proven that you only can boot Windows entry from UEFI menu.
buggy-kernel detected. Do you want to activate [Backup and rename Windows EFI files]? yes (if any choice fails, please retry with the other)
To undo & to rename files to their original names, you just need to tick the "Restore EFI backups" option of Boot-Repair.

   Any rename either manually or with Boot-Repair of bootmfgw.efi will need to be redone after a Windows update as it will restore Windows files.

   **C: **Edit Windows BCD, one Alternative to Boot-Repairs rename to make shim have Windows name.
Some systems work better to register grub/shim from inside Windows - for those that keep resetting Windows as default
[http://askubuntu.com/questions/371559/grub-not-showing-on-startup-for-windows-8-1-ubuntu-13-10-dual-boot](http://askubuntu.com/questions/371559/grub-not-showing-on-startup-for-windows-8-1-ubuntu-13-10-dual-boot)
bcdedit /set {bootmgr} path \EFI\ubuntu\grubx64.efi
[https://coderwall.com/p/vfyqkg](https://coderwall.com/p/vfyqkg)

   **D:  **Use efibootmgr

 **d1**:  If Description has to be Windows then change UEFI description.
sudo efibootmgr -c -L "Windows Boot Manager" -l " \EFI\ubuntu\shimx64.efi"
**d2**:  Disable Windows in UEFI and only boot from rEFInd or grub. If Windows is #1
sudo efibootmgr -A -b 0001

 [http://linux.dell.com/cgi-bin/gitweb/gitweb.cgi?p=efibootmgr.git;a=blob_plain;f=README;hb=HEAD](http://linux.dell.com/cgi-bin/gitweb/gitweb.cgi?p=efibootmgr.git;a=blob_plain;f=README;hb=HEAD)
[http://software.intel.com/en-us/articles/efi-shells-and-scripting/](http://software.intel.com/en-us/articles/efi-shells-and-scripting/)
   **E:** Some install rEFInd which seems to be another workaround and has nice boot icons.
[http://www.rodsbooks.com/refind/index.html](http://www.rodsbooks.com/refind/index.html)
[http://www.rodsbooks.com/refind/secureboot.html](http://www.rodsbooks.com/refind/secureboot.html)
Now has a ppa to make it easy to install:
[http://www.rodsbooks.com/refind/getting.html](http://www.rodsbooks.com/refind/getting.html)

---

### Post by A4Skyhawk on 2014-10-15
I now get the GNU Grub menu on bootup.  The following steps were used (see Post #6, thread [http://ubuntuforums.org/showthread.php?t=2101840](http://ubuntuforums.org/showthread.php?t=2101840)):

 1) mount the efi partition
 Code:  
  sudo mount -t vfat /dev/sda2 /mnt
 2) create backups of your windows .efi files
 Code:   
 sudo cp /mnt/EFI/Boot/bootx64.efi /mnt/EFI/Boot/bootx64.efi.bkp
 sudo cp /mnt/EFI/Microsoft/Boot/bootmgfw.efi /mnt/EFI/Microsoft/Boot/Bootmgfw.efi.bkp
 3) Copy the ubuntu .efi file in it's place
 Code:
 sudo cp /mnt/EFI/ubuntu/grubx64.efi /mnt/EFI/Boot/bootx64.efi
 sudo cp /mnt/EFI/ubuntu/grubx64.efi /mnt/EFI/Microsoft/Boot/bootmgfw.efi
 4) Copy the ubuntu .efi file to the same location with a .grb extention, in case you need to use boot-repair in the future.
 Code:  
 sudo cp /mnt/EFI/ubuntu/grubx64.efi /mnt/EFI/Boot/bootx64.efi.grb
 sudo cp /mnt/EFI/ubuntu/grubx64.efi /mnt/EFI/Microsoft/Boot/bootmgfw.efi.grb
 END
 
I did not complete steps #5 thru 8 as I could not find a file in my /etc directory similar to that shown in step #5.
 Perhaps that is why I now cannot boot Windows?  The &#8220;Windows&#8221; options in both the Grub and the Startup Device Menu (F12) take me to the Grub menu only.
 Here is the boot-repair report following the above changes:  [http://paste.ubuntu.com/8566307/](http://paste.ubuntu.com/8566307/)

---

### Post by oldfred on 2014-10-15
I prefer not to do this:
sudo cp /mnt/EFI/ubuntu/grubx64.efi /mnt/EFI/Microsoft/Boot/bootmgfw.efi

That replaces the Windows efi boot file with grub, and you then should be able to boot Ubuntu even if system is one that only boots Windows.
But you then also cannot boot Windows directly from UEFI menu, only the renamed back up file. And you have to have added an entry to 25_custom like Boot-Repair does or 40_custom so you have an entry to boot the renamed Windows file. This was common before grub could correctly find an efi boot for Windows. But now grub2's os-prober correctly finds the bootmgfw.efi and adds that to grub menu. But if really grub you just have a loop.

Does the boot of the hard drive which should use bootx64.efi which is now grub work to boot to grub? If so undo the rename of Windows, and see if you can directly boot Windows from UEFI.

---

### Post by A4Skyhawk on 2014-10-15
This is what I did.  Must have messed up because it booted to Windows.  I was able to get to Ubuntu via F12:
1) mount the efi partition
 Code:  
  sudo mount -t vfat /dev/sda2 /mnt
 2) create backups of your windows .efi files
 Code:   
 sudo cp /mnt/EFI/Boot/bootx64.efi /mnt/EFI/Boot/bootx64.efi.bkp
 (skipped the code that was here)
 3) Copy the ubuntu .efi file in it's place
 Code:
 sudo cp /mnt/EFI/ubuntu/grubx64.efi /mnt/EFI/Boot/bootx64.efi
 (skipped the code that was here)
 4) Copy the ubuntu .efi file to the same location with a .grb extention, in case you need to use boot-repair in the future.
 Code:  
 sudo cp /mnt/EFI/ubuntu/grubx64.efi /mnt/EFI/Boot/bootx64.efi.grb
 sudo cp /mnt/EFI/ubuntu/grubx64.efi /mnt/EFI/Microsoft/Boot/bootmgfw.efi.grb
 END

Boot-repair report:  [http://paste.ubuntu.com/8567916/](http://paste.ubuntu.com/8567916/)

I have to say that, with the many changes that I have made, I&#8217;m not certain which of these files is exactly what they should be.  A "process flow chart" of files from boot, thru UEFI menu and GNU Grub menu, to Ubuntu and Win would really help me.  In the absence of that, should I "start over" populating the files in sda2?  How?
TIA for your patience,
A4Skyhawk

---

### Post by oldfred on 2014-10-15
Always best to have a backup before you start renaming thing. I do not know where you at if you do not know.

If you are booting Windows from UEFI not grub menu, then you must not have renamed bootmfgw.efi.

Many users have backed up bootx64.efi and copied grub or shim and rename that. Then they could set hard drive as default boot and that worked. The then should be able to boot Windows either from UEFI menu, one time boot key, or grub menu.

       Windows UEFI install should  have backup of bootmgfw.efi here:
C:\Windows\Boot\EFI\bootmgfw.efi from a working Windows x86_64 installation.
And from your Windows 8 repair flash drive you can reinstall Windows boot files. 

And you can always do a total uninstall and reinstall of grub to refresh grub.

These are the standard folders. I prefer not to modify the Windows one, if at all possible to boot any other way. 
      
 /EFI/Boot
/EFI/Microsoft/Boot
/EFI/ubuntu

I think /EFI/Boot only has bootx64.efi. My install did not create it. 
Windows has bootmfgw.efi & BCD which are the essential boot files plus language and other supporting files in its efi partition.
Ubuntu has grubx64.efi, shimx64.efi, and a grub.cfg that is just three lines to transfer with configfile entry to the actual grub.cfg in your install. There now are some files for signing key management, but we do not yet use that.

---

### Post by A4Skyhawk on 2014-10-21
Sorry for the long delay in responding.  In the meantime, I have started over to get back on track by:
 
a) reset/refreshed my Win 8.1 OS,
b) re-installed Ubuntu 14.04.1
c) ran boot-repair "report" only, shown here:"  [http://paste.ubuntu.com/8582104/](http://paste.ubuntu.com/8582104/)
d) saved all files in sda2 and sda3 (as .orig), while also adding the prefix "ZZZ" to the files in sda3 (on the suspicion that Win might go here to recopy and reload these files into sda2???).  
    Boot-repair [edit - "report" only] shown here [http://paste.ubuntu.com/8619465/](http://paste.ubuntu.com/8619465/)
e) followed the first 4 steps from post #6, thread [http://ubuntuforums.org/showthread.php?t=2101840](http://ubuntuforums.org/showthread.php?t=2101840)

 
1) mount the efi partition
Code: 
sudo mount -t vfat /dev/sda2 /mnt
2) create backups of your windows .efi files
(as explained above in d))
3) Copy the ubuntu .efi file in it's place
Code:
sudo cp /mnt/EFI/ubuntu/grubx64.efi /mnt/EFI/Boot/bootx64.efi
sudo cp /mnt/EFI/ubuntu/grubx64.efi /mnt/EFI/Microsoft/Boot/bootmgfw.efi
4) Copy the ubuntu .efi file to the same location with a .grb extention, in case you need to use boot-repair in the future.
Code: 
sudo cp /mnt/EFI/ubuntu/grubx64.efi /mnt/EFI/Boot/bootx64.efi.grb
sudo cp /mnt/EFI/ubuntu/grubx64.efi /mnt/EFI/Microsoft/Boot/bootmgfw.efi.grb
END
 
I now get the grub menu on bootup and can boot into Ubuntu, but selecting Win returns the grub menu. 
 If I press F12 on rebooting, I have 1 selection each for Ubuntu and Win.  Selecting either returns the grub menu.  (As I mentioned in post #15, if I could launch Win via F12, then problem solved!) 
I have not run boot-repair yet.
I also do not find a file similar to that which is referred to in step #5 of the referenced post #6.  
 

 What to do next?
 

 TIA,
 A4Skyhawk

---

### Post by ubfan1 on 2014-10-21
The 25_custom file is one you make yourself.  Usually, the Windows stuff is in a higher numbered file, but looks like the poster wanted to move it up in the grub menu. Have you turned off secure boot?  Bug 1091464 still is present and keeps grub from booting Windows (on some machines at least) when secure boot is on.

---

### Post by oldfred on 2014-10-21
This is the Windows boot file. Did you make a copy of it or rename it?

  /EFI/Microsoft/Boot/bootmgfw.efi 

You copied grub over it, so when UEFI boots Windows it really boots grub. But if you can boot Ubuntu from either ubuntu entry in UEFI or hard drive entry (bootx64.efi) which you also made as a copy of grub, then you do not have to rename the Windows efi file.

It used to be that the only way to boot was to rename bootmgfw.efi and from grub menu boot the renamed file. Boot-Repair would rename it bkpbootmfgw.efi and create a 25_custom Windows efi boot entry to boot that file. Back then grub2's os-prober would not create efi boot entries for Windows so it was the only fix available. But then we found Windows updates would of course overwrite bootmfgw.efi and only Windows would boot again. And the previous bkp... file would not be the newer copy and confusion may result. Or best not to rename Windows if at all possible.

Now we know most systems will boot the hard drive entry or bootx64.efi, so that is all that has to be renamed.

If you have the original Windows bootmgfw.efi file copy that back into the Windows efi folder.

---

### Post by A4Skyhawk on 2014-10-21
Ubfan1:  Secure boot and quick boot are off.  As are Win updates, hibernate, and sleep.  Win will never be used by my wife, so I am only trying to
retain it for my "emergency" needs, whatever they may be (I do use excel).

---

### Post by A4Skyhawk on 2014-10-21
Oldfred:  You asked:  "This is the Windows boot file. Did you make a copy of it or rename it?
/EFI/Microsoft/Boot/bootmgfw.efi ".  The original was saved as .orig as seen in the B-R report  [http://paste.ubuntu.com/8619465/](http://paste.ubuntu.com/8619465/).  
 

 You said : &#8220;If you have the original Windows bootmgfw.efi file copy that back into the Windows efi folder.&#8221;  So I did 'cp /mnt/efi/microsoft/boot/bootmgfw.efi.orig /mnt/efi/microsoft/boot/bootmgfw.efi'.
As a result, bootup now goes directly to Win.   

 F12 displays a menu w/ Ubuntu and Win; selecting Win launches Win; selecting Ubuntu returns grub menu w/ U and W options, both of which respond as expected.   
 

 Still looking for a way to bootup to Ubuntu w/o using F12.  Using F12 to get to Win would be OK.
 

 TIA,
 A4Skyhawk

---

### Post by oldfred on 2014-10-22
What computer is this?

Some vendors modify UEFI to only let you directly boot the UEFI entry with Windows in the description. But most let you boot hard drive. 
The hard drive boot entry is /efi/Boot/bootx64.efi.

So in many cases we can copy grub into /efi/Boot and rename bootx64.efi, rename grubx64.efi to be bootx64.efi and set UEFI to boot hard drive.

---

### Post by A4Skyhawk on 2014-10-22
The computer is a Lenovo C260, all-in-one.
 Just to make sure I understand what you're saying, what are you referring to here:  &#8220;Some vendors modify UEFI....&#8221; - is this a file, or is it the Startup Device Menu shown here? - [http://imgur.com/tuTgtR1](http://imgur.com/tuTgtR1)
 This image is what appears at F12 when /mnt/efi/microsoft/boot/bootmgfw.efi is the original file and /mnt/efi/boot/bootx64.efi is the grubx64.efi file.
 When /mnt/efi/microsoft/boot/bootmgfw.efi is the grubx64.efi file, I get the response that I describe in my post #21 above.

 

 &#8220;and set UEFI to boot hard drive.&#8221;  How do I do this?

---

### Post by oldfred on 2014-10-22
F12 is the boot menu, but in UEFI you should also see boot menu and may be able to change boot order. Perhaps in UEFI menu is a hard drive entry. I thought you should see that with f12 also?

Some vendors HP & Sony for sure internally modify UEFI. So even if UEFI shows ubuntu entry, you can never make it the default boot entry. It is internal code in UEFI that checks for Windows in the description.

I thought Lenovo let you change boot order.

Note that this is a pdf:
       Vendors violated UEFI specs - [http://hwe.ubuntu.com/docs/ubuntu-bios-uefi-requirements.pdf](http://hwe.ubuntu.com/docs/ubuntu-bios-uefi-requirements.pdf)
> Firmware should not enforce any boot policy other than the mechanism specified in Section 3 of the
UEFI 2.3.1 specification [UEFI 2.3.1]. Specifically, firmware should not modify boot behaviour de-
pending on the Description field of the EFI_LOAD_OPTION descriptor.

---

### Post by A4Skyhawk on 2014-10-22
So I guess I go w/ these options:

 1) To boot to grub (w/o going thru F12), and then to Ubuntu, copy grubx64.efi into /mnt/EFI/Boot/bootx64.efi and /mnt/efi/microsoft/boot/bootmgfw.efi.
 2) On the infrequent occasion that I need Windows on my wife's computer, copy the original bootmgfw.efi into
 /mnt/efi/microsoft/boot/bootmgfw.efi
 

 Should I mark this thread 'solved'?
 

 Thanks for your help,
 A4Skyhawk

---

### Post by oldfred on 2014-10-22
If you can boot a hard drive entry that is the bootx64.efi which really is grubx64.efi, you do not have to copy grub over the Windows file. 

There are other work  arounds, some seem better on one brand or model system. But the rename bootx64 or rEFInd seem to be two better ones. I think renaming the Windows file is the last choice.

I think I have posted essentially the same info in each of these.
 [http://ubuntuforums.org/showthread.php?t=2234019](http://ubuntuforums.org/showthread.php?t=2234019)
[http://askubuntu.com/questions/486752/dual-boot-win-8-ubuntu-loads-only-win/486789#486789](http://askubuntu.com/questions/486752/dual-boot-win-8-ubuntu-loads-only-win/486789#486789)
[http://askubuntu.com/questions/507013/windows-8-1-changes-boot-order](http://askubuntu.com/questions/507013/windows-8-1-changes-boot-order)
[http://askubuntu.com/questions/244261/how-do-i-get-my-hp-laptop-to-boot-into-grub-from-my-new-efi-file](http://askubuntu.com/questions/244261/how-do-i-get-my-hp-laptop-to-boot-into-grub-from-my-new-efi-file)

---

### Post by A4Skyhawk on 2014-10-22
I haven't found anything that gives me what I am looking for.  But, I would like to try the steps after #4 in post #6, thread [http://ubuntuforums.org/showthread.php?t=2101840](http://ubuntuforums.org/showthread.php?t=2101840).
There are a couple similar threads using this approach.  But I don't know how to proceed.  Absent that, I will fall back to 
my post #29 above.
Thanks again,
A4Skyhawk

---

### Post by oldfred on 2014-10-22
I think the issue is do you have to copy grub over bootmfgw.efi to boot. 
If so then you can only boot Windows from grub menu. And then Windows updates will overwrite the copy of grub that has the Windows efi name, with a new Windows efi file and you have to copy grub again. Plus major grub update may need you to copy grub again.

As long as you have a backup and keep track of what is copied where, you should be ok.

---

### Post by A4Skyhawk on 2014-10-22
My needs probably are very atypical.  Primarily, because this application is for my wife's computer and I am attempting to keep it as simple as possible because she has little experience w/ navigating thru computer bootup procedures.  Therefore, the objective is to have a bootup that goes right to Ubuntu w/o any (or little) intervention; i.e., no requirement for <F12>.   I can satisfy this by saving grubx64.efi as /mnt/efi/boot/bootx64.efi and /mnt/efi/microsoft/boot/bootmgfw.efi.
Any attempts to boot into Win will require my intervention, and my cognizance to replace the bootmgfw.efi w/ the original.  Likewise a recognition that Win and grub updates may/will require some additional file manipulation.  But perhaps by then "Boot-Repair" will have cracked the code and be able to counter MS's/Lenovo's obstructionistic tactics!
Again, thanks fo your help.
A4Skyhawk

---

### Post by woodwardmw2 on 2015-07-31
I had this same issue today, installing Ubuntu on my parents' new Lenovo C260. Like you, I wanted to boot to Ubuntu, but still have Windows as an option in case we ever needed it.

This post, particularly your steps 1-4 in post #21, was very helpful in getting a solution that works for booting to GRUB and Ubuntu (although is less than ideal, thanks to the way Lenovo and Microsoft have set things up). By the way, I am able to access Windows via GRUB too, by selecting the "Windows Boot UEFI loader" option. The other Windows options re-cycle back to GRUB again as you described.

---

### Post by oldfred on 2015-07-31
Most systems will boot a hard drive entry using /EFI/Boot/bootx64.efi.

So better to just copy grub or shim into /EFI/Boot and rename either to bootx64.efi and boot hard drive entry in UEFI. You may have to add UEFI entry with efibootmgr if your UEFI does not have one.

Best not to rename Windows efi boot file bootmgfw.efi. First major Windows update will overwrite it and you have to copy again. Also good to have a way to directly boot Windows from UEFI.

Always backup entire ESP -Efi System Partion before making any changes.

More details on copy of /EFI/ubuntu into /EFI/Boot and renaming in link in my signature.

---

### Post by biozshock on 2016-01-12
As this thread is first in google's "lenovo ubuntu dualboot" i want to share my findings with those who are searching :)

I have a lenovo x1 2nd gen.
BIOS set up to use legacy **then** UEFI

Ubuntu 14.04 installed from legacy flahsdrive stick. Added 2mb partition reserved for bootup as installer had suggested.

After installation of ubuntu i went to grub's `/etc/grub.d/40_custom`
and added 
```
menuentry "Cuntinue to windows" {
    exit
}
```

This will exit grub with legacy boot and continue to use UEFI windows loader! :D

---

