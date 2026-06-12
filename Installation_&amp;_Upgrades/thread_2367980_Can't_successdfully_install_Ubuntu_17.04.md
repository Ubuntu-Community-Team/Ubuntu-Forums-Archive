---
title: "Can't successdfully install Ubuntu 17.04"
date: 2017-08-05
forum: Installation &amp; Upgrades
---

### Post by m3mpower on 2017-08-05
Hi Everyone

Need some help please
I have been trying to install Ubuntu for last two days, alongside Windows 10, but nothing.
When i restart the PC, it just boots to Windows 10.
I have followed Youtube videos but nothing.
Can someone help please?

I have Windows 10 installed on a SSD, i created a 30GB partition for Ubuntu, installed Ubuntu, i have changed boot order in BIOS, disabled secure boot, disabled fast boot,  and still the same problem, always boots to Windows 10.

Thanks

---

### Post by ajgreeny on 2017-08-05
You talk of the BIOS but most Win 10 machines use UEFI firmware not BIOS.

Can you confirm whether your machine uses BIOS or UEFI, and also that you installed Ubuntu in whatever manner Win 10 is installed.
If they are not both installed in the same manner you will always have the problem you speak of.

See **Boot-Repair** in my signature and follow the instructions there to run the **Boot-info script**.
Do not run the default repair just yet but simply show us the pastebin link you are given from running the script.

---

### Post by oldfred on 2017-08-05
Also what brand/model system?

---

### Post by m3mpower on 2017-08-05
> **oldfred said:**
> Also what brand/model system?

Hi

HP 500-415NS

Thanks

---

### Post by m3mpower on 2017-08-05
> **ajgreeny said:**
> You talk of the BIOS but most Win 10 machines use UEFI firmware not BIOS.

Can you confirm whether your machine uses BIOS or UEFI, and also that you installed Ubuntu in whatever manner Win 10 is installed.
If they are not both installed in the same manner you will always have the problem you speak of.

See **Boot-Repair** in my signature and follow the instructions there to run the **Boot-info script**.
Do not run the default repair just yet but simply show us the pastebin link you are given from running the script.

Hi

I talk of BIOS because thats where i have changed the boot order, because on a youtube video i have seen that the boot order must be changed and set priority to DVD Rom.
However i think my PC uses UEFI.
I don't know what you mean by "manner" of installation.
I know i have created a partition in my C drive and installed Ubuntu in that, that partition is not the last one, there is one after it, i don't know if that makes a difference

Thanks

---

### Post by oldfred on 2017-08-05
You do not have a c: drive except in Windows.
If is probably sda in Linux and then each partition is a number after the drive.
Windows mixes drives & partitions so d: drive in Windows may be another partition sda5 on the sda drive or sdb1 on a second actual drive.

