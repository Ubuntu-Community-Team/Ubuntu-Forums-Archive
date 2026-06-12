---
title: "Ubuntu 14.04 installation via USB on UEFI + SSD-HDD part + NVIDIA drivers (Windows10)"
date: 2016-02-11
forum: Installation &amp; Upgrades
---

### Post by tanguy3 on 2016-02-11
[SIZE=3][SIZE=2]What got solved here (for total noobs, newbies or beginners) :
- adequate SSD & HDD partition (/ or /home /swap) & optimization for Ubuntu 14.04
- boot of Ubuntu 14.04 via UEFI (issues at first installation - screen becoming black)
- complete Ubuntu 14.04 installation (each step carefully)
- installation of NVIDIA drivers (latest version 352) for an adequate (& non-blurred) screen resolution.
[/SIZE][/SIZE]
Happy reading,
Best,
Tanguy
- [SIZE=3][SIZE=2]and a very big thanks to Oldfred for his very kind/patient help[/SIZE][/SIZE]

--------------------------------------------------
Hi ):P, 

As many here in this sub-section, I am eager to test ubuntu alongside my windows 10 (installed on a 240 Go SSD).
This SSD is already partitionned (Windows 10 occupying the largest partition), and a small 23.28 Go partition is currently RAW. there is currently a broken Debian OS on it (I'd like to erase it, but don't know yet how).


[LIST=1]
[*]Windows has probably being installed via UEFI (as there is a 100 Mb UEFI partition in disk management) - so I believe I need to install ubuntu via the "UEFI USB disk" option after having powered on the desktop with USB stick on it and repeatedly ticking F11. So far so good. 
[*]Then I get a screen with various options including "installing Ubuntu" - which I selected. 
[*]Then, an initial screen starts with sequential lines being "printed". Only 2 lines got printed, and then screen went black/powered off (because no signal), like nothing happened anymore. The USB stick light went off too, but the computer was still on. After a few minutes, I decided to switch it off. So far my Windows OS is still working-operational (and hope it will stay as such). 
[/LIST]

Any ideas on why it went wrong ?
Thx a lot for your help,
Best,
Tanguy


