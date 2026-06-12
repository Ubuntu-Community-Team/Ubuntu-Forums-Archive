---
title: "Dell laptop fresh install"
date: 2023-06-03
forum: Installation &amp; Upgrades
---

### Post by acefromspace on 2023-06-03
I got a used Dell laptop (Inspiron 15) Want to do a fresh install of Ubuntu 20.04 Here are the laptop specs:
AMD A6-9200 Radeon R4 5 computercores 2C+3Gx2 Gallium 0.4 AMD Stoney DRM 3.1.0 LLVM 3.8.0 64 bit 192.3 harddrive
Should I expect any issues or do you have any tips that might be helpful?
Laptop has Windows 10 on it but I have no interest in keeping that (or even dual boot)
Also, what about the BIOS? I am used to working with older computers... any advice on BIOS settings?

---

### Post by oldfred on 2023-06-03
What model Dell.
Many need UEFI settings changed. And UEFI install.
How you boot install media UEFI or BIOS is then how it installs.
My new Dell with Intel 11th Gen just worked with 22.04 Kubuntu, I actually forgot the make the changes we have been suggesting for all earlier model Dell system. I did have to turn off Windows fast start up & Windows bit locker as it was Windows 11.

You do need to update UEFI to latest available. Windows may have done that. 
System seems old enough that 20.04 should work, but often better to use newest LTS like 22.04.

Dell typically needs UEFI update, if SSD also SSD firmware update. 
It needs UEFI setting for drives changed to AHCI, not Intel RST nor RAID. But if dual booting with Windows you must first install AHCI drivers into Windows or it will not boot.
Often better to have UEFI Secure boot off. And UEFI fast boot off, as that assumes no system changes & you are changing system.
Newer systems need legacy off to boot in UEFI mode.
And in Windows you need Windows fast start up off as that sets hibernation flag and then Linux NTFS driver cannot see the NTFS partitions. Note that Windows updates may turn fast start up back on.
Older Dell seemed to need legacy on, but still select UEFI to boot (without secure boot). 

