---
title: "Aspire ES1-533 dual boot snark"
date: 2018-03-06
forum: Installation &amp; Upgrades
---

### Post by highballmint182 on 2018-03-06
I am on a quest to solve this thing. I have tried many times to get a simple dual boot going on the same drive, unsuccessfully. I have what appears to be the same setup as another poster on a very similar thread, except for the UEFI bios, which did successfully update, but no change in application:
 
 
[LIST]
[*] 500 GB HDD on Aspire ES-1533, Apollo Lake processor, chipset and south bridge. 
[*] Main board =Acer Stego_AP, Windows 10 pre-installed and re-installed 
[*] UEFI [BIOS] InsydeH20 setup utility rev5.0, ver 1.12 [UEFI bios] 
[*] GPT, UEFI = enabled, secure boot = re-enabled 
[*] (U)EFI partiton = gone [in Windows 10] 
[*] fastboot = disabled 
[/LIST]

Big part of the problem is I enter EUFI bios, then:
 
[LIST=1]
[*] go to "Set Supervisor Password" press ENTER (I set pass "a") check, good     there. 
[*] no menu entry for &#8220;select an UEFI file as trusted for executing:" 
[*]  no matter what I do no new page appears with listed hard drives: 
[/LIST]
 - HDD0
 - HDD0

 "Select an UEFI file as trusted for executing" is not an option in my bios. Also, I can&#8217;t press ENTER on the first HDD0 since no sub list with the name "<EFI>" comes up. Since no sublist comes up, no shimx64.efi, grubx64.efi or MokManager.efi are there. This was true on both UEFI bios setups.   

 This all appears to be unique to the Acer Aspire ES1-533 [I call it the ES-1533, but no difference] I have tried for over 3 weeks to get a simple dual boot going on this machine, tried many different suggestions, variations and setup routines. Still no dual boot.  

 My installs always hang up at the same place too, during grub installation. ALWAYS fails. Plus, I only see this next thing for less than a second, but after grub v2.02 [beta] comes up when booting from USB stick, there are lines saying that there's "a problem loading EFI files", "no caching mode page found", "assuming drive cache - write through" or something like that, I can't get the code that goes by too fast for me to read them.  

 That sounds messed up, so I checked the EFI and Recovery partitions in Windows, and they were not mounted, empty when I finally did get them mounted. Somehow, they were borked, either from installation or from the UEFI bios and turning fast boot and secure boot on and off too much, or some other thing.  Any hoo, I reinstalled Windows to get the partitions back, successfully. I am going to go a little slower now so I don&#8217;t have to redo that again, but so far all installation attempts have stalled at the same place, while setup was installing grub loader. There are some fantastic threads and help here, I hope I have provided a little more information to help with the solution. And I really need the help!!

---

### Post by oldfred on 2018-03-06
Some have had issues with format of ESP - efi system partition which is FAT32.
It does not have lock, but some have seen it where grub could not write to it.
Often then chkdsk from Windows or dosfsck from Linux fixed it.

In a few cases users backed up entire ESP, deleted it. Then created new FAT32 partition with boot flag to make it ESP. And restore boot files.
But new UEFI entries may be required as UUID & GUIDs get changed with new partition.

 Must be unmounted or from live installer.