_Notes_:
- I carefully followed [http://www.ubuntu.com/download/desktop/create-a-usb-stick-on-windows](http://www.ubuntu.com/download/desktop/create-a-usb-stick-on-windows) in order to create an "Ubuntu USB booting stick".
- the ISO image got directly downloaded via ubuntu (twice, incase the first one was corrupted)
- 2 different USB sticks got utilized
- I tried the first time to install ubuntu via the non-UEFI mode. It went further in the installation process (but no purple ubuntu screen though)

---

### Post by Nuno_Abreu on 2016-02-11
UEFI was always an enemy of Linux - I'd start by disabling it in the BIOS.
After it, you should boot the USB stick (not in UEFI mode, of course). After it, partition the hard drive well to not erase any existing partitions - you better use Gparted for resizing. 

After that, install Ubuntu on the free space you left on the Gparted process (by resizing, for example, the Windows NTFS partition: **NOT THE EFI ONE!**). Don't also forget to install the bootloader to the specified drive.
After install, reboot the computer - you should now see some entries to boot to the preferred OS.

If you have any doubts, feel free to ask!

---

### Post by ubfan1 on 2016-02-11
You should install Ubuntu in the same mode as Windows is installed, in this case, UEFI.  You have gotten grub to boot in UEFI mode, so your problems are probably video related.  Try the "nomodeset" option on the grub kernel line (type "e" to edit the grub commands, instructions are on screen, add the word nomodeset where "quiet splash" are, and reboot.  Search this forum for video or nomodeset for many other options to help specific problems.  It would help if you told us exactly what model PC you are using.  When you download, always use a hashcheck to ensure that the download is correct.

---

### Post by sudodus on 2016-02-11
Welcome to the Ubuntu Forums :-)

I can add a couple of links, that will be useful in general, and for ***UEFI*** and ***boot options*** in particular.

[Installation/FromUSBStick#UEFI](https://help.ubuntu.com/community/Installation/FromUSBStick#UEFI)

[Try Ubuntu (Kubuntu, Lubuntu, Xubuntu, ...) before installing it](http://ubuntuforums.org/showthread.php?t=2230389); boot options at post #7.

---

### Post by tanguy3 on 2016-02-11
Thx for your replies. 
_@nuno_abreu_, thx, but I feel I should carry on with this UEFI, since my Windows has been installed via this way (and it looks like basically being how the motherboard got configured). 
Let's say it would be my last option (formating everything and reset back everything after). I would have felt more comfortable with old-school Bios though.

_@sudodus_, thx, I will be checking your links.

_@ubfan1_, I agree with you, I believe I should install Ubuntu in the same mode as Windows is installed.
[I]
[B]It would help if you told us exactly what model PC you are using
[/B][/I]
The PC is a "bespoke" one (made by a pro though, not myself), but still make it more complex than if it was a standard factory one.
SSD :Kingston V300 240Gb SATA 3 , 
RAM :16GB, HDD : 4Tb with an 
Motherboard : MSI, X995 SLI Krait edition, MS-7885 
CPU : intel(R) Core(TM) i7-5820k CPU @ 3.30GHz processor, 3301 Mhz, 6 cores, 12 logic processors, Sata based, 
GPU : GTX970, 
Monitor : G-Master (4k resolution)
[I](Bios mode : UEFI)

[B]You have gotten grub to boot in UEFI mode, so your problems are probably  video related.  Try the "nomodeset" option on the grub kernel line  (type "e" to edit the grub commands, instructions are on screen, add the  word nomodeset where "quiet splash" are, and reboot.  Search this forum  for video or nomodeset for many other options to help specific  problems.
[/B][/I]
Re nomodeset option, I'll have a look - I just wonder if this is really "video related" since the initial USB boot seems to be stopped from straight the begining - but I'll have a look. add the  word nomodeset where "quiet splash" ; do you mean writing "quiet splash nomodeset" or replace "quiet splash" by "nomodeset" ?
[I]
[B]When you download, always use a hashcheck to ensure that the download is correct.
[/B]
[/I]Hashcheck - ok, I will have a look on what it means

---

### Post by oldfred on 2016-02-11
I prefer to replace quiet splash with nomodeset, but you can add it also.

By replacing you get to see the entire boot process. It posts timestamps and what it is doing.
But new systems are so fast, that it scrolls by so quick that you cannot tell much, unless it stops and then may be able to see what issue is.

If booting using the nVidia card, then you need nomodeset.

While this shows the old BIOS screen, futher down it shows booting with grub after install. But with UEFI you boot with grub and it is the same.
 At grub menu you can use e for edit, scroll to linux line and replace quiet splash with nomodeset.
How to set NOMODESET and other kernel boot options in grub2 - both BIOS liveCD & grub first boot ( also UEFI with grub) 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)

---

### Post by sudodus on 2016-02-11
Check that the md5sum matches the string at this link

[UbuntuHashes](https://help.ubuntu.com/community/UbuntuHashes)

Run ```
md5sum file.iso
``` with the actual file name of your iso file.

---

### Post by tanguy3 on 2016-02-11
@all, Thx a lot for all your directions - there is quite a bit of information, and study/ work to do... I'll come back asap.

---

### Post by Nuno_Abreu on 2016-02-12
I'm pretty sure you can boot Windows from a legacy BIOS, even though it was installed via UEFI - it will basically ignore the EFI partition and the OS partition is the same.
UEFI is a pain because if you install an OS, the configuration files are overwriten and if you don't have a rescue CD or a live usb (especially when you install Windows after Linux) - then, it is difficult to get the original EFI options back.
I would leave the EFI partition alone - but it's okay that you try that way.

Also, if you have problems to boot the DVD on UEFI mode, you might have to try legacy mode - I think as long as the EFI partition is there, it will install in UEFI... But I'm not sure about this, please correct me!

---

### Post by oldfred on 2016-02-12
Both Windows & Ubuntu install in the boot mode that you boot install media.
So if you boot installer DVD or flash drive in UEFI it installs in UEFI.

Windows only boots in BIOS mode from MBR partitioned drives. And if drive was gpt it incorrectly converts it from gpt to MBR(msdos) leaving backup gpt partition table. Then Linux tools assume you want to erase drive as it is misconfigured. Fixparts will repair that issue.

I think if you try to boot Windows on BIOS mode from gpt drive it may erase drive, or just give error message. You cannot create the MBR bootable partition on the gpt drive.

I find UEFI easier as you can just back up the ESP - efi system partition and restore it to a FAT32 formatted partition with boot flag. No install programs required. And it is small so easy to back up to flash drive or any other device.

But UEFI like anything new is different, takes a bit for us to learn how to use, and is more complex both as it is UEFI and BIOS and because it offers more features.

---

### Post by tanguy3 on 2016-02-12
Ok, so I carefully went through all your propositions. Thx again. 

_@sudodus,_ thx for your links - there is a lot (feeling a bit swamped - but well, it's linux, so I spent a few hours on them, trying to figure them out). 
[LIST]
[*]Md5sum is the same (I used [https://help.ubuntu.com/community/HowToMD5SUM#MD5SUM_on_Windows](https://help.ubuntu.com/community/HowToMD5SUM#MD5SUM_on_Windows)) 
[/LIST]
[COLOR=#ff0000] 
[/COLOR]_@oldfred_ _@ubfan1_, I kept UEFI : USB option in the Grub menu, "e", replaced quiet splash

[LIST]
[*][COLOR=#008000]**Installation panel appears !** [/COLOR](... and it feels good :KS - video was the issue, you were right) 
[*]I would like to install Ubuntu on the broken Debian distribution (which is the only partition with an ext4 type) 
[*=1]so I would like to select /dev/sdb5 ext4 which already has a (broken) system on it (Debian GNU/Linux(7.9)and as Device for boot loader installation: /dev/sdb5 Debian GNU/Linux (7.9) 
[/LIST]
[INDENT][COLOR=#ff0000]Is that a good idea ?[/COLOR]**[COLOR=#ff0000] The issue being [/COLOR]**: [COLOR=#ff0000]I read that SSD needed to be erased first before having something being written back on it (unlike HDD). I wonder if the ubuntu installation cleans the drive before it writes back on it. I havent' pushed on "install now" button yet[/COLOR]
[/INDENT]

_@nuno_Abreu_, looks like UEFI works (so far)

Thanks again for your help
Best,
Tanguy

_Notes_ (done when going thru the various links, personnal comments, feedback, before trying out "nomodeset" - not sure if these points are still crucial regarding the current advancement):

[LIST]
[*]if I already see the Grub (I imagine this is the grub) with choices on  how to boot (and with a UEFI USB option), should I go thru the USB stick  creation again ? 
[*]on [https://help.ubuntu.com/community/Installation/FromUSBStick#UEFI](https://help.ubuntu.com/community/Installation/FromUSBStick#UEFI) - *Make the boot drive with Unetbootin, mkusb, Disks or the Startup Disk  Creator. (Some 'grub and ISO' systems work in UEFI mode, others work  only in BIOS mode.) *sounds to be key here*. *
[LIST]
[*]what about pendrivelinux.com - would it be Bios mode only ? It looks like it works so far... 
[*]unetbootin seems to be BIOS based only (sad, it looked so simple) 
[*]mkusb seems for Linux installations only (not usable under windows) 
[/LIST]
  
[*][https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)  - on the "Creating an EFI System Partition" point 2.3, my disk  partition already contains a 100Mb EFI partition. How could I check this  is FAT32 (I tried to find further info on disk management, but  none...)? What if it is not FAT32 ? 
[/LIST]

---

### Post by oldfred on 2016-02-12
Windows normally creates a 100MB ESP - efi system partition. A bit small, but room for Ubuntu's standard efi boot files. If later experimenting with multiple installs and UEFI boot options you may want to check amount used. If an ESP, it must be FAT32 with boot flag. Only one per device or hard drive, so do not create another. UEFI spec may allow more than one, but most UEFI implementations only work with one.

You can use this to see existing partitions.
sudo parted -l

I just overinstalled on my SSD a 15.04 install with 16.04. But I have 14.04 as main working install on same SSD and have trim enabled.
I used Something Else, choose old / (root) partition, ext4 and ticked format. If you have swap it auto finds it, so you do not have to do anything else. I actually have swap on both SSD & HDD and it adds both to fstab.

If you can boot installer in UEFI mode (you see grub not purple BIOS boot screen), the it must be working. Some installer or flash drives have in the past had issues.

---

### Post by tanguy3 on 2016-02-12
ok, so if I understand you well, it sounds possible to overwrite then.

 I just clicked on **install now** - having selected (as previously mentionned) **/dev/sdb5 ext4 **which already has a (broken) system on it (Debian  GNU/Linux(7.9)and as "*Device for boot loader installation:*" [B]/dev/sdb5  Debian GNU/Linux (7.9).
[/B]
and immediately a pop-up appeared :
             "No root file system
              No root file system is defined. Please correct this from the partitioning menu"

Mmmh, what went wrong ? Looks like there is sthg I haven't fully grasped yet...

---

### Post by ubfan1 on 2016-02-12
There are some drop-down selections to make on the selected partition, among them "use as"  then select "/" as root.
If the install fails for disk related errors, you can run the format on that partition, them from the live media's "try", fstrim the filesystem.

---

### Post by tanguy3 on 2016-02-12
Indeed, there was a need to double-click on it --> edit partition.
Sorry to take again a little bit from your time, but just to make sure, I guess I'd need to "**use as**:" a "Ext4journaling file system" (hesitating with "FAT32 file system") ?
I ticked "format the partition" box too btw...

---

### Post by oldfred on 2016-02-12
Device for grub Boot loader should always be a drive like sda, never a partition.

But with UEFI, grub only installs to the ESP on drive sda, so it really does not matter what you pick. But best to use correct as someday they may update install. Other Linux systems do let UEFI installs to other ESP or drives.

---

### Post by tanguy3 on 2016-02-12
@oldfred, Thank you very much for your patience, your time - am aware these questions could start to be a bit annoying,.. (I try to be fast)

Basically, on the main installation type table - the line     /*dev/sbd5 - ext4 - **/** - (Size 25000 MB, used 5338 MB) - blank* (strange because there is still some data on "used" - even if I previously ticked "format")     is now ticked.

But you mentionned sda as **device for** **boot loader installation** (which is actually the HDD, not the SSD - I just want to make sure this would be the right thing):[INDENT][I]/dev/sda ATA WDC WD4003FZEX-0 (4.0 TB)
/dev/sda2
/dev/sdb ATA KINGSTON SV300S3 (240.1 GB)
/dev/sdb1 Windows Boot Manager
/dev/sdb2
/dev/sdb3 
/dev/sdb4
/dev/sdb5
[/I][/INDENT]

sda still ? sdb hosts the SSD..

I read on ([http://askubuntu.com/questions/343268/how-to-use-manual-partitioning-during-installation/343352#343352](http://askubuntu.com/questions/343268/how-to-use-manual-partitioning-during-installation/343352#343352)) it was needed to add a further partition for **/home***. *Do you agree this would be needed ? I would therefore create a new partition table on the HDD (sda) for home - Would you recommend that too ?
I would then take exactly the same options as picked for the previous ones when edited (ext4) - even if my plan is to put an FTP device (total commander e.g.) in order to easily communicate files between both OS (Windows and Ubuntu) - the main storage remaining on Windows. ext4 would be still ok then ?

Thx again for your very kind help,
Best,
Tanguy

---

### Post by oldfred on 2016-02-12
The minute you partition and format a drive/partitions, it creates the ext4 structure and allocates 5% reserved space. So you should show some use.

I often suggest a separate /home for newer users. But if a brand new user it does add a bit of complication as you have to use Something Else or manual partiitoning. Since you already are using Something Else, probably a good idea. Many new users do not even know what a partition is as Windows has always referred to "drives" which may or may not be a drive.

But many of us use a data partition. Bit more advanced still. Since I only have Ubuntu installs, I use a shared ext4 partition for all data, but mount data in all installs. Back with XP, I had a shared NTFS data partition and a shared Linux formatted data partition. But data partitions cannot be created during install. I always create in advance and then mount in fstab after booting into install. Since some manual editing required, it is more advanced.

Do you have ESP - efi system partition on hard drive or only on SSD? One user did not have it on HDD which like yours was seen as sda. Then grub failed to install as it only installs to ESP on sda. Once he created the ESP on the hard drive then grub installed. 
I have installs on both sda & sdb, but even when I specify to use ESP on sdb, and installer even says it is installing grub to sdb, it overwrites my main ubuntu boot on sda. (quickly learned to backup ESP).

If installs are on same computer you do not use FTP. You just mount NTFS partition. With Windows 8 or later you must turn off the fast start or always on hibernation as Linux will not normally mount hibernated Windows. And if you write into hibernated Windows, when you go back to Windows the hibernation includes file structure, so it does not see any new files, or they are lost.

Best not to write into Windows system partition, but create and use a separate NTFS data partition. That still is mounted with Windows hibernation, but avoids issues that writing into system can create.

---

### Post by tanguy3 on 2016-02-12
creating a /home - ok, it shall be then. I'm indeed on "something else", so if it is best practice. I'd rather do it one for all - but well.
*" But data partitions cannot be created during install. I always create in  advance and then mount in fstab after booting into install. Since some  manual editing required, it is more advanced."*

So probably it would be better me to cancel/quit the current installation then ? The issue here being that the HDD is fully occupied by Windows... I guess this data partition could be performed on Windows (and when back to the installation, it would be ready). Is this correct ? If I quit the installation now, there won't be any wrong impact when coming back?


[LIST]
[*]I indeed only have a visible 100MB EFI partition on the SSD (HDD being fully NTFS) - (EFI & ESP are the same ?). So you would suggest I create a second 100MB-200MB EFI on the HDD ? I'll look for solutions about this.. 
[*]If root / on the SSD is on EXT4 format and /home on NTFS format for Ubuntu, wouldn't it create issues ? Maybe, I should keep it simple, and forget about this 
[*]What does "Mount NTFS partition" mean ? 
[/LIST]

---

### Post by oldfred on 2016-02-12
Mount is the process of seeing the data in a partition. It often is hidden as if you click on an unmounted partition it will auto mount.
In Windows you have to unmount a flash drive or it gives you warning/error messages as if it still is writing data, it can corrupt data or entire flash drive. Windows automounts all NTFS partitions it can see. 
Similar with Linux, but all drive partitions can be mounted, but not all are auto-mounted when you reboot. I mount several partitions in fstab which has all the default mounts like /boot/efi,  /,  & /home (if you have it). You then can add other default mounts. I then label partitions I do not mount in fstab with more useful labels that Windows d: or E:.  And then a default mount with nautilus uses label not the very long UUID.

Why is SSD seen as sdb? Was it only drive and you added the HDD?
I found that SATA port order controls which drive is first, and skipping a port can make it more confusing as flash drives or DVD get in the middle. So best to have UEFI boot on sda installed in SATA port 0 on motherboard.

What partitions do not now have on HDD?
Post this:
sudo parted -l

---

### Post by tanguy3 on 2016-02-12
ok - now I understand, thx - the flash drive example is a pretty good one...
You mention about fstab & sudo parted -l, the issue is I am still at installation type level (no access to terminal yet). Do you think I could do that after installation  (or install ubuntu multiple times - the first one being to create the adequate environment - the second one being the finalized one) ?

There is only one NTFS partition on the HDD 3725,90 Go (D: )[I]

Why is SSD seen as sdb? Was it only drive and you added the HDD?
[/I]Honestly, I don't really know,... the bespoke desktop is brand new - all components are brand new too - I did not add anything (sending an email to the seller to ask him further news).

---

### Post by oldfred on 2016-02-12
Seller may not even realize or know.

Windows really only likes to boot from first drive. But UEFI or BIOS defines which drive is first for booting & for a Windows install.

And boot drive is always hd0 in BIOS/grub, but can be any drive as seen once booted into Ubuntu. My old system I normally booted from sdc or sdd which was hd0 for booting in grub.

You can boot live installer in live mode and use terminal from that.
       Get a terminal by <ctrl_+alt+F1> & back to gui with ctrl alt f7
[https://help.ubuntu.com/community/UsingTheTerminal/](https://help.ubuntu.com/community/UsingTheTerminal/)
In Ubuntu you start a terminal window with ctrl + alt + t
or via the menu Program -- Accessories -- Terminal
Or with Unity search on Terminal

Boot installer in UEFI mode. And go to terminal.
Post this:
sudo parted -l

---

### Post by tanguy3 on 2016-02-12
ok, I got it now... I did not realize there was already access to a terminal (installation being not complete)
So :

Model: ATA WDC WD4003FZEX-0 (scsi)
Disk /dev/sda: 4001GB
Sector size (logical/physical): 512B/4096B
Partition Table: gpt

Number -  Start -  End   -   Size  -    File system  -  Name                                  - Flags
1            - 17.4Kb   - 134Mb -   134MB                         - - Microsoft reserved partition -       msftres
2            - 135MB -   4001GB -  4001Gb -    ntfs -               Basic Data partition -                 msftdata

Model: ATA KINGSTON SV300S3 (scsi)
Disk /dev/sdb: 240GB
Sector size (logical/physical): 512B:512B
Partition Table: gpt

Number -  Start -  End   -   Size  -    File system  -  Name                                  - Flags
1 -            1049kB  -106Mb    - 105mb   - fat32              - EFI system partition -                 boot 
2            - 106MB   -240MB    - 134Mb -                        Microsoft reserved partition       - msftres
3            - 240MB -   209GB    - 209GB -    ntfs                - Basic Data partition                 - msftdata
4            - 209GB   - 210GB     - 472MB   - ntfs - -                                                          hidden,diag
5            - 210GB   - 235GB     - 25.0GB  - ext4                                                           - - msftdata
6            - 235GB   - 240GB -     5340MB -  linux-swap(v1)

Model: USB Flash Memory (scsi)
Disk /dev/sdc: 16.1GB
Sector Size (logical/physical): 512B/512B
Partition Table: msdos

Number - Start - End    - Size - Type -    File system - Flags
1 -           512B -    16.1B -    16.1B  - Primary -   Fat32 -          boot

---

### Post by oldfred on 2016-02-12
Microsoft recommends the system reserved partition as a partition before any NTFS partition used to boot from. I do not think it is required for a data partition.
So, on your drive you should be able to convert the system reserved/reformat to an ESP - efi system partition, FAT32, with boot flag.
Then you can use Windows to shrink the large NTFS partition if you have data in it, or want to use it as a shared data partition.
And then either manually partition for / (root) & swap and maybe /home. But if you store most data in the NTFS partition /home does not have to be large or can be the standard default install of just / & swap. I normally use 25GB for /, but have system totally configure so all user data is in one of my data partitions, not in /. 
 UEFI install,windows 8 with Something Else screen shots
[http://www.everydaylinuxuser.com/2014/05/install-ubuntu-1404-alongside-windows.html](http://www.everydaylinuxuser.com/2014/05/install-ubuntu-1404-alongside-windows.html)
[http://www.everydaylinuxuser.com/2013/09/install-ubuntu-linux-alongside-windows.html](http://www.everydaylinuxuser.com/2013/09/install-ubuntu-linux-alongside-windows.html)
But I suggest using Windows to shrink Windows if installing on same drive and reboot Windows first. 
But do not create any partitions with Windows disk tools.
[http://www.dedoimedo.com/computers/dual-boot-windows-8-ubuntu.html](http://www.dedoimedo.com/computers/dual-boot-windows-8-ubuntu.html)
[https://help.ubuntu.com/community/DiskSpace](https://help.ubuntu.com/community/DiskSpace)

---

### Post by tanguy3 on 2016-02-13
So, I carefully went thru your valuable links (thx, again)

 in **disk management** (Windows), I shrinked 
- HDD space (-200 Go) - & in Ubuntu install I created /home
- SSD space (- 17406 Mb - having 16 Gb of RAM) - & in Ubuntu install I created swap area - [COLOR=#ff0000]btw couldn't be that SWAP space under HDD ?[/COLOR]

in Ubuntu install on SSD, I dedicated (25000Mb with broken Debian on it) to /

Device for boot loader installation : /dev/sdb - since that's where the SSD is located (/dev/sda being on the HDD).
Installation complete - "please reboot"
reboot - pushing F11 and oh surprise on "Please select boot device":

[I]- Windows boot manager (P6: Kingston SV300S37A240G)
- Debian (P6: Kingston SV300S37A240G) -[COLOR=#ff0000] I thought it was formated ?[/COLOR]
- ubuntu (P6: Kingston SV300S37A240G) - [COLOR=#ff0000]1[/COLOR]
- ubuntu (P6: Kingston SV300S37A240G) - [COLOR=#ff0000]twice ?[/COLOR]
- SATA6:Kingston SV300S37A240G
- SATA5:WDC WD4003FZEX-00Z4SA0
- SATA10: TSSTcorp CDDVDW SH-224F
- UEFI: Built-in EFI shell
- Enter set-up
[/I]
When pushing on "ubuntu" (the 1st one) - I took away the USB key.. 
Black screen, and on the bottom ; Welcome to GRUB!
(error: file not found. Entering rescue mode... grub rescue> _)

Is this expected ?

When pushing on "ubuntu" (the 2nd one) - (USB key still on it)
I typed e, and decided to change "quiet splash" with "nomodeset", and Ubuntu started up (login worked fine and so on).
[B]
sudo parted -l [/B][COLOR=#ff0000](in red, what changed from initial parted -l)[/COLOR]
Model: ATA WDC WD4003FZEX-0 (scsi)
Disk /dev/sda: 4001GB
Sector size (logical/physical): 512B/4096B
Partition Table: gpt

Number -  Start -  End   -   Size  -    File system  -  Name                                  - Flags
1            - 17.4Kb   - 134Mb -   134MB                         - - Microsoft reserved partition -       msftres
2            - 135MB -   4001GB -  4001Gb -    ntfs -               Basic Data partition -                 msftdata
[COLOR=#ff0000]3 - 3791GB - 4001GB - 210GB - ext4
[/COLOR]
Model: ATA KINGSTON SV300S3 (scsi)
Disk /dev/sdb: 240GB
Sector size (logical/physical): 512B:512B
Partition Table: gpt

Number -  Start -  End   -   Size  -    File system  -  Name                                  - Flags
1 -            1049kB  -106Mb    - 105mb   - fat32              - EFI system partition -                 boot 
2            - 106MB   -240MB    - 134Mb - -                        Microsoft reserved partition       - msftres
3            - 240MB - [COLOR=#ff0000]192[/COLOR]GB    - [COLOR=#ff0000]192[/COLOR]GB -    ntfs                - Basic Data partition                 - msftdata
[COLOR=#ff0000]7 - 192GB - 209GB - 17.4GB - linux-swap(v1)[/COLOR]
4            - 209GB   - 210GB     - 472MB   - ntfs - -                                                          hidden,diag
5            - 210GB   - 235GB     - 25.0GB  - ext4                                                           - - msftdata
6            - 235GB   - 240GB -     5340MB -  linux-swap(v1)

Model: USB Flash Memory (scsi)
Disk /dev/sdc: 16.1GB
Sector Size (logical/physical): 512B/512B
Partition Table: msdos

Number - Start - End    - Size - Type -    File system - Flags
1 -           512B -    16.1B -    16.1B  - Primary -   Fat32 -          boot

---------------
question :
1 - how can I clean GRUB (take out Debian + non-working Ubuntu(1))?
2 - how could I avoid putting "nomodeset" ? Please note my next (probably not in this thread) challenge will be to get a better screen resolution (since this one seems to be very basic - mentionning in case there is a link), and installing nvidia drivers might be required.
3 - since we are talking about windows 10 and reaching a quite adequate result, would be point 7 onwards from [http://www.everydaylinuxuser.com/2014/05/install-ubuntu-1404-alongside-windows.html](http://www.everydaylinuxuser.com/2014/05/install-ubuntu-1404-alongside-windows.html) still relevant (or might need to be adapted) ? 
4 - anything you would change in order to improve this setting (in order to avoid bad surprises) ?

Thx again for your help...
Best,
Tanguy

---

### Post by oldfred on 2016-02-13
First menu is the UEFI menu.
That has its own NVRAM and remembers all installs. Only if you disconnect a drive will it forget anything. So you need to use efibootmgr and remove extra entries.

You normally get two ubuntu entries. One grub & one shim where shim is the grub version for secure boot. Not sure why both as I thought shim worked if UEFI secure boot on or off.

UEFI may add entries back into its NVRAM if found in /EFI/ , so often best to houseclean those first. you may need live installer, or edit fstab, as new versions do not let you edit it unless you change mount back to defaults and reboot. 
These are different ESP - efi system partitions, so show different UUIDs. You must use your UUID for the ESP, and should only change the umask=0077 to defaults as shown in examples below.

 14.04 fstab entry defaults
UUID=FD76-E33D  /boot/efi       vfat    defaults        0       1
15.04 fstab entry umask=0077
UUID=68CD-3368  /boot/efi       vfat    umask=0077      0       1

sudo cp /etc/fstab /etc/fstab.backup
gksudo gedit /etc/fstab
or
sudo nano /etc/fstab
sudo mount -a

    
       sudo efibootmgr -v 
sudo efibootmgr -d /dev/sda #default is sda

   Delete entry change XXXX to correct entries. Some UEFI require all 4 HEX char, other just need 1 or 2 significant char.
sudo efibootmgr -b XXXX -B
Delete Ubuntu or any other entry you do not want or is invalid.
[http://ubuntuforums.org/showthread.php?t=2289179&p=13331743#post13331743](http://ubuntuforums.org/showthread.php?t=2289179&p=13331743#post13331743)

What video card/chip?
       
 # list drivers available, same list as system settings,  software updates,  additional drivers or last tab
ubuntu-drivers devices
# or
ubuntu-drivers devices | grep recommended

---

### Post by tanguy3 on 2016-02-14
ok, so, as far as I understand, even if some boot entries do not exist anymore, EFI menu acts a bit like a "log" too and everything could be cleaned thru "efibootmgr". 
*(*I like this line btw [I](sudo cp /etc/fstab /etc/fstab.backup))

... and should only change the umask=0077 to defaults as shown in examples below ...[/I]
_Result_ of when typing sudo nano /etc/fstab, the following page :

```
#<file system> - <mount point> - <type> - <options> - <dump> - <pass>
# **/** was on /dev/sdb5 during installation
UUID=e8861d68-bc3c-441f-b0e0-42565de508d1 - / - ext4 - errors=remount-ro - 0 - 1

# **/boot/efi** was on /dev/sd**b**1 during installation
UUID=0228-2F2B - /boot/efi - vfat - defaults - 0 -1 ([COLOR=#008000]it was already set to default[/COLOR][COLOR=#008000], I still did *sudo mount -a*[/COLOR])

# **/home** was on /dev/sda3 during installation
UUID=45691f53-69bf-4091-a078-8f4d2e5e0be4 - /home - ext4 - defaults - 0 - 2

# **swap** was on /dev/sdb6 during installation (there is a swap too much here - I need to find out if it is necessary for windows, or if it was part of the older Debian distro)
UUID=7bebf8b0-d284-4342-b6da-cb9c975a4161 - none - swap - sw - 0 - 0

# **swap** was on /dev/sdb7 during installation (swap 2)
UUID=a60baf06-39e3-404e-86fa-7d0741dc0fae - none - swap - sw- 0 -0


```---> this first part seems to be ok then.

sudo efibootmgr -v, fine.. (great links). 
*sudo efibootmgr -d /dev/sda #default is sda[COLOR=#008000] - during installation I specified my boot loader to be on sdb since representing SSD - should I change it to [I]sudo efibootmgr -d /dev/sdb ? not sure what was the purpose of this command...*[/COLOR][/I]
sudo efibootmgr -b XXXX -B worked like a charm (Debian & double Ubuntu are out - which is great - it looks clean now, it is very motivating)
 
ubuntu-drivers devices

```
 == /sys/devices/pci0000:00/0000:00:03.0/0000:05:00.0 ==
modalias : (...a lot of numbers...)
vendor : NVIDIA Corporation
driver : nvidia-352-updates - distro non-free
driver : nvidia-352 - distro non-free recommended
driver : xserver-xorg-video-nouveau - distro free builtin


```/Please note the main GPU is a nvidia geforce GTX-970

---

### Post by oldfred on 2016-02-14
With my SSD as sda & HDD as sdb, I have tried many times to specify grub with UEFI installs to install to my ESP on sdb. It even says during install if you watch closely, installing to sdb. But it always overwrites my default /EFI/ubuntu folder on sda.  I understand some other Linux distributions will install grub to sdb, but do not know where in grub settings or code that is.

My 14.04 install still used defaults in fstab, but newer installs all changed to 0077 and prevent editing fstab. And then when new install overwrote my working install, I could not change it back, until editing fstab back to defaults.

With an nVidia card you need the proprietary drivers.

It looks like -352 is recommended. Some want the very newest and add a ppa to get that, but see note here. You can just install from command line or in System Settings, Software & updates, drivers tab install the nVidia driver.

[https://launchpad.net/~graphics-drivers/+archive/ubuntu/ppa](https://launchpad.net/~graphics-drivers/+archive/ubuntu/ppa)

Do not attempt to install more than one or a different nVidia driver without totally purging the old one. And best to never install directly from nVidia with its .run file. Driver is integrated into kernel and init file system can only have one driver version.

I, for whatever reason, have swap on both sda & sdb. And only install / (root) to a drive. But it always adds both swaps to fstab. If I remember I comment out one or the other, but with 8GB of RAM I never have used swap. My old system with 4GB of RAM almost never used swap either, but RAM is now cheap, so I did 8GB on my build.

---

### Post by tanguy3 on 2016-02-14
Ok good to know about sda/sdb... especially when I'll upgrade. This is valuable - thx.

Concerning NVIDIA, ok, only one driver, and not downloading from Nvidia - alright. I went to your link - they recommend 352, as you do (currently running the benchmark btw), and I should be fine with 352, as much as I can get higher screen resolution (limited to 1024 * 768 (4:3))  & sound (currently not working).

I am not comfortable with linux language yet (my first linux  experience not so lately was with a raspberry pi - learned a bit, but environment was  very different - very enjoyable btw), would you confirm about the following commands (as I suppose the NVIDIA -352 is not installed yet because not identifying the Geforce GTX 970 *)? 

[LIST=1]
[*]sudo apt-get purge nvidia 
[*]sudo apt-get update 
[*]sudo apt-get install nvidia-352 
[/LIST]

* when typing lspci | grep NVIDIA, I get
05:00.0 VGA compatible controller: NVIDIA Corporation Device 13c2 (rev a1)
05:00.1 Audio device: NVIDIA Corporation Device 0fbb (rev a1)

----------------------

By the fact of having the adequate drivers installed, does it mean the replacement of "quiet splash" by "nomodeset" at ubuntu boot start won't be needed anymore ?

Thank you again for your help
Best,
Tanguy

---

### Post by oldfred on 2016-02-14
You should not need nomodeset on boot once nVidia driver is installed.

Those are terminal commads to install nVidia.
You should not need purge if no previous nVidia installed.

I have seen these mentioned also. # is a comment, not a command. Not sure if still required or not.
 # While you're at it upgrade libvdpau & nvidia-settings

And I recent saw this as a new way to install. Not sure what versions support this, now:


 sudo ubuntu-drivers autoinstall

---

### Post by tanguy3 on 2016-02-15
you mentionned that only one driver at a time --> sthg I seriously  consider. I previously broke my Debian OS because of that (the previous  Debian distro was actually a too light distro).

Even if I prefer  terminal, I did not manage to find "auto-install" specs, not knowing  what it would actually install (since you mentionned about the fact only  one driver at a time).
so I :
- went through the gui
- searched for "additional drivers" 
- waited a bit it updates the list 
- then chosed "using NVIDIA binary driver - version 352.63 from nvidia-352 (proprietary, tested)

I tried to install libvdpau (sudo apt-get install libvdpau), but no  success (E: Unable to locate package libvdpau). Wouldn't this library  come into conflict with nvidia drivers ?

Some splash error logo appeared on the side - so I decided to "restart" the computer:
_3 outcomes_ :
- I still had to change "[COLOR=#ff0000]quiet splash[/COLOR]" by "[COLOR=#ff0000]nomodeset[/COLOR]" -> which is a minor point of course, but well, if we can make it clean ... why not...
-  there was a new screen resolution - 3840*2160 (it's pretty small),  but I changed it back to a lighter screen resolution later on through  the GUI (system settings - display..)
- still no sound when going on  Youtube, but as drivers got installed, when clicking on the "sound" icon  on top right, sound setting appeared. On output, I picked the adequate  sound driver,... and magic came...

I re-did phoronix-tests (from  the launchpad link you shared - & of course I shared the results),  and everything seems to be fine.

I guess the next step would be to do stuff like [http://howtoubuntu.org/things-to-do-after-installing-ubuntu-14-04-trusty-tahr](http://howtoubuntu.org/things-to-do-after-installing-ubuntu-14-04-trusty-tahr) ...
-----------------

**@oldfred** _**thank you very much**_ for your help & your patience during these few days. I learned a lot.
It  was a quite long and steep learning curve for me (I actually had to  understand everything you mentionned - the reason why it took so long)  and frankly speaking, I'm exctatic.
You know the funniest is I'd  trust more this Ubuntu installation than this windows10 one (putting /  on the SSD & /home on the HDD is sthg I wish to automatically do on  Windows)

You provided very valuable advice re Windows10, Ubuntu  14.04, UEFI and all. If you are ok, I could restructure a bit the  initial thread, so it could be useful for similar requests - maybe I  could change the title thread... (since very general). Just let me know.

Best,
Tanguy

---

### Post by oldfred on 2016-02-15
You can edit thread & title.
And if [Solved], you can change that also. Many search forum or use Google which has forum and solved and good title help searches.

---

