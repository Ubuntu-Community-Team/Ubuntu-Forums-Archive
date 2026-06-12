---
title: "grub fails to boot Ubuntu 12.04-2 (64 bit)after install"
date: 2013-02-20
forum: Installation &amp; Upgrades
---

### Post by Jay_E on 2013-02-20
Greetings.

I  installed Ubuntu 12.04-2 from a DVD
(ubuntu-12.04.2-desktop-amd64.iso)

The DVD booted OK.

After the install - where it said it was finished and it was time to boot from the Hard Drive, grub failed.

It said something like (I didn't write it down at the time.):
Grub Rescue > Ubuntu 12.04-2 fail boot 

I started to reading the posts and suspected an UEFI problem.
For general background, I read:
[http://www.zdnet.com/ubuntu-linux-adopts-new-uefi-boot-problem-approach-7000004648/](http://www.zdnet.com/ubuntu-linux-adopts-new-uefi-boot-problem-approach-7000004648/)

and
[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

Anyway.  I'm stumped.

This is a new system. It never had any windows on it.
I am trying to get an Radeon HD 7750 to work and have installed both
Debian 6.06    and   ubuntu-12.10-desktop-amd64.iso
Both of these booted OK. I had wiped all partitions out and started over each time.

Then I tried Ubuntu 12.04-2 in a dual boot with the Debian -
by taking the install option to install Ubuntu side-by-side with Debian.
That did not work. I *really* wish I had written the exact error message.
It was along the lines that grub could not find the partition.

So I wiped all partitions and started over with the Ubuntu 12.04-2 install.
This time I used the easy install method so I could go eat dinner without answering a lot of install questions.
This is where I get the Grub Fail message.
the Ubuntu 12.04-2 did not have a Rescue option in the menu,
just ( paraphrase)
   - try it
   - install it
   - memory test

I tried the "Try it" option to see if I could fix it.
No Go. That version of GParted said it needed 'gpart'.
I couldn't get gpart.

After reading more posts, I tried to boot with BIOS set with full UEFI enabled.

Got a new error message this time:
The current BIOS setting do  [sic]  not fully support the boot device.
Click OK to enter the BIOS setup.
Go to Advanced > Boot > CSM Parameters and adjust the CSM
(Compatibility Support Module) settings to enable the boot device.

OK. did this.
Changed Launch CSM
From: Enabled
To: Disabled

The Bios screen had these explanations:
[Enabled] : For better compatibility, enable the CSM to fully support the 
non-UEFI driver add-on devices or the Windows UEFI mode.

[Disabled] : Disable the CSM to fully support the Windows Security Update and Security Boot.

OK. I'm confused. But no matter. Try something and see if it works....
Saved the settings and tried to boot the HD.

[Insert drum roll here.]

A new error!

A different BIOS display..
Here is the info written from the screen...   :-)
American Megatrends
AMIBIOS (C) 2012 American Megatrends, Inc.
ASUS Sabretooth 990FX R2.0.ACPI BIOS Revision 0906
CPU AMD FX(tm) -8150 Eight-core processor    .....
....
The VGA card is not supported by the UEFI driver.
CSM (...) settings have been changed for better compatibility

Just great.   :-(

Then the option to procede, or go back and change the settings.
I tried to procede.

That went to the 1st message about adjusting the CSM to enable the boot device.

OK.  I'm writing this down so I won't have to go back; do it over to answer a question later - of what I did try.

OK.
Rest CSM back to auto.
[This BIOS is labelled ASUS UEFI mBIOS Utility - EZ Mode (or Advanced mode)
Launch CSM: Enabled
               {Then 4 more settings show up.}
I set these to:
Boot Device Control              :  UEFI and Legacy OpRom
Boot from Network devices   :  Legacy OpRom first
Boot from Storage Devices   :  Both, UEFI first
Boot from PVIe/PCI Expansion Devices : UEFI driver first

save and reboot.
{insert a drum roll while I go get a beer.] :popcorn:

A different error message.

Grub loading
Welcome to GRUB!
error:  invalid arch independent ELF magic.
Entering rescue mode...
grub rescue>

Beer in hand I went googling for grub rescue commands.
Ah-hah. Another post said:
"Sometimes, when you change the partition layout of your HD, the number  of the partition which contains GRUB2 changes. Let's assume we installed  GRUB2 from (hd0,7) or /dev/sda7, which is a logical partition inside an  extended partition. Then we deleted /dev/sda5 and /dev/sda6, our  /dev/sda7 became /dev/sda5. Now when the "MBR part" is looking for the  rest of the program, it can't find it in (hd0,7) since such partition  doesn't exist anymore. In this case, instead of showing the usual GRUB2  menu, you are being dropped to some sort of command line which is called  GRUB rescue."

YES - So isn't Ubuntu supposed to RE install the MBR  and Grub when it runs?
Is this the problem??

Here is the posting:
[https://bbs.archlinux.org/viewtopic.php?id=85603](https://bbs.archlinux.org/viewtopic.php?id=85603)

Still. This isn't the message that I started off with - so I will try another UEFI setting.:roll:
Boot Device Control              :  UEFI and Legacy OpRom
Boot from Network devices   :  Legacy OpRom first
Boot from Storage Devices   :  Ignore
Boot from PVIe/PCI Expansion Devices : Legacy OpRom driver first


and another link about the commands..
**(hd0) (hd0,1) (hd1) (hd1,1)** This list is showing that there are two physical hard drives (hd0 and  hd1) and each hard drive has a single partition on it (hd0,1 and  hd1,1). Where legacy Grub counted partitions from #0, Grub2 counts  partitions from #1. Another important thing to note is that the order in  which Grub2 names the drives does not necessarily correspond with the  drive device assignments in Linux. So the first linux drive /dev/sda is  not necessarily (hd0). You can figure out which drive is which though,  by ‘mounting’ them and checking. The Grub2 root command ‘mounts’ the  volume. Note that you want to mount the partition, not the drive.  So if  I issue the command *root (hd0,1)* to mount the partition on the first drive, Grub2 responds with:


......
above from:
[http://planetstephanie.net/2009/05/27/grub2-rescue-mode/](http://planetstephanie.net/2009/05/27/grub2-rescue-mode/)



Yikes!

also the 'help' and the 'root' commands did not work.  ](*,)


Maybe that is the problem.
But first, try a reboot with the altered settings:
  Get the ELF magic again.

Go back to factory settings...


and I saw a comment in the above post:
 						You can avoid all of these problems if you have free space at  the start of your disk, or create a bios_grub partition of > 31kb.
[URL="http://grub.enbug.org/BIOS_Boot_Partition"]http://grub.enbug.org/BIOS_Boot_Partition[COLOR=Black] 
[/COLOR][/URL]
 					
  [sic  - a bad link]


Maybe that is the problem.
But first, try a reboot with the altered settings:
  Get the ELF magic again.

Go back to factory settings...

I will load up a system rescue disk, run GPARTED add the blank spaces on the front of the disks and reload.

Will end this post and give results tomorrow/later today.

In the meantime, anybody have a suggestion?
(Or want to go out for a beer?)

Jay

---

### Post by Jay_E on 2013-02-20
Hey there.

I am having a similar problem.
[http://ubuntuforums.org/showthread.php?t=2118052&highlight=uefi](http://ubuntuforums.org/showthread.php?t=2118052&highlight=uefi)

I just couldn't get Ubuntu to boot.
I reset my bios and still no luck.

As a test I tried to install Debian 6.06.
IT WORKED - BOOTED JUST FINE.

I'm a masochist.
went back and retried Ubuntu 12.04-2 and 12-10
No go for either.

Went back to Debian.
Boots just fine.

Hmmm.

Wanted to share...

Jay

---

### Post by Jay_E on 2013-02-20
An update.
I retried with an extra space before the first partition.
12-04-2 and 12-10 still won't boot

went back to debian 6.0.6
IT WORKED.

So. With a good MBR and GRUB. I went back to try 12.04-2 and 12.10
BOTH FAIL.
BIOS is set for auto - UEFI or legacy

Went back and installed Debian 6.06.

IT WORKED.


Has anyone with a uefi-capable bios got a successful install of 12.04-2   ???
  (OldFred,  have you installed 12-04-2 with a uefi bios?)
  ( Might want to do a disk clone first...)


Thanks, 
Jay

PPS
 the only other thing I can think of  - is that this is a grub2 problem..
will look for grub2 problem reports.

---

### Post by Jay_E on 2013-02-20
I'm looking for a solution too.
Will keep you posted.
Jay

---

### Post by oldfred on 2013-02-20
After all that I need a beer. :)

Not I do not even have UEFI. But I was originally going to install this new UEFI thing with my build back in 2006. I only found server motherboards over $2K and I was looking for more like $100-$200 price.

Then last summer I was going to build a new system so I started following all the issues so  would know what to do. I do already have gpt partitioning on several drives.

You have two boot modes UEFI and legacy/BIOS/CSM or whatever your system calls compatiblity with the old BIOS mode.
UEFI only boots from gpt partitioned drive.
Windows only boots from gpt drives with UEFI.
Ubuntu boots from either gpt or MBR(msdos) drives with BIOS mode.

Do you want UEFI or BIOS? Do you want MBR or gpt partitioning? 
Are you installing Windows on this system? Always better on separate drive.

So how is drive partitioned and what mode are you booting installer  DVD/Flash with. How you boot installer from UEFI/BIOS menu is how it  installs.

Everyone knows BIOS, not many know UEFI, but it is the new thing and will be the future. With my new SSD, I created an efi partition for future boot, which has to be near start of drive (recommended first, but Windows wants it repair partition first), then a bios_grub 1MB unformatted partition for my current BIOS boot with gpt partitioning.

If you want UEFI:
       You will need to use the 64 bit version of 12.10 and from the UEFI menu boot the flash drive in UEFI mode. That way it will install in UEFI mode.
Systems need quick boot or fast boot turned off in UEFI settings. Vital for some systems. Best to backup efi partition and Windows partition first.
Use Windows Disk Tools to shrink Windows main partition, but not to create any new partitions, if installing on same drive.
[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)
[https://wiki.archlinux.org/index.php/UEFI](https://wiki.archlinux.org/index.php/UEFI)
As of 12.04.2, it is possible to install on UEFI systems with Secure Boot enabled (using signed versions of Shim, GRUB, and the Linux kernel). This is only currently set up for Ubuntu (desktop, alternate, and server) and Edubuntu images due to pressures of time; we expect to enable it across the entire Ubuntu family for 12.04.3.  Details:
[https://wiki.ubuntu.com/PrecisePangolin/ReleaseNotes/UbuntuDesktop](https://wiki.ubuntu.com/PrecisePangolin/ReleaseNotes/UbuntuDesktop)


May be best to see exactly where you are at?
       
 Post the link to the BootInfo report that this creates. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)
Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration and diagnose advanced problems.
Install in Ubuntu liveCD or USB or Full RepairCD with Boot-Repair (for newer computers) 
[http://sourceforge.net/p/boot-repair/home/Home/](http://sourceforge.net/p/boot-repair/home/Home/)
[https://help.ubuntu.com/community/UbuntuSecureRemix](https://help.ubuntu.com/community/UbuntuSecureRemix)

---

### Post by mörgæs on 2013-02-20
> **Jay_E said:**
> 
I am having a similar problem.


No, you have an unrelated problem, as yours is about UEFI. 

Posts merged.

---

### Post by Jay_E on 2013-03-04
MBR, GPT and grub..
(( Lions, Tigers and Bears, Oh my! ))


[http://en.wikipedia.org/wiki/GUID_Partition_Table](http://en.wikipedia.org/wiki/GUID_Partition_Table)   -- talks about the GUID PArtition Table,

[http://www.wensley.org.uk/gpt](http://www.wensley.org.uk/gpt)              ---says
Normally, Grub does not understand GPT partition tables and needs to be tricked into starting
from one. You need to create a very small partition at the start of your disk to hold the grub stage2,
(or stage1.5 if you would like to start stage2 from /boot)

Wow
Nothing is simple.
The   [http://www.wensley.org.uk/gpt](http://www.wensley.org.uk/gpt)  post goes on and says to use gparted to make a minimal partition, another partition for /boot
and goes on from there.

I'll try that.
If that fails, Ill get the boot-info stuff.

*****Many****   thanks to the people that updated the Ubuntu community    Boot-info   and   Boot-Repair  websites..

Jay

---

### Post by Jay_E on 2013-03-04
> **mörgæs said:**
> No, you have an unrelated problem, as yours is about UEFI. 

Posts merged.

Hey there.
Yes, it has taken me a week to get bck.
I have been otherwise occupied.

To answer your questions
   I tried the Ubuntu 12.04-2  and Ubuntu 12-10
There is no other OS to share the disk. it is a new system.
To avoid problems of leftovers, I used gparted to re-format the disk esch time.

The install goes OK.
When I try to boot from the HD the first time, I get:
grub-rescue > error: file '/boot/grub/i386-pc/linux.mod  not found

I have re-downloaded and burned several CDs and DVDs.

I can install Debian OK

_[[COLOR=#000000]Mörgæs[/COLOR]]("http://ubuntuforums.org/member.php?u=939075")_,  Thank you for your response.

Jay

---

### Post by oldfred on 2013-03-04
First are you trying to install in UEFI mode or BIOS/legacy/CSM mode.

Do you want to also install Windows?

Windows will only install to gpt partitioned drives with UEFI.
From UEFI, Windows will only boot if drive is gpt.
Ubuntu does not care if drive is MBR(msdos) or gpt if booting in BIOS mode (but you do need the 1MB unformatted bios_grub partition). The Ubuntu installer will auto create either a bios_grub or efi partition during install.
But all systems with UEFI need an efi partition which you can only create in gpt partitioned drives.

How you boot the installer for both Windows and Ubuntu is how it installs. Or from UEFI menu boot in UEFI mode & it installs in UEFI mode.

And a lot of settings in UEFI/BIOS seem to control how you boot also.
New systems need secure boot off, UEFI on, CSM or BIOS off or what ever combination of settings do that as it seems to vary a lot by UEFI system. And some seem to be backwards, like UEFI on means secure boot off. But secure boot is also UEFI boot?

And you have to turn fast boot off in UEFI.

---

### Post by Jay_E on 2013-03-04
OldFred,
WOW you are fast!

Thank you for the clarifications.
-----to answer your question..
Nope, no windows.
But, I would like to try a dual boot of both Debian and Ubuntu.
   (I'm trying out new ATI and OpenCL drivers - and Ubuntu (or Mandrake) may have an easy path to climb.)
-----
I have  yet another question.
you said  [COLOR=#006400](but you do need the 1MB unformatted bios_grub partition)[/COLOR]
Er, in Gparted terms, does that mean I leave 5 or so MB blank at the beginning of the first partition?
Or actually make a (primary?) partition and mark the type of file system as unformatted?
I assume that this has nothing to do with the  /boot   partition.
( I have been wrong before. Repeatedly. )

At the moment, I have /dev/sda and /dev/sdb
/dev/sda has
[LIST=1]
[*]a gB of dead space 
[*]an ext2 of /boot 
[*]more space 
[*] an ext2 of /root 
[*]lots more space 
[/LIST]

/dev/sdb has
[LIST=1]
[*]a gb of space 
[*]yet another ext2  /boot (The reason for this escapes me at the moment.) 
[*]space 
[*]swap 
[*]space 
[*]/home 
[*]300GB of even more space 
[/LIST]


Suggestions???  Tomatoes to throw?
I have held back on putting stuff on this machine and getting cozy - so I can wipe them all and start over.
But that may require at least one more beer.

Thank you for your patience!
Jay

Soon to be [RESOLVED]

---

### Post by oldfred on 2013-03-05
I suggest both efi and bios_grub partitions as adding an efi partition to beginning of drive later can be difficult. But efi partition will only be used by UEFI install or bios_grub by BIOS/Legacy install. If gpt partitioned then you can convert from BIOS boot to UEFI. But if MBR you cannot convert and do not need those partitions. 

I do not suggest a separate /boot, but do keep / (root) smaller. If dual booting with other Debian based I would just leave /home inside / and use data partitions for all data. Then you can easily mount the same data partition in all installs. I have many Ubuntu installs and do exactly that.

       For the Total space you want for Ubuntu:
Ubuntu's standard install is just / (root) & swap, but it is better to add another partition for /home if allocating over 30GB.:
Only if gpt -  all partitions in gpt are primary:
gpt: 250 MB efi FAT32 (for UEFI boot or future use for UEFI, you only can have one, so if already existing do not attempt another)
gpt: 1 MB bios_grub no format (for BIOS boot not required for UEFI)
gpt or MBR(msdos)
Ubuntu partitions - smaller root only where hard drive space is limited.
If total space less than about 30GB just use / not separate /home or standard install.
1. 10-25 GB Mountpoint / primary or logical beginning ext4(or ext3)
2. all but 2 GB Mountpoint /home logical beginning ext4(or ext3)
3. 2 GB Mountpoint swap logical

   Depending on how much memory you have you may not absolutely need swap but having some is still recommended. I do not hibernate (boots fast enough for me) but if hibernating then you need swap equal to RAM in GiB not GB. And if dual booting with windows a shared NTFS partition is also recommended. But you usually cannot create that as part of the install, just leave some space. Or partition in advance (recommended).
One advantage of partitioning in advance is that the installer will use the swap space to speed up the install. Thanks Herman for the tip.

Instead of /home create as many 25GB future root partitions as you want. I created two 100GB data partitions on my new 650GB drive 3 years ago and left the rest unallocated. I then installed Ubuntu, and the then beta. But I left those partitions and with every version I added another 25GB / partition. And If I wanted to test another 25GB. I now have so many I cannot keep track, have to turn off os-prober as it finds too many, It is time to houseclean as some of the old installs are now obsolete.

      
 Splitting home directory discussion and details:
[http://ubuntuforums.org/showthread.php?t=1811198](http://ubuntuforums.org/showthread.php?t=1811198)
[http://ubuntuforums.org/showthread.php?t=1901437](http://ubuntuforums.org/showthread.php?t=1901437)
[http://ubuntuforums.org/showthread.php?t=1734233&highlight=%2Fdata]("http://ubuntuforums.org/showthread.php?t=1734233&highlight=%2Fdata")
Link is on move home but see post by bodhi.zazen on data partition #6
[http://ubuntuforums.org/showthread.php?t=325048](http://ubuntuforums.org/showthread.php?t=325048)

---

### Post by oldfred on 2013-03-05
I suggest both efi and bios_grub partitions as adding an efi partition to beginning of drive later can be difficult. But efi partition will only be used by UEFI install or bios_grub by BIOS/Legacy install. If gpt partitioned then you can convert from BIOS boot to UEFI. But if MBR you cannot convert and do not need those partitions. 

I do not suggest a separate /boot, but do keep / (root) smaller. If dual booting with other Debian based I would just leave /home inside / and use data partitions for all data. Then you can easily mount the same data partition in all installs. I have many Ubuntu installs and do exactly that.

       For the Total space you want for Ubuntu:
Ubuntu's standard install is just / (root) & swap, but it is better to add another partition for /home if allocating over 30GB.:
Only if gpt -  all partitions in gpt are primary:
gpt: 250 MB efi FAT32 (for UEFI boot or future use for UEFI, you only can have one, so if already existing do not attempt another)
gpt: 1 MB bios_grub no format (for BIOS boot not required for UEFI)
gpt or MBR(msdos)
Ubuntu partitions - smaller root only where hard drive space is limited.
If total space less than about 30GB just use / not separate /home or standard install.
1. 10-25 GB Mountpoint / primary or logical beginning ext4(or ext3)
2. all but 2 GB Mountpoint /home logical beginning ext4(or ext3)
3. 2 GB Mountpoint swap logical

   Depending on how much memory you have you may not absolutely need swap but having some is still recommended. I do not hibernate (boots fast enough for me) but if hibernating then you need swap equal to RAM in GiB not GB. And if dual booting with windows a shared NTFS partition is also recommended. But you usually cannot create that as part of the install, just leave some space. Or partition in advance (recommended).
One advantage of partitioning in advance is that the installer will use the swap space to speed up the install. Thanks Herman for the tip.

Instead of /home create as many 25GB future root partitions as you want. I created two 100GB data partitions on my new 650GB drive 3 years ago and left the rest unallocated. I then installed Ubuntu, and the then beta. But I left those partitions and with every version I added another 25GB / partition. And If I wanted to test another 25GB. I now have so many I cannot keep track, have to turn off os-prober as it finds too many, It is time to houseclean as some of the old installs are now obsolete.

      
 Splitting home directory discussion and details:
[http://ubuntuforums.org/showthread.php?t=1811198](http://ubuntuforums.org/showthread.php?t=1811198)
[http://ubuntuforums.org/showthread.php?t=1901437](http://ubuntuforums.org/showthread.php?t=1901437)
[http://ubuntuforums.org/showthread.php?t=1734233&highlight=%2Fdata](http://ubuntuforums.org/showthread.php?t=1734233&highlight=%2Fdata)
Link is on move home but see post by bodhi.zazen on data partition #6
[http://ubuntuforums.org/showthread.php?t=325048](http://ubuntuforums.org/showthread.php?t=325048)

---

### Post by Jay_E on 2013-03-05
February 5, 2013
Hello OldFred, and others.

Well.
I wiped out both disk; burned an AMD 64 Lubuntu 12.10 cd and installed it.

As part of the install I added another partition for UEFI boot, with space before that for the GUID Partition table.

As much as I would like to say "RESOLVED", Nope.

As I said, the disk booted and installed OK.
EXCEPT.
When I tried to start from the HD (It's time to boot your new system.) I get this grub display:

GRUB Loading.
Welcome to GRUB!

error: no such device: cba609c8-fca7-4a66-8ed6-31b9da5a929a.
grub rescue>

-------
a google of the error message sends me to:
[http://askubuntu.com/questions/143667/boot-error-no-such-device-grub-rescue](http://askubuntu.com/questions/143667/boot-error-no-such-device-grub-rescue)

it says to run grub boot repair.
OK, I'll do that, but I think that the install that I just did should not have left the HD in an error state.

Will keep this short and post again with results of endeavors. :)
Jay

---

### Post by Jay_E on 2013-03-05
Quite Late on February 5, 2013

While I was waiting for the boot-repair and the linux-secure to download,
I read a posting where a user changed is disks and had the same boot problem.

Uh-Oh.

I deleted all partitions on Both disks - created all-encompassing partitions and did a format.
Went back and deleted the new partitions. (did these just to wipe the disks.)

Yikes!

The manage flags for the two disks were different!

/dev/sda  is a solid state drive 0 80GB.  Previously, I had set this up as root and boots.
/dev/sdb is a hard disk drive 800 GB - I had set this up as swap and home.

Sooooooo.
I switched.
set up /dev/sda  as swap and /home  and /var  ( for boinc task checkpointing).


It Booted.
no grub errors.

Why would this be?
Is there some restriction of SDD vs HDD ??

Almost resolved.

Jay

---

### Post by Jay_E on 2013-03-06
February 6, 2013

While I was waiting for the boot-repair and the linux-secure to download,
I read a posting where a user changed is disks and had the same boot problem.

Uh-Oh.

I deleted all partitions on Both disks - created all-encompassing partitions and did a format.
Went back and deleted the new partitions. (did these just to wipe the disks.)

Yikes!

The manage flags for the two disks were different!

/dev/sda is a solid state drive 0 80GB. Previously, I had set this up as root and boots.
/dev/sdb is a hard disk drive 800 GB - I had set this up as swap and home.

Sooooooo.
I switched.
set up /dev/sda as swap and /home and /var ( for boinc task checkpointing).

Reinstalled from scratch. (add this line in edit.)
It Booted.
no grub errors.

Why would this be?
Is there some restriction of SDD vs HDD ??

Almost resolved.

Jay 

[LIST]
[*]                           :popcorn: 
[/LIST]
 
PS
 I think this is the second time I tried to post this.
I could not find it this morning so I reposted.
I sincerely apologize if it shows up again somewhere else.
Jay

---

### Post by oldfred on 2013-03-06
Should be no difference between SSD & hard drive. But SSDs work better with some BIOS and Linux entries.

Is one drive MBR and the other gpt?

       Do SSD need customization?
[http://ubuntuforums.org/showthread.php?t=1981478](http://ubuntuforums.org/showthread.php?t=1981478)
Arch suggests gpt for SSD. Only if installing Windows on older system may you want MBR as Windows only boots from gpt with UEFI. 
[https://wiki.archlinux.org/index.php/Solid_State_Drives](https://wiki.archlinux.org/index.php/Solid_State_Drives)
[http://ubuntuforums.org/showthread.php?t=2003022](http://ubuntuforums.org/showthread.php?t=2003022)
[https://sites.google.com/site/easylinuxtipsproject/ssd](https://sites.google.com/site/easylinuxtipsproject/ssd)

post this:
sudo parted -l

---