sudo parted -l
sudo dosfsck -t -a -w /dev/sdXY
Where X is drive like a from sda, and Y is partition like from sda1. Your may be sda2 or some other partition.
The -a seems to help in clearing dirty bit
[https://bbs.archlinux.org/viewtopic.php?id=164185](https://bbs.archlinux.org/viewtopic.php?id=164185) 

Just to confirm install is correct.

 May be best to see details, you can run from your Ubuntu live installer or any working install, use ppa version not older Boot-Repair ISO:
Post the link to the Create BootInfo summary report. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info) and:
[https://sourceforge.net/p/boot-repair/home/Home/](https://sourceforge.net/p/boot-repair/home/Home/)

---

### Post by highballmint182 on 2018-03-06
Well hello there OldFred, we meet at last. Thank you so much for the promising looking advice. I will keep updated as I move through these steps, hopefully successfully. As I am no spring chicken my self, slow is a great speed to go! I should practice that more often.

---

### Post by highballmint182 on 2018-03-09
Hello there oldfred. Sorry taking so long getting back to ya. tried a couple more os's, debian stuff, think i'm up to 5 or 6 by now, but all fail in spite of my efforts. all freeze at the grub install portion of the os install. locks system solid. the only way out is the ungraceful hard shutdown. I'm going to bed now, but if you have anything else i can try, ill be back at it again asap.. otherwise, I guess i'm stuck with windows10 on this system. thanks for any suggestions you have, oldfred

---

### Post by highballmint182 on 2018-03-09
Well, this is an interesting development. after another reinstall try or  two, I discovered that the EFI partition and the Recovery partitions are  again emptied out, borked as it were, but they were fine till I tried  to dual boot install... that is a little bothersome, back to the drawing  board. I will try returning UEFI bios back to default state to see what happens there.
Nope...running chkdsk next

---

### Post by oldfred on 2018-03-09
did you try the dosfsck with the -a parameter?

Or backup entire partition and create new ESP? The brute force option.

---

### Post by highballmint182 on 2018-03-09
When I did the sudo dosfsck -t -a -w /dev/sdXY, I changed the XY to my location, and it ran fine. it actually removed the dirty bit, didn't take too long, and looked like it would actually work. But it still froze at the same point of the install, installing grub.


When i reloaded windows (the full monty), the EFI and Recovery partitions there were restored, but maybe during the partition shrinkage for installation, it wrecked the EFI (and Recovery) partitions again? Unless I am reading it wrong... When I checked Disk Manager after win reinstall, they were full and formatted for FAT32, now they are 100% empty and not formatted for anything.

So if need to create a new ESP, can i do it without reformatting windows again? How do I do that anyways?

---

### Post by oldfred on 2018-03-09
I have not done it, But some have had to fully backup the ESP and then delete & restore it.
If you copy /EFI folders UEFI may find the file, but usually I believe it normally only finds Windows entries and you have to use efibootmgr to add other systems.
Some may need to you add from UEFI boot menu.

Even if it does not add Windows you can add an entry with efibootmgr.
Entries in UEFI include a GUID which is unique to each partition. There is both a type GUID, so UEFI knows it is the ESP and a unique GUID (somewhat like UUID).
The unique GUID is in the UEFI entry, so if partition recreated, you can delete old UEFI entries and add new ones.

Examples of GUID (PARTUUID) on sda and I have a test install of Fedora that let me install to the ESP on sdb, so showing different GUID.

```
 lsblk -f -o +PARTUUID /dev/sda
NAME   FSTYPE LABEL  UUID                                 MOUNTPOINT PARTUUID
sda                                                                  
&#9500;&#9472;sda1 vfat   ESP    D966-440A                            /boot/efi  [COLOR=#ff0000]c371fe4e-a6db-4c46-b056-a4eea609f81d[/COLOR] 

   fred@Z170N:~$ sudo efibootmgr -v
[sudo] password for fred: 
BootCurrent: 0000
Timeout: 1 seconds
BootOrder: 0000,0001,0002,0006,0003
Boot0000* ubuntu	HD(1,GPT,[COLOR=#ff0000]c371fe4e-a6db-4c46-b056-a4eea609f81d[/COLOR],0x800,0x639c000)/File(\EFI\UBUNTU\SHIMX64.EFI)
Boot0001* Fedora	HD(1,GPT,e58602b1-8fc4-46d1-991f-1d6511d9cdf4,0x800,0x61da000)/File(\EFI\FEDORA\SHIMX64.EFI) 



```

---

### Post by highballmint182 on 2018-03-09
audible gulp :/  so like rEFInd or something I guess

---

### Post by oldfred on 2018-03-09
I have seen where rEFInd does work with those systems with issues.
But if corruption in ESP, then it will not work either.

---

### Post by highballmint182 on 2018-03-09
Well, that's kind of a relief, because I can't find rEFInd. I downloaded it, installed in my Mint, tried to find it, rebooted, still can't find it. hmmmm. anyways just downloaded EaseUS to see if that will rebuild the broken partition. Unlikely, but I have to see what I have to see. Too soon to quit this yet. 
And I have yet to explore the wonders of efibootmanager. never tried that either. I'm hooked

---

### Post by oldfred on 2018-03-09
From Ubuntu live installer booted in UEFI mode, run this just to see if files installed correctly.

 May be best to see details, you can run from your Ubuntu live installer or any working install, use ppa version not older Boot-Repair ISO:
Post the link to the Create BootInfo summary report. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info) and:
[https://sourceforge.net/p/boot-repair/home/Home/](https://sourceforge.net/p/boot-repair/home/Home/)

---

### Post by highballmint182 on 2018-03-09
That's kind of a relief, since I can't find it. Maybe I only thought I downloaded it. whatever. I did find EassOS, and it reveals much more than the Disk Management. turns out that the partitions in question are actually formatted properly, and have data in them. Now I'm confused...

---

### Post by highballmint182 on 2018-03-09
|I just noticed that when USB boot media boots, there are no entries in GRUB for any EFI or UEFI installs. Never have been, but after doing all this research, it seems like there should be EFI or UEFI in front of the selected boot option, whether trial or install is selected. 
I ran Rufus to format boot media to GPT and EUFI, formatted in FAT32, selected my ISO, and went on from there. Something wrong there. Looking into it.

---

### Post by oldfred on 2018-03-09
Full install to internal drive boots from /EFI/ubuntu or the fallback (which is usually a copy of Windows efi file) /EFI/Boot/bootx64.efi.
If external device and UEFI boot, it only boots from /EFI/Boot/bootx64.efi. With Ubuntu installer that is a version of grub/shim with just the parts of grub needed to boot a live installer.
The live installer than also has syslinux as the BIOS boot loader.

 Shows install with screen shots. Both BIOS purple accessibility screen & UEFI black grub menu screen
 [https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

---

### Post by highballmint182 on 2018-03-12
Back again. Sick too much. don't get sick. Anyways, since UEFI has all primary partitions, is it possible to load Windows *after *a Linux install? up till now that was difficult and not advised, but since so many primary partitions are available, load windows last and then add it to GRUB? Just wondering. still  working on trying to get boot-repair to work. no success so far, can't get it to load in a live environment. too many root restrictions etc... onward and upward

---

### Post by oldfred on 2018-03-12
If UEFI only, then can just extract ISO with 7-zip to FAT32 formatted drive with boot flag on FAT32 partition.
Will not boot in BIOS mode
UEFI only USB key, just extract ISO ( 7 zip or similar) to FAT32 formated flash & set boot flag.
[http://askubuntu.com/questions/395879/how-to-create-uefi-only-bootable-usb-live-media](http://askubuntu.com/questions/395879/how-to-create-uefi-only-bootable-usb-live-media)
UEFI only bootable flash drive
[http://ubuntuforums.org/showthread.php?t=2299040](http://ubuntuforums.org/showthread.php?t=2299040)

Or:
       Most find this works:
[https://help.ubuntu.com/community/mkusb](https://help.ubuntu.com/community/mkusb)
[https://wiki.ubuntu.com/Win32DiskImager/iso2usb](https://wiki.ubuntu.com/Win32DiskImager/iso2usb)

You can install Windows after Ubuntu.
But last installed system will set itself as first in UEFI boot order.

All Acer do require you to set "trust" on Ubuntu UEFI boot files. It seems Windows boot files are assumed to have trust?

---

### Post by highballmint182 on 2018-03-12
Well, UUIB is a wash, so is BootRepairDisk. There has to be an installed system for either to work. So, no installation has happened, just getting stuck in the same ol same ol, trying to install GRUB freezing system. never changes.
So, ok, trying to extract ISO with 7-zip to FAT32 formatted drive with boot flag on FAT32 partition. I partitioned USB stick in windows Disk Management, then repartitioned in Rufus i guess. there is a real shortage of partition managers online these days. will let you know how that goes in a few....

---

### Post by highballmint182 on 2018-03-12
On this system, anything that needs a Linux installation to be installed in order to have any input won't work, and since I cannot get any installation to complete, the last try with just dropping a ISO seemed good. of course, it didn't take either, just stopped at the GRUB install portion again. after all these hours, and all this time, I am about ready to throw in the towel. this system has been messed with so much by acer and microsoft, I think they have succeeded in preventing the usage of any Linux/Windows dual boot. If anyone running the same setup as this has had any success setting up a dual boot I will be checking here regularly for a while. Meanwhile, oldfred and all others who have provided so much direction, my sincerest thanks. I will be back....
ps my set is  

 
 
 
 
 
[LIST]
[*] 500 GB HDD on Aspire ES-1533, 	Apollo Lake processor, chipset and south bridge.

[*] Main board =Acer Stego_AP, 	Windows 10 pre-installed and re-installed

[*] UEFI [BIOS] InsydeH20 setup 	utility rev5.0, ver 1.12 [UEFI bios]

[*] GPT, UEFI = enabled, secure boot 	= re-enabled

[*] (U)EFI partiton = gone [in 	Windows 10]

[*] fastboot = disabled  	
[/LIST]

---

### Post by oldfred on 2018-03-12
You have to have an ESP - efi system partition.
That is the FAT32 formatted partition with the boot flag. 
Normally if dual booting both Windows & Ubuntu use the same ESP.

---