If keeping Windows, you have to install the AHCI driver into Windows first or it will not boot. And it may need several reboots to get it working.
Windows AHCI driver install:
[https://discourse.ubuntu.com/t/ubuntu-installation-on-computers-with-intel-r-rst-enabled/15347](https://discourse.ubuntu.com/t/ubuntu-installation-on-computers-with-intel-r-rst-enabled/15347)
Dell - All
[https://www.dell.com/support/article/en-is/sln298524/how-to-use-and-troubleshoot-the-inspiron-17-5759?lang=en&ref=topsolutions#Resetting_System_Setup](https://www.dell.com/support/article/en-is/sln298524/how-to-use-and-troubleshoot-the-inspiron-17-5759?lang=en&ref=topsolutions#Resetting_System_Setup)
How to Install Ubuntu Linux on your Dell PC 
[https://www.dell.com/support/article/us/en/04/sln151664/how-to-install-ubuntu-linux-on-your-dell-pc?lang=en](https://www.dell.com/support/article/us/en/04/sln151664/how-to-install-ubuntu-linux-on-your-dell-pc?lang=en)

My old Haswell based Dell. has these settings.
Under Advanced: USB enable, On board device, AHCI.
Under boot: Secure Boot off, Load legacy, USB boot enabled, Boot mode UEFI.
But then every USB installer has two boot modes UEFI:flash or flash where flash is name or label of flash drive. And one with just name is the BIOS/legacy/CSM boot mode.

---

### Post by ajohnl on 2023-06-04
I've installed very recently on an Inspiron 17, 7000 series. Main confusion initially was dual booting with win8,1. Win had been installed by dell to mbr boot rather than UEFI. Adding Ubuntu caused it to install for an mbr boot. This can also happen when win10 is installed. The bios has a setting to select UEFI booting. I had noticed that with just windows on it own it didn't boot when UEFI was set but didn't think  about it. ;) Then spent time finding it was booting mbr. This machine didn't come with a win dvd. The Dell install is digitally signed. I don't know when Dell started doing this.

Other than that no problem installing a single instance of Ubuntu. One install option is use entire disk. Another is to use a partition on the disk produced by shrinking windows. Best done in windows and probably worth compacting first. Then use windows partitioner to shrink it noting how much it's currently using and leave space for it to use in the future. All wins state how much they need. One problem I had ~3years ago was a partition in the middle of disk storage. Not wise but as there was no obvious way of moving it I simply removed it when I installed Linux, Win was still happy when it booted. However I have recently upgraded it and that now means that win uses several partitions. 3 rather than 2. The update given it's size may well have been several gb. I later received a welcome to windows email, The update was advised not forced. My new machine also has 2 partitions that I think relate to win. The small one is right at the top of the disk space so can simply be left as it is and the main one shrunk.

In UEFI you may have problems booting from USB. In my case rattling the F12 key bought up a selection of boots - picked the longer USB one. There were 2 one just called USB. It shouldn't matter which one is used but note just in case. I found out about use of the F12 key on the web with google mentioning the full model number which is on one of the labels. Dell didn't leave much time for using it hence rattling it as soon as the machine powers up.

I have had problems installing several flavours of Ubuntu on the machine. There are various versions that use different desktops. Ubuntu is refusing to offer a boot selection menu. I can select them by using the F12 key at boot. The machine had a 1tb hard drive in it but once the win8 destroyed it's self via updates I switched to a 500gb ssd, 2.5inch same as the disk. Youtube outlined the dismantling aspects using the model and it's model number in the search. On that I have installed several versions giving each one 50gb. More than enough for linux and apps. This is done using the other install options using either win's efi partition or creating one~500kb and one for the OS which is mounted to /. Some installs may select the win efi partition automatically or the existing one when an ubuntu has been added previously.  This video goes through this approach but I would question some of the sizes used. 
[https://www.youtube.com/watch?v=hrhw8vBTw7g](https://www.youtube.com/watch?v=hrhw8vBTw7g)
That also shows how to create a swap partition. The need depends on how much ram your machine has. I don't know if an auto install on the entire disk creates one automatically. A directed install to a partition on the disk for running multiple versions doesn't. For trying I don't bother with a separate home partition. When I finally pick a version I very probably will.

Making a separate partition for home can make release updates easier. General advice is back up your data but when installing the new version tell it not to format home. You will want to format efi if there is only one OS on the machine. Something I have not done but it should get rid of the old entry in there and create a new one.

You might want to update your bios. I've not tried this. Dells site has a video on updating it. It uses windows. I think there are updates that will run under Linux but when I tried to get one to reinstall win8 it wouldn't download. Might be worth checking for bios updates before removing windows, The video does need to be watched.

---

### Post by acefromspace on 2023-06-04
I got this from my son (very good with computers) He set it up as dual boot Windows and Ubuntu (might be relevant because he had to use F12 to boot linux) I don't care... just want a fresh install He used an older version (ubuntu 14.04) Not sure why but I just want to do a simple install (entire hard drive... or most of it)
Thank you all... I have some reading to do.

---

### Post by ajohnl on 2023-06-05
The main thing to look at is the bios settings. There may be a setting to choose UEFI booting or legacy. It will be in one or the other. That setting influences how the drive needs to  be partitioned. There may also be a secure boot option. On a Dell it looks like best to turn that off.

Oldfred made the point about UEFI updating, That means bios updates. The Dell here is somewhat over 10years old and I haven't updated. I'm running it in UEFI and have had multi boot selection problems but that could be for other reasons. ;) I'll find out shortly..

I tried a directed install yesterday and the installer wouldn't do what I wanted. It was a blank disk so went back to what I did previously.  Used the disk partitioner on the install stick to partition as I wanted then directed the install into that. The installer may say manual or  other etc to do  it this way.. The reason I  probably had problems with the install may have been because it was a blank disk.

Anyway I partitioned like this before installing a different version of Ubuntu and all went ok
50gb larger than it need be if home is mounted in it's own partition - as you can see from how much is used. This flavour of Ubuntu comes with lots of software and have installed more myself.

Swap partition - depends how much memory you have. You can create as many partitions as  needed and the install offers a selection of things that it can be mounted to. The photo is of a UEFI install which must have the efi partition.

---

### Post by oldfred on 2023-06-05
@ajohnl
Please do not post in line, just post an attachment. Not everyone has high speed Internet. Use paperclip icon in Advanced editor.
Also for partitioning, just better to post terminal output in code tags.
Easy to add code tags with Forum's advanced editor and # icon.

```
[FONT=monospace][COLOR=#000000]Model: Samsung SSD 970 EVO Plus 500GB (nvme) [/COLOR]
Disk /dev/nvme0n1: 500GB 
Sector size (logical/physical): 512B/512B 
Partition Table: gpt 
Disk Flags:  

Number  Start   End     Size    File system  Name       Flags 
 1      1049kB  538MB   537MB   fat32        esp_nvme   boot, esp 
 2      538MB   32.0GB  31.5GB  ext4         focal_0 
 3      32.0GB  63.5GB  31.5GB  ext4         focal_k 
 5      63.5GB  273GB   210GB   ext4         nvme_data 
 4      469GB   500GB   31.5GB  ext4         jammy 
[/FONT]
```

I highly recommend gpt partitioning whether UEFI or BIOS install. Microsoft has required gpt partitioning for UEFI installs of Windows since 2012.
I started using gpt with old BIOS only system but then had to have a 1MB bios_grub partition. For a few years when first converting to UEFI, I added both the bios_grub & ESP - efi system partition so I could easily convert boot mode. But both bios_grub & ESP  are not required, just the one to match boot mode.

---

### Post by donald187 on 2023-06-05
There's also this.

[https://www.dell.com/support/kbdoc/en-us/000131655/how-to-install-ubuntu-linux-on-your-dell-pc](https://www.dell.com/support/kbdoc/en-us/000131655/how-to-install-ubuntu-linux-on-your-dell-pc)

---

### Post by ajohnl on 2023-06-05
Sorry about that @oldfred. I had no need to post the shot inline but thought a photo was more appropriate for the OP as not sure about what he has done before. All partitioners are pretty similar.

I can add that creating the partitions using the install sticks partitioner 1st works fine. A first install for me without that didn't. The install iwill probably expect the user to mount the efi partition to boot/efi and set the boot flag. The other partition can then be mounted to / then if needed another partitions can be added and mounted to home. The photo also shows usage. / has all sorts in it. video editor, photo apps, sound related stuff and all of the usual. With a separate home it doesn't need to be as big as I have made it,

---

### Post by acefromspace on 2023-06-05
Thank you all for the info... this a bit over head (I was very good at this years ago but I've been out of the loop for a long time) I'm going to have my son read all this (he will be very interested)
Would it be easier if I just leave windows on there (he made a "shared" partition for data and also a partition for Ubuntu)
BTW, I've used 32 bit in the past (that's the Ubuntu 20.04 I have on a USB flash drive) I will consider just getting Ubuntu 22.04 (I always use LTS versions) and using the 64 bit version.
I am very busy but not in a hurry. I'm 62 years old and having memory issues (I'm low on RAM... bad joke LOL) So... don't need windows but if that makes this easier, I am fine with that.
I also don't mind if I have to do F12 every time to boot the linux.

---

### Post by oldfred on 2023-06-05
Dell was one of the first to offer UEFI updates via Linux with fwupdate.
UEFI/BIOS updates brand model list  for Dell with (uefi >= 0.6.2 & dell >= 0.7.3) 
[https://fwupd.org/lvfs/devicelist](https://fwupd.org/lvfs/devicelist)

If older than that, better to keep Windows. Leave 30% free in the Windows main partition, or it gets very slow.
Make sure fast start up is off. It sets hibernation flag and that prevents the Linux NTFS driver from mounting read/write.

Use Windows tools to shrink largest NTFS partition and reboot, so it can run chkdsk which it needs after any resize.

---

### Post by ajohnl on 2023-06-06
My first multiboot on my dell laptop was fine and just worked alongside windows. The reason seems to be that win had been installed mbr so ubuntu did too. I'd assume this would be the same for several different OS's. I did this because i have a new machine with win11 on and wanted some reassurance that ubuntu installs work, Pointless really as the win11 will be installed uefi. Win destroyed itself via updates so not on the machine now.

There are several flavours of Ubuntu around so installed several uefi style to enable me to pick one. No boot menu, The machine just ran though to the last one installed. So installed an OS that I know produces a menu. Fedora stable, Opensuse. If I used the F12 key and selected it I got the menu, Even with it set for boot priority the machine just ran through to the last ubuntu installed, That turned out to be due to a bios uefi boot disk being active. Set it to inactive and opensuse booted as it should and I could select it or the ubuntu I wanted to run.

Then in case the bios boot was messing up unbuntu installs I went through the whole thing again. The ubuntu installs just run through to the last installed. Oddly this time if I use the F12 key I see one entry - Ubuntu and if I select that I do get a menu.

Ok so if I installed OpenSuse I could get a menu. Hang on though if I installed another version would I have the same  problem? I suspect so. I might then find that I could get a menu if I installed an Ubuntu, Reason in both cases a different name in efi storage and a rat arsed mess called grub that can't sort itself out when there are multiple copies of it's own distro around, The annoying thing is that win can if there are multiple versions of that installed,

LOL That's my theory anyway but oldfred has suggested some grub scripting changes that may fix it,

An eg. I just ran grub-update in the last ubuntu installed. The one a normal boot falls through to. It tells me that it has found the other ubuntu and created a menu entry for it, Rather strange as it's grub.cfg already had an entry for it, A normal boot still  runs through to it. Use F12, Might expect 2 entries for the same other version but no there is just one.

---

### Post by oldfred on 2023-06-06
How you boot install media, UEFI or BIOS is then how it installs & repairs.
With new systems you want to always boot in UEFI mode and use gpt partitioning.
But have to use boot mode that Windows is in, if dual booting with Windows. 
Microsoft has required vendors to install in UEFI mode since 2012. Users have option, but should not use BIOS on newer systems.

All official flavors of Ubuntu and many unofficial versions that use "ubuntu" as boot entry will always only have one UEFI boot entry. Or maybe two, one shim & one grub. Then in the ESP - efi system partition is a 3 line grub configfile entry to the default (usually last) install. And then grub will only offer to boot other installs in same boot mode. But now they want to turn off os-prober or just run it once for security reasons as it opens and scans every partition for operating systems.

---

### Post by ajohnl on 2023-06-07
Security questioning can crop up due to some one asking if some feature  is secure, It can be a hard question to answer so just kill it. I had an  instance if this years ago when using a NAS for extended storage. I  chose to use a net protocol built into the kernel that was intended for  use with diskless pc's. Light and efficient with the usual access  controls.A  feature was knocked out so no longer any use to me.  Complained. Rather than simply killing it they commented out some of the  source code and added instructions to re enable it. They could equally  have left the decision to some one - who
[SIZE=5]ROOT
[SIZE=2]a person Ubuntu doesn't have.Is that secure - no. LOL Is UEFI secure?  Sounds like it isn't and there can be multiple efi partitions on a disk and on other disks. What gathers the info - the kernel. Scan disks? I doubt it more likely scan partitions looking for a marker. What privileges are needed to use it - root's. it's pretty clever in the eif partition area. When efibootmgr is used to create a new entry it's capable of filling in certain areas of the entry by itself. For instance no partition number is needed unless there is more than one efi partition. Same probably applies to disks if only one is fitted. It generates the uuid's anyway. More than usual on the mgr here
[https://discussion.fedoraproject.org/t/efibootmgr-nvme-how-to-create-entry-with-custom-label/75566](https://discussion.fedoraproject.org/t/efibootmgr-nvme-how-to-create-entry-with-custom-label/75566)

LOL I find it interesting as the distro's need us not just sys admin people to develop and test code. A sys admin wont have much of a problem removing what they see as undesirable and will have root privileges, I've been wondering what has happened since some one spotted an obscure security hole in X. Desktop software has always been frowned on in respect to making system level changes yet a lot of users want it. KDE's latest answer is allow a user to look at all but need root privileges to write back changes. It used to be run the file browser Dolphin as root. There could be means to control this using stuff that is already there but for a sudo user the new approach is ideal.
[/SIZE][/SIZE]

---

### Post by ajohnl on 2023-06-07
I should add that SU stands for Super User but people started calling them root. ;) It can mean switch user when some one is in a root account, In my case it used to be the user that invoked SU privileges. Of late I have so specifically name the user I want to switch too. I've sometimes wondered what would happen if it wasn't me,

---