HPs are not dual boot friendly. If you installed in UEFI modem, you may have to boot a fallback UEFI boot entry which may also be seen as a hard drive entry.
HP violates UEFI standard that says NOT to use description as part of UEFI boot. And only valid description is "Windows Boot Manager".
Boot-Repair in advanced mode will copy files, links below users had to manually copy files as they were before Boot-Repair copied files. Check the "Use the standard file" option.

       Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot, only use ppa download into Ubuntu live installer.
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
[https://sourceforge.net/p/boot-repair/home/Home/](https://sourceforge.net/p/boot-repair/home/Home/)

You may need an UEFI boot entry that used /EFI/Boot/bootx64.efi which is the fallback boot.
Post this after updates or post the full Summary Report from Boot-Repair which includes this.
sudo efibootmgr -v

       
 HP Probook 4545s Secure boot off, manually copy files.
[http://ubuntuforums.org/showthread.php?t=2133796](http://ubuntuforums.org/showthread.php?t=2133796)
HP Manually renamed files to make it work.
[http://ubuntuforums.org/showthread.php?t=2131886](http://ubuntuforums.org/showthread.php?t=2131886)

Similar instructions in link in my signature below:

 Copy shimx64.efi to /EFI/Boot/bootx64.efi
[http://ubuntuforums.org/showthread.php?t=2247186](http://ubuntuforums.org/showthread.php?t=2247186)
Boot-Repair should automatically do copy file with 'use standard EFI file':
[http://askubuntu.com/questions/150174/sony-vaio-with-insyde-h2o-efi-bios-will-not-boot-into-grub-efi](http://askubuntu.com/questions/150174/sony-vaio-with-insyde-h2o-efi-bios-will-not-boot-into-grub-efi)
Sony, HP & others:
[http://askubuntu.com/questions/486752/dual-boot-win-8-ubuntu-loads-only-win/486789#486789](http://askubuntu.com/questions/486752/dual-boot-win-8-ubuntu-loads-only-win/486789#486789)
Boot-Repair should automatically do copy file with 'use standard EFI file':
[http://askubuntu.com/questions/582073/dual-boot-but-only-windows-boots/582114#582114](http://askubuntu.com/questions/582073/dual-boot-but-only-windows-boots/582114#582114)
Rename bootx64.efi
[http://ubuntuforums.org/showthread.php?t=2234019](http://ubuntuforums.org/showthread.php?t=2234019)

---

### Post by m3mpower on 2017-08-07
Hi

I have done it again, this time by choosing "something else" instead of "install alongside Windows" and creating a partition Swap Area...( i followed a youtube video ).
When i hit "restart" it gave me the screen shown below.
But then i forced shut down, and when i restarted it came up with Grub, and it seems to be working OK.

My main reason for installing Ubuntu is to be able to partition and restore back ups into a CF card ( Windows wouldn't do it as it only recognises the first partition ).
I use Macrium Reflect for my back ups, but it won't install in Ubuntu.
What can i use instead ?

Thanks

[IMG]http://i187.photobucket.com/albums/x244/m3mpower/20170807_121950.jpg[/IMG]

---

### Post by m3mpower on 2017-08-07
Hi

I also forgot to mention that Ubuntu changes the time on my PC to 2 hours behind

---

### Post by oldfred on 2017-08-07
Are you installing Ubuntu or just creating live installer?
Live installer is like a DVD and can not be modified. So you cannot permanently make any changes.
But you should be able to install apps, if you have enough RAM, but then have to reinstall when you reboot. 
If you add persistence, you can save the download, but still have to reinstall apps.

One thread with time fixes, but many threads. But I think only works on full install.
[https://ubuntuforums.org/showthread.php?t=2321876](https://ubuntuforums.org/showthread.php?t=2321876)

 Backup windows before install - post by Mark Phelps
[http://ubuntuforums.org/showthread.php?t=2137439&p=12611710#post12611710](http://ubuntuforums.org/showthread.php?t=2137439&p=12611710#post12611710)
[http://www.macrium.com/reflectfree.asp](http://www.macrium.com/reflectfree.asp)
Another suggestion by srs5694
[http://www.runtime.org/driveimage-xml.htm](http://www.runtime.org/driveimage-xml.htm)
Microsoft Windows 8.1 reinstall/refresh
[http://windows.microsoft.com/en-us/windows-8/create-reset-refresh-media](http://windows.microsoft.com/en-us/windows-8/create-reset-refresh-media)

---

### Post by m3mpower on 2017-08-07
when i boot the pc from the usb drive where i saved the iso image with Rufus, i select the option INSTALL UBUNTU.
so as far as i know i am installing Ubuntu.
i just realised that it made one of my partitions on the C drive not readable , so its kind of messing things up this install.

it also seems macrium reflect cant be installed under Ubuntu.

i might give it another try from scratch and if it doesnt work then obviously ill just have to forget about Ubuntu.

thanks

---

### Post by oldfred on 2017-08-07
I do not think the one time I used Macrium, that it was from Ubuntu.
Many that want an image use Clonezilla, but I never have used it.
Ubuntu is normally so easy to install, that I just backup my data & configurations. But I did the same (only backup my data) with Windows XP years ago, but it was a lot harder to install & configure, and I had to backup serial numbers of any paid software.

 discussion of alternatives/strategy backups
[https://help.ubuntu.com/community/BackupYourSystem](https://help.ubuntu.com/community/BackupYourSystem)
[https://help.ubuntu.com/community/CategoryBackupRecovery](https://help.ubuntu.com/community/CategoryBackupRecovery)
[http://ubuntuforums.org/showthread.php?t=2236636](http://ubuntuforums.org/showthread.php?t=2236636)
[http://askubuntu.com/questions/2596/comparison-of-backup-tools](http://askubuntu.com/questions/2596/comparison-of-backup-tools)
If you install your own system you are the system admin
Sysadmins: Everything they told you about backup WAS A LIE
[http://www.theregister.co.uk/2013/07/12/storagebod_monomyth/](http://www.theregister.co.uk/2013/07/12/storagebod_monomyth/)
[http://www.smallnetbuilder.com/nas/nas-features/31745-data-recovery-tales-raid-is-not-backup](http://www.smallnetbuilder.com/nas/nas-features/31745-data-recovery-tales-raid-is-not-backup)

---

### Post by m3mpower on 2017-08-07
Hi

can i boot ubuntu from a USB ? without actually installing it on my C drive ?
so that whenever i want to use ubuntu i have to plug in my USB

thanks again

---

### Post by oldfred on 2017-08-07
You can use the Live installer from a flash drive in live mode, or you can do a full install to a 16GB or larger flash drive and still have some room for data partition.

I usually do a full install to my larger flash drives and also have ISO to boot other versions or repair ISO. On a small flash drive I may just install grub to directly boot ISO. 
Live installer will boot in either UEFI or BIOS, depending on what you select from UEFI.
Full install in BIOS is relatively easy to install as you can directly install grub to MBR whether drive is MBR or gpt partitioned.
Full install in UEFI requires a bit of copying and renaming of grub boot files from sda to flash drive's ESP as UEFI only boots from /EFI/Boot/bootx64.efi and with full install grub only installs to ESP on drive seen as sda.

 [http://askubuntu.com/questions/295701/what-would-be-the-differences-between-a-persistent-usb-live-session-and-a-instal](http://askubuntu.com/questions/295701/what-would-be-the-differences-between-a-persistent-usb-live-session-and-a-instal)
Pros & cons of persistence install over direct install to flashdrives - C.S.Cameron
[http://ubuntuforums.org/showthread.php?t=2133067](http://ubuntuforums.org/showthread.php?t=2133067)
[http://ubuntuforums.org/showthread.php?t=1655412](http://ubuntuforums.org/showthread.php?t=1655412)

---

### Post by m3mpower on 2017-08-08
Hi Oldfred

Well since i installed Ubuntu alongside Windows 10, i spent many hours and in the end it also made one of my partitions not accessible on my C drive, i'm still trying to fix that :mad:
So thats why i decided to not have it install on my main work PC because i need it to be "clean" and working...

Can you please recommend an option, my last option is to get a laptop with Windows 10 and just install Ubuntu on it and just keep it with Ubuntu.

The other option is to use a USB flash drive, i have 16gb and 32gb.
Can you post a link on how to do full install on USB flash drive please ?

Thanks

---

### Post by oldfred on 2017-08-08
New UEFI system or older BIOS based system.
Either way you have to use Something Else and you need to partition in advance.
See link in my signature for just about everything you need. But some additional links:

But UEFI needs gpt partitioning and an ESP - efi system partition (FAT32). UEFI only boots from an ESP and only from /EFI/Boot/bootx64.efi on external devices. But grub only installs to the ESP on the internal drive in /EFI/ubuntu.

 One advantage of partitioning in advance is that the installer will use the swap space to speed up the install. Thanks Herman for the tip. If installing to smaller flash drive, and have 4GB or more of RAM, you may not need swap as you will not be doing video editing or large database use. I suggest 2GB or none.
[https://help.ubuntu.com/community/DiskSpace](https://help.ubuntu.com/community/DiskSpace) 
      
 UEFI/gpt partitioning in Advance:
[URL="http://askubuntu.com/questions/743095/how-to-prepare-a-disk-on-an-efi-based-pc-for-ubuntu"]http://askubuntu.com/questions/743095/how-to-prepare-a-disk-on-an-efi-based-pc-for-ubuntu
[/URL]
 UEFI Full install to external USB drive or flash drive
[https://ubuntuforums.org/showthread.php?t=2338836](https://ubuntuforums.org/showthread.php?t=2338836) by Halbarad 

      
 Backup efi(ESP) partition and Windows partition before Install of Ubuntu. Only one efi partition per hard drive.
[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)
[https://wiki.archlinux.org/index.php/UEFI](https://wiki.archlinux.org/index.php/UEFI) 
    [URL="http://askubuntu.com/questions/743095/how-to-prepare-a-disk-on-an-efi-based-pc-for-ubuntu"]
[/URL]

---

### Post by m3mpower on 2017-08-08
Well obviously its too complicated for everyone since there is no simple instructions to follow for Windows 10.
I did do the swap area thing but as i said it made the partition next to it not accessible on windows.
Im not happy to risk the loss of my data while installing Ubuntu which seems to be an operating system only for the tech guys.
i'll look for a solution on google / youtube

Thanks anyway

---

### Post by oldfred on 2017-08-08
Windows cannot read Linux partitions. Swap is not a shared data partition but a space for use if you load too many programs into RAM and need more space. Often very slow then compared to RAM.
       17.04 Ubuntu To Begin Making Use Of Swapfiles In Place Of SWAP Partitions
[http://blog.surgut.co.uk/2016/12/swapfiles-by-default-in-ubuntu.html](http://blog.surgut.co.uk/2016/12/swapfiles-by-default-in-ubuntu.html)
no more than 5% of free disk space or 2GiB, whichever is lower.
[https://wiki.archlinux.org/index.php/swap#Swap_file_creation](https://wiki.archlinux.org/index.php/swap#Swap_file_creation)
[https://help.ubuntu.com/community/SwapFaq](https://help.ubuntu.com/community/SwapFaq) 
    
There are a few third party tools that may allow reading, but generally better to use NTFS for a shared data partition. The Linux NTFS driver works well.

---

### Post by m3mpower on 2017-08-09
Hi
The not accessible partition is not Linux, it was a NTFS partition that was created before I even installed Ubuntu. 
So I had my 500gb SSD which I split into 2 partition, C drive that had W10, and G drive which was for storage. 
When I installed Ubuntu, I pre created a partition for the install, I took 30gb from the C drive, so the G partition was not touched. 
After the install finished, my G drive was not accessible, do you know what I'm trying to explain?

---

### Post by oldfred on 2017-08-09
If Windows 8 or 10 fast start up is on which is hibernation, then Linux will not mount the partition to prevent damage. Also Linux will not mount a NTFS partition that needs chkdsk.

 Fast Start up off (always on hibernation)
[http://ubuntuforums.org/showthread.php?t=2324331&p=13488472#post13488472](http://ubuntuforums.org/showthread.php?t=2324331&p=13488472#post13488472)
[http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html](http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html)
[http://www.tenforums.com/tutorials/2859-hibernate-enable-disable-windows-10-a.html](http://www.tenforums.com/tutorials/2859-hibernate-enable-disable-windows-10-a.html)
[http://askubuntu.com/questions/843153/ubuntu-16-showing-windows-10-partitions](http://askubuntu.com/questions/843153/ubuntu-16-showing-windows-10-partitions)

---

### Post by m3mpower on 2017-09-02
Hi 
as per previous posts, i was trying to install Ubuntu alongside Windows 10 by creating a separate partition on C drive.
In the end i ended up installing Linux on a separate SSD, completely independant from Windows drive.
Now on my C drive, on the EFI system partition, i have a folder called "Ubuntu". ( i can see it in "partition minitool" ) ( see photo attached )
Is this normal? should i be worried?

Thanks

---

### Post by oldfred on 2017-09-02
That is standard.

Grub only installs to the ESP - efi system partition on drive seen as sda.
I do prefer to manually partition and include an ESP on all drives & copy boot files into that ESP more as a backup, but then maybe possible to boot that drive if sda fails for any reason.

---

### Post by m3mpower on 2017-09-02
Thanks for your reply.
What seems strange to me is that linux is installed on a different drive, so is it still normal that the Ubuntu folder goes into the Windows drive?

---

### Post by oldfred on 2017-09-02
Only if the Windows drive is seen as sda. But normally the Windows drive is sda.
With UEFI all boot loaders share the ESP.

---

### Post by m3mpower on 2017-09-02
So if I remove my Windows drive, I will not be able to boot into Linux?

---

### Post by oldfred on 2017-09-02
If you physically removed Windows drive, you have no ESP - efi system partition to boot from.
That is why I like to have an ESP on every drive. And copies of boot files/folders in ESP on every drive.

But if removing drive, you probably have to manually add a new UEFI boot entry using ESP on Ubuntu drive as internally UEFI has used the GUID of the ESP on the Windows drive to boot Ubuntu.
Relatively easy to do with Ubuntu live installer and an efibootmgr command to add new entry or houseclean old entries.

When you disconnect drives, UEFI's NVRAM forget entries from that drive.  UEFI seems to refind Windows entries if a Windows drive is then plugged in, but usually have to manually re-add Ubuntu entries.

---

### Post by m3mpower on 2017-09-02
Hi
Can you please tell me how to add EFI boot on the Linux drive? Does it have to be a FAT32?
I only hace 2 EXT4 partitions and a swap on the Linux drive.
I followed instructions in the link below ( although in my case it is a separate drive for Linux and not alongside Windows)

[https://itsfoss.com/install-ubuntu-1404-dual-boot-mode-windows-8-81-uefi/](https://itsfoss.com/install-ubuntu-1404-dual-boot-mode-windows-8-81-uefi/)

---

### Post by oldfred on 2017-09-02
How large is Linux drive?
Post this:
sudo parted -l

UEFI suggests ESP should be first partition, although most Windows installs seem to have a recovery partition first. I have seen some users but ESP further into drive, but those were not large drives. I would expect UEFI may not be able to find an ESP on a multiple TB size drive is not near beginning.

 It is recommended to use always GPT for UEFI boot as some UEFI firmwares do not allow UEFI-MBR boot. 
   For the Total space you want for Ubuntu:
Ubuntu's standard install is just / (root) & swap(prior to 17.10), but it is better to add another partition for /home if allocating over 30GB.:
Only if gpt -  all partitions in gpt are primary (no logicals):
gpt: 300-500 MB efi FAT32 w/boot flag (ESP for UEFI boot or future use for UEFI, you only can have one per drive, so if already existing do not attempt another)
gpt: 1 or 2 MB No Format w/bios_grub flag (for BIOS boot not required for UEFI)
for gpt(GUID) or MBR(msdos) partitioning
Ubuntu partitions - smaller root only where hard drive space is limited.
If total space less than about 30 to 50GB just use / not separate /home or standard install.


[LIST=1]
[*]20-25+ GB Mountpoint / primary or logical beginning ext4
[*]all but 2 GB Mountpoint /home logical beginning ext4
[*]2 GB Mountpoint swap logical (not required with 17.04 and later uses a swap file, if no swap partition found)
[/LIST]
    Depending on how much memory you have you may not absolutely need swap but having some is still recommended. I do not hibernate (boots fast enough for me) but if hibernating then you need swap equal to RAM in GiB not GB. And if dual booting with windows a shared NTFS partition is also recommended. But you usually cannot create that as part of the install, just leave some space. Or partition in advance (recommended).
One advantage of partitioning in advance is that the installer will use the swap space to speed up the install. Thanks Herman for the tip.
[https://help.ubuntu.com/community/DiskSpace](https://help.ubuntu.com/community/DiskSpace)
suggested partitions for just Ubuntu on 3TB drive.
[http://askubuntu.com/questions/336439/any-problems-with-this-partition-scheme](http://askubuntu.com/questions/336439/any-problems-with-this-partition-scheme)
Another advanced suggestion from TheFu with Multiple / (root) - Post #5 similar to what I actually do
[http://ubuntuforums.org/showthread.php?t=2170308](http://ubuntuforums.org/showthread.php?t=2170308)
[http://ubuntuforums.org/showthread.php?t=2021534](http://ubuntuforums.org/showthread.php?t=2021534)
UEFI/gpt partitioning in Advance:
[http://askubuntu.com/questions/743095/how-to-prepare-a-disk-on-an-efi-based-pc-for-ubuntu](http://askubuntu.com/questions/743095/how-to-prepare-a-disk-on-an-efi-based-pc-for-ubuntu)
More details:
[http://askubuntu.com/questions/336439/any-problems-with-this-partition-scheme](http://askubuntu.com/questions/336439/any-problems-with-this-partition-scheme)

---

### Post by m3mpower on 2017-09-03
> **oldfred said:**
> How large is Linux drive?

120GB SSD

[/QUOTE=Post this:
sudo parted -l[/QUOTE]

OK i will do this in next post

[/QUOTE=UEFI suggests ESP should be first partition, although most Windows installs seem to have a recovery partition first. I have seen some users but ESP further into drive, but those were not large drives. I would expect UEFI may not be able to find an ESP on a multiple TB size drive is not near beginning.[/QUOTE]

In Windows 10 the first partition is the 450mb recovery, then the 99mb EFI system, then C drive.
My Linux install is on a separate SSD, not the Windows drive.
i'll attach some photos of the partitioning
Thank you

[ATTACH=CONFIG]276577[/ATTACH][ATTACH=CONFIG]276578[/ATTACH][ATTACH=CONFIG]276579[/ATTACH]

---

### Post by m3mpower on 2017-09-03
As for sudo parted -l here are the results

Thanks[ATTACH=CONFIG]276580[/ATTACH]

---

### Post by oldfred on 2017-09-03
You now have ESP on sdb, not on sda.
And grub only installs to ESP on drive seen as sda.

It may be easier just to switch drives in SATA ports.
Best to have Windows drive in SATA0 and each drive in next SATA port skipping none. 

You may want to add an ESP to current sdb, but just need to shrink any partition and create a new FAT32 partition with boot flag.

---

