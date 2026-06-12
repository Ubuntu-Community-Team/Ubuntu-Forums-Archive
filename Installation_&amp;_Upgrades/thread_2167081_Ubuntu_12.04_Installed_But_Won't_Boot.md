---
title: "Ubuntu 12.04 Installed But Won't Boot"
date: 2013-08-12
forum: Installation &amp; Upgrades
---

### Post by pvollma on 2013-08-12
My motherboard quit, so I got a new Lenovo tower and installed my 500GB HDD from my dead system into it as sdb, with the pre-installed Windows 8 on sda. I booted from a 12.04 LTS DVD, deleted all the Windows partitions, and created three new partitions on sda for /, /home and swap. I then installed 12.04 on sda, first with the boot record (from the installation dialog) on sda, then tried again selecting sda1. Both times, the system will not boot from sda, but boots fine from sdb (so at least I didn't lose anything!). I can also mount sda while booted in 10.04 on sdb, and see the expected file layout on / and /home.The message I get when I boot from sda is:

First:

no upper memory
Aborted. Press any key to exit.

After pressing a key:

Error 1962: no operating system found. Press
any key to repeat boot sequence.

Am I picking the wrong destination for the boot record? Is something else wrong? Any help greatly appreciated, as I would like to move to 12.04 LTS.

---

### Post by oldfred on 2013-08-12
If system was Windows 8, it was UEFI with gpt partitioning. But old drive was/is MBR(msdos). UEFI has a CSM or compatibility mode to work with old BIOS.

Best to see exactly where you are:
       Post the link to the BootInfo report that this creates. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)
Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration and diagnose advanced problems.
LighterWeight (Lubuntu based) Boot-RepairCD
[http://sourceforge.net/projects/boot-repair-cd/files/](http://sourceforge.net/projects/boot-repair-cd/files/)
Full Ubuntu 13.04 liveDVD or USB Install with Boot-Repair included (for newer computers) 
[https://help.ubuntu.com/community/LinuxSecureRemix](https://help.ubuntu.com/community/LinuxSecureRemix)

---

### Post by melchor2 on 2013-08-12
You should try this Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)

---

### Post by pvollma on 2013-08-12
Ran boot-repair, link is:

[http://paste.ubuntu.com/5978182/](http://paste.ubuntu.com/5978182/)

Thanks!

---

### Post by grahammechanical on 2013-08-12
From the boot repair printout I see this at the bottom of the printout

> GPT detected. Please create a BIOS-Boot partition (>1MB, unformatted filesystem, bios_grub flag). This can be performed via tools such as Gparted. Then try again.


Others, more experienced than me, may give better advice but I think with GPT we need that greater than 1MB partition at the front of the disk with it set with the bios_grub flag. Perhaps you could create that partition and then re-install using the Something Else option.

Regards.

---

### Post by pvollma on 2013-08-12
I booted from the live DVD, deleted the Ubuntu 12.04 partitions and recreated them, with a 1 GB biosgrub partition on the front of sda (sda1). I continued with the installation, directing the boot loader to sda1. Same problem and error messages.

New info file at:  [http://paste.ubuntu.com/5978777/](http://paste.ubuntu.com/5978777/)

---

### Post by oldfred on 2013-08-12
It looks like you installed grub to sda1, but you need it in sda not sda1.

It has become somewhat confusing. You never install grub to a partition, but if you have UEFI you have to install grub to the efi partition.
So with BIOS boot you need to install grub to MBR, and with UEFI boot you install to efi partition.

With gpt partitioning you have to have a bios_grub partition for core.img and grub to then install correctly. With MBR partitioning core.img is hidden in the sectors after the MBR but before first partition. 

Boot-Repair should re-install grub to sda correctly, now that you have bios_grub.

---

### Post by pvollma on 2013-08-12
OK, just to make sure, you're saying that I can boot from the boot repair DVD and let it repair the boot record on sda, and this should NOT affect the existing Ubuntu 10.04 on sdb? This is important, as I don't want to have to recreate everything I have now from memory or backups, but in an orderly manner by mounting the sdb drives in 12.04 (when booted from the 12.04 Live DVD, I am able to mount and access both / and /home on sdb). Thanks!

---

### Post by oldfred on 2013-08-12
You can also uncheck the auto repair, but then check the fix mbr. Under boot options then it should give you choices of what to install where.

---

### Post by pvollma on 2013-08-12
Great, now I'm in a boot-repair loop! I get a quick couple of messages and progress bars about repairs being made, and then the message "Filesystem repair requires to unmount partitions. Please close all your programs. Then close this window." No matter what I do, either close with the window "X" or click "OK" the same quick messages appear and then I get this. I started no other programs, so I don't know why it's complaining about unmounting a partition.

---

### Post by Geezanansa on 2013-08-12
Did you note down Boot Info Script url?  Post it here if you did or if you can!.
It may be because Windows has been restarted, still has fast boot enabled or some other reason preventing complete unmounting of Windows partition.  
You could try booting Windows (if you can) and use the shutdown (instead of restarting) option after making sure all hibernation and fast boot options are off.
Restart machine booting boot-repair/live media and try running boot-repair once again.

---

### Post by pvollma on 2013-08-12
> **Geezanansa said:**
> Did you note down Boot Info Script url?  Post it here if you did or if you can!.

**Both scripts (before repartitioning and afterwards) are posted above**
.
It may be because Windows has been restarted, still has fast boot enabled or some other reason preventing complete unmounting of Windows partition.
  
**There is no longer a Windows partition on sda**

You could try booting Windows (if you can) and use the shutdown (instead of restarting) option after making sure all hibernation and fast boot options are off.

**No Windows to boot**

Restart machine booting boot-repair/live media and try running boot-repair once again.

**I suspect you did not read the entire thread**

---

### Post by pvollma on 2013-08-12
OK, I'm about ready to give up on this crap! Since I couldn't get out of the boot-repair loop, I booted from the Live DVD, and ran the installation again, this time directing the boot record to sda (not sda1). Same exact problem when I try to boot from sda. The boot repair file for this iteration is at [http://paste.ubuntu.com/5979711/](http://paste.ubuntu.com/5979711/).

---

### Post by oldfred on 2013-08-12
Are you running Boot-Repair from your install or a liveCD? It may need you to run from liveCD.

       LighterWeight (Lubuntu based) Boot-RepairCD
[http://sourceforge.net/projects/boot-repair-cd/files/](http://sourceforge.net/projects/boot-repair-cd/files/)
Full Ubuntu 13.04 liveDVD or USB Install with Boot-Repair included (for newer computers) 
[https://help.ubuntu.com/community/LinuxSecureRemix](https://help.ubuntu.com/community/LinuxSecureRemix)

---

### Post by pvollma on 2013-08-13
I'm running Boot-Repair from a Boot-Repair Live DVD.

---

### Post by pvollma on 2013-08-13
Tried one more test: I installed GParted on my 10.04 system, deleted all the partitions on sda, and created a partition table on sda. I then shutdown 10.04, booted from the 12.04 LiveDVD, and selected "Install 12.04 alongside 10.04", letting the installation do all the partitioning for me. Once the installation completed, I let the system reboot, and, of course, it booted into 10.04! Gparted shows sda partitioned as follows:

unallocated   unallocated   1.00 MiB
/dev/sda1     unknown       1.00 MiB  bios_grub
/dev/sda2     ext4             923.62 GiB
/dev/sda3     linux-swap     7.89 GiB  

Why is the installation program simply not working, no matter what I try? At this point, I'm afraid to try anything else, as it might hose my existing 10.04, and then I'm really dead in the water.

---

### Post by oldfred on 2013-08-13
But are you still booting from the MBR in sdb which still has the grub from 10.04, and your new grub is in the MBR for sda? Change boot order in BIOS or with one time boot key to see what boots from sda?

---

### Post by pvollma on 2013-08-13
When I bring up the BIOS boot device selection menu, and select the sda drive, I get the exact same error messages I described in the post that opened this thread. Nothing I have done has changed this, and the boot repair files I've submitted have not seemed to give anyone a clue as to what is wrong.

---

### Post by oldfred on 2013-08-13
If you boot from sda, exactly what message do you now get? If you are getting no boot loader then it is looking for a UEFI bootable system in an efi partition. You need to turn off UEFI and change to CSM mode for BIOS compatibility.

---

### Post by pvollma on 2013-08-13
As I said in the post to which you replied, I get the same error messages listed in the post that opened this thread:

no upper memory
Aborted. Press any key to exit.

After pressing a key:

Error 1962: No operating system found. Press
any key to repeat the boot sequence.

The BootInfo file for this installation is [http://paste.ubuntu.com/5982752](http://paste.ubuntu.com/5982752)

If the BIOS is so sensitive to some mode it's in, why does it consistently boot my 10.04 system, which was installed on an entirely different machine, and the hard drive moved to this one?

---

### Post by oldfred on 2013-08-13
It could be just that you do not have a boot flag. I have only seen that with Intel motherboards, but it can also be on a gpt partitioned drive. With gpt partitioned drives you are only supposed to have a boot flag on the efi partition. But if in BIOS mode you do not need or usually have an efi partition. 
But some BIOS will not boot without the boot flag.

With gparted the boot flag indicates an efi partition. I might just make another small partition and add a boot flag. Not sure if then it may complain that you do not have any efi files. But in BIOS mode that should not matter.

Some UEFI/BIOS have settings where they look for an efi partitition and boot files, then if not found, look in MBR for boot signature, and then if not found give a boot error. Grub does not use nor need a boot flag in BIOS mode, only Windows. So any BIOS that has to have a boot flag is designed just for Windows.

[http://forums.lenovo.com/t5/IdeaCentre-Desktops-Home-Servers/b540p-error-1962-no-operating-system-found/td-p/1068069](http://forums.lenovo.com/t5/IdeaCentre-Desktops-Home-Servers/b540p-error-1962-no-operating-system-found/td-p/1068069)
Following the link to more info says boot flag could be an issue. Boot repair shows correct partitions & MBR so those should not be issues, but who knows what these new CSM (BIOS) look for.

---

### Post by pvollma on 2013-08-14
By "boot flag" do you mean a partition with the flag "bios_grub?" The first partition has that flag (it was created by the installation program -- for this last try, I deleted all the sda partitions, told gparted to create a partition table, and then let the installation program do whatever it wanted).

---

### Post by oldfred on 2013-08-14
I do not think it matters what partition has boot flag, but I would not use any existing partitions as the boot flag changes the gpt ID to be the efi partition, not bios_grub nor data. So I might just create a tiny one with the flag to see if that is the issue. Not sure.

---

### Post by pvollma on 2013-08-14
Just so I understand what you're recommending -- do I run gparted (from 10.04), delete all the sda partitions, create 1 small partition with the flag of bios_grub, and then boot from the 12.04 DVD and let the installation create everything else?

---

### Post by oldfred on 2013-08-14
Do not use gparted from 10.04, it is really old now and does not have much gpt support. You really need the newer version with the Ubuntu live install or the very newest as a repairCD.

       [http://partedmagic.com/](http://partedmagic.com/)
[http://gparted.sourceforge.net/faq.php](http://gparted.sourceforge.net/faq.php)

---

### Post by pvollma on 2013-08-14
I am running Gparted from the Boot Repair DVD. I deleted all the partitions on sda, but when I create a new, small partition (1 MiB minimum) on sda, I cannot assign any flags to it (the "Manage Flags" option is greyed out when I select the new partition. For file system I used unformatted.

---

### Post by oldfred on 2013-08-14
Post this (better in code tags to preserve formatting, # on advanced edit menu) and a screen shot from gparted.

       sudo parted /dev/sda unit s print

---

### Post by pvollma on 2013-08-14
Model: ATA ST1000DM003-1CH1 (scsi)
Disk /dev/sda: 1953525168s
Sector size (logical/physical): 512B/4096B
Partition Table: gpt


Number  Start        End          Size         File system     Name  Flags
 1      2048s        4095s        2048s                              bios_grub
 2      4096s        1936973823s  1936969728s  ext4
 3      1936973824s  1953523711s  16549888s    linux-swap(v1)

This is a screen shot from gparted running on 10.04, after clearing sda of partitions and letting the installation program partition the drive.

  [IMG]http://www.pcvsoftware.net/temp/Screenshot.png[/IMG]

---

### Post by oldfred on 2013-08-14
If you shrink sda2 by a few MB and create a new partition formatted FAT32 can you not add a boot flag?

---

### Post by pvollma on 2013-08-15
I booted with Boot Repair disk, deleted all partitions on sda, created a 100MB FAT32 partition, then assigned the bios_grub flag to it. After applying the changes, I shutdown and rebooted the 12.04 installation disk. I did not do any further partitioning, just select "Install 12.04 alongside 10.04 ... and be able to pick which operating system to boot." The install ran fine (as it always does). I also saw the "Installing grub2 on sda ..." message complete. And, as usual, when I boot from sda, I get the same messages about no upper memory and no operating system found. Fortunately, I can still boot my 10.04 from sdb. One thing I did notice -- in the BIOS boot menu, sda is SATA1, the DVD drive is SATA2 and sdb is eSATA1. Does that explain why my old drive still boots?

---

### Post by ubfan1 on 2013-08-15
The bios_grub flag is not the "boot" flag.  The boot flag is called "boot".

---

### Post by pvollma on 2013-08-15
That made no difference -- I created a 100MB partition with a flag of "boot" and then ran the 12.04 installation again. Same error messages as previously reported.

[IMG]http://www.pcvsoftware.net/temp/Screenshot-1.png[/IMG]

---

### Post by oldfred on 2013-08-15
Do you have old drive plugged in as an external using eSata. Or are there different ports inside your system?

Perhaps it only boots the eSata in BIOS mode but you have UEFI on so sda is not seen as a BIOS boot drive?
But some systems in CSM mode try to boot UEFI from efi partition, then if not found will boot from MBR, and then only if MBR not found give the error on no bootable system.

---

### Post by pvollma on 2013-08-15
My old drive was installed in the machine by Best Buy, so I don't know how they set it up, but it shows as eSATA in the BIOS boot menu. You use all these terms like "CSM mode" and "UEFI" about which I don't have a clue. Is there a version of Ubuntu that can be installed without all this hassle? The drive has been wiped clean several times, to the point where it must look like a new drive out of the box. Are you saying that 12.04 cannot be installed on a new drive, that some magic incantation in required before the system will work? I get no error messages when doing the installation, no error message from Boot Repair, and now the Boot Repair guys at gmail.com want me to contribute something (i.e., money) to look at the BootInfo summary I've posted. To say my frustration level with Ubuntu has peaked is really an understatement. I appreciate your attempts to help, but it shouldn't be this difficult!

---

### Post by pvollma on 2013-08-15
I brought up the BIOS setup, here's what is lists for "Startup:"

CSM [Enabled]
Boot Mode [Auto]
Boot Priority [Legacy First]
Quick Boot [Disabled]
Rapid Boot [Disabled]
   keyboard stuff ...

Any help?

---

### Post by oldfred on 2013-08-15
The settings you have posted above seem to be what you should want for UEFI/BIOS settings.

Ubuntu installs to UEFI systems or BIOS systems. But not all systems are the same and some vendors do not comply with standards. They are making many corrections to their UEFI/BIOS on the motherboard.
And grub is finding bugs and creating work arounds for some of the bugs in many UEFI systems.

All new systems with Windows 8 pre-installed have the new UEFI which replaces BIOS. But UEFI has a BIOS compatibility mode called CSM/BIOS/Legacy depending on vendor. The UEFI standard is the Compatibility Support Module (CSM), which emulates a BIOS mode.

But the error you are getting still seems to be Windows related as the BIOS is expecting Windows. In Google that error goes back several years, so it has been posted many times before.
Comments seem to say Lenovo has hard coded Windows into system. But you do not have to have Windows just that it sees files with the Windows boot names.
[http://forums.lenovo.com/t5/ThinkStation/UEFI-Mode-installation-of-Linux-distributions-on-Thinkstation/td-p/1018555](http://forums.lenovo.com/t5/ThinkStation/UEFI-Mode-installation-of-Linux-distributions-on-Thinkstation/td-p/1018555)


This seems to be similar to your issue. Modified UEFI to only boot certain systems.
 Lenovo ThinkCentre M92p only boots Windows or Redhat.
[http://www.phoronix.com/scan.php?page=news_item&px=MTIyOTg](http://www.phoronix.com/scan.php?page=news_item&px=MTIyOTg)
[http://mjg59.dreamwidth.org/20187.html?thread=774619](http://mjg59.dreamwidth.org/20187.html?thread=774619)

---

### Post by pvollma on 2013-08-17
[SIZE=2][FONT=arial]I followed the instructions in the first link of your latest post. [COLOR=#333333]After running the installation, and then booting from the installation DVD again, I installed efibootmgr as directed. However, when I enter[/COLOR][/FONT][/SIZE][COLOR=#333333][FONT=Arial][SIZE=2][FONT=arial] [/FONT][/SIZE][/FONT][/COLOR]
[COLOR=#333333][FONT=Arial][SIZE=2][FONT=arial]sudo efibootmgr -v[/FONT][/SIZE][/FONT][/COLOR]
[COLOR=#333333][FONT=Arial][SIZE=2][FONT=arial] [/FONT][/SIZE][/FONT][/COLOR]
[COLOR=#333333][FONT=Arial][SIZE=2][FONT=arial]I get[/FONT][/SIZE][/FONT][/COLOR]
[COLOR=#333333][FONT=Arial][SIZE=2][FONT=arial] [/FONT][/SIZE][/FONT][/COLOR]
[COLOR=#333333][FONT=Arial][SIZE=2][FONT=arial]Fatal: Couln't open either sysfs or procfs directories for accessing EFI variables. Try 'modprobe efivars' as root.[/FONT][/SIZE][/FONT][/COLOR]
[COLOR=#333333][FONT=Arial][SIZE=2][FONT=arial] [/FONT][/SIZE][/FONT][/COLOR]
[COLOR=#333333][FONT=Arial][SIZE=2][FONT=arial]which also fails with a fatal error.[/FONT][/SIZE][/FONT][/COLOR]

---

### Post by oldfred on 2013-08-17
I was just reading a review of new UEFI motherboards. They have both SATA & ESata ports on motherboard. I might check which ports your drives are installed into.

Some UEFI systems just do not offer all the features (that they should offer). You may be able to install Intel's UEFI software, but I have never tried that. And it does not look exactly straight forward.

 [https://help.ubuntu.com/community/UEFIBooting#UEFI_Shell](https://help.ubuntu.com/community/UEFIBooting#UEFI_Shell)
EFI/boot/bootx64.efi.efi" ---> Brings up 'EFI shell environment' with command prompt.
Launch EFI Shell from File System Device
[https://wiki.archlinux.org/index.php/Unified_Extensible_Firmware_Interface#UEFI_Shell](https://wiki.archlinux.org/index.php/Unified_Extensible_Firmware_Interface#UEFI_Shell)
[http://software.intel.com/en-us/articles/efi-shells-and-scripting/](http://software.intel.com/en-us/articles/efi-shells-and-scripting/)

---

### Post by pvollma on 2013-08-18
You're not going to believe this, but on a lark I re-ran Boot Repair again, selecting the fix option, and it now boots to Grub and offers me the choice to boot 12.04 or an earlier version, and 12.04 boots! I have no idea what changed since the last time I tried this, or what, if anything, I did differently (not sure I can mark this thread as SOLVED!). Anyway, one curious thing is that Grub presents me with the option of the 12.04, older version, and then a list of 10-15 kernels (mostly, if not all, the same version). Where is this list coming from, and how can I trim it?

Thanks again for sticking with me through all this frustration. Now I can transfer that frustration to trying to figure out Unity!

---

### Post by oldfred on 2013-08-19
Glad you got it to work.

I have a 4:3 monitor and preferred the gnome2 menus as I have more vertical space. All new monitors are widescreen, so having Unity makes a bit more sense with those. So I installed fallback or gnome panel.
       gnome3 classic
sudo apt-get install gnome-panel
On login screen click on logo/cog-wheel/star and choose 
[http://www.psychocats.net/ubuntu/classicgnome](http://www.psychocats.net/ubuntu/classicgnome)
12.04 LTS / Precise Classic (No effects) Tweaks and tricks kansasnoob & cortman
[https://help.ubuntu.com/community/PreciseGnomeClassicTweaks](https://help.ubuntu.com/community/PreciseGnomeClassicTweaks)
[http://ubuntuforums.org/showthread.php?t=1966370](http://ubuntuforums.org/showthread.php?t=1966370) 
[http://ubuntuforums.org/showthread.php?t=2090021](http://ubuntuforums.org/showthread.php?t=2090021)
[http://www.omgubuntu.co.uk/2012/03/gnome-classic-in-ubuntu-12-04-its-like-nothing-ever-changed](http://www.omgubuntu.co.uk/2012/03/gnome-classic-in-ubuntu-12-04-its-like-nothing-ever-changed)

You may have old kernels in old install and grub2 adds all of them. If you can boot old install you can houseclean kernels. I have lots of old installs from tests, but have not housecleaned them. So I turn off os-prober and only add a few entries into 40_custom for versions I may want to try to boot.

      
 How to: Create a Customized GRUB2 Screen that is Maintenance Free.- Cavsfan
[https://help.ubuntu.com/community/MaintenanceFreeCustomGrub2Screen](https://help.ubuntu.com/community/MaintenanceFreeCustomGrub2Screen)
[http://ubuntuforums.org/showthread.php?t=2076205](http://ubuntuforums.org/showthread.php?t=2076205)

If you boot old install:
 Determine your current kernel:
uname -a
uname -r
In synaptic search for linux-image to choose to delete old ones
Also command line in post #8
[http://ubuntuforums.org/showthread.php?t=1283521](http://ubuntuforums.org/showthread.php?t=1283521)

---

