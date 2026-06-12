---
title: "Moving old SSD to new Lenovo MiniPC"
date: 2021-06-21
forum: Installation &amp; Upgrades
---

### Post by MarcoPau on 2021-06-21
Hi all, I know this is a common topic but couldn't manage to sort it out by reading other people's threads...

I have a Pentium with Z270 chipset system with a 2.5 inches SSD I'd like to move to my newer Lenovo Thinkcentre minipc with i5 and M.2 SSD. 

For now, can't even manage to boot grub after moving the 2.5 in SSD to the Lenovo. 

Do I have any option rather than starting a new Ubuntu from scratch?

Thanks!

---

### Post by ubfan1 on 2021-06-21
How is Ubuntu installed on the ssd from the Pentium, legacy or UEFI?  Is your Thincentre set up to boot that type of install?  You might be able to convert a legacy install to UEFI by adding a EFI partition, then installing grub there.  A bit of cleanup is recommended after such an action, but that's doable after you get it running.

---

### Post by grahammechanical on 2021-06-21
Excuse me, but you fail to tell us which version of Ubuntu is on that 2.5 inch SSD. If the hardware in your newer machine is newer than the release date of the version of Ubuntu then the operating system most likely will not have hardware drivers for much of the new hardware.

When using Ubuntu on the Pentium did you run it with a proprietary video driver? Best to revert to using an open source video driver. There is a better chance that an open source video driver will work on the newer machine than the proprietary video driver.

You need to confirm that the BIOS/UEFI settings utility of the newer machine actually sees the 2.5 inch SSD as a boot option. Does the Thinkcentre have an existing operating system? Is it Windows? You need to determine if Windows is installed in BIOS/Legacy/Compatibility mode or UEFI mode. Also what mode was Ubuntu installed in? BIOS mode or UEFI mode. When dual booting both operating systems should be installed in the same mode to avoid problems like this.

Regards

---

### Post by MarcoPau on 2021-06-22
Thank you guys for your contribution.

Thinkcentre has a windows on its M.2 drive. Ubuntu version is groovy with open source video drivers.

The 2.5 drive is seen as a boot option in fact I set it as primary boot in the thinkcentre.

If I enter setup on both systems I see Bios version xxxx, does this mean I am running a Bios install on both of them?

/sys/firmware/efi is missing on Ubuntu, thus I assume at least Ubuntu is Bios mode.

---

### Post by tea for one on 2021-06-22
Return your Ubuntu SSD to its original PC, boot Ubuntu and open a terminal:-
```
[ -d /sys/firmware/efi ] && echo "UEFI mode" || echo "Legacy mode"
```
I suspect Windows 10 is in UEFI mode, you can check via 
System Information > System Summary > BIOS mode > UEFI

Are both modes UEFI?

---

### Post by MarcoPau on 2021-06-23
Linux is in BIOS mode, Windows is UEFI.

Any option?

---

### Post by ubfan1 on 2021-06-23
If I understand correctly, you have a windows disk with Windows in UEFI mode, and another disk with Ubuntu in legacy mode.  The minimum needed to boot Ubuntu in UEFI mode is to get the grubx64.efi and shimx64.efi and grub.cfg into your ...EFI/ubuntu directory, and edit the grub.cfg to put in your UUID, hdx and parttiion number for your Ubuntu root.  That's it.  Wont boot Windows, but you can do that directly from the EFI menu (some key at powerup to allow you to select device/os to boot).  Then you can add the /boot/efi mount point, add the fstab entry for the EFI there, install the grub-efi-amd64-signed and shim-signed, and rerun the update-grub to rewrite the grub.cfg to allow Windows to boot.  I was surprised that a legacy grub.cfg would actually boot Ubuntu in UEFI mode, but I had to do something similar at one time -- installed Ubuntu to a new disk in legacy mode, then converted it to UEFI.  I had just copied all the EFI/ubuntu files from another working computer, and edited the grub.cfg.

---

### Post by oldfred on 2021-06-23
Most legacy installs are on MBR(msdos) partitioned drives.
Windows requires gpt partitioning for UEFI installs.
But since Ubuntu will let you use MBR with UEFI (it maybe should not), you just need to reinstall grub in UEFI boot mode and that will convert your install to UEFI boot whether drive is gpt or MBR. It probably will use ESP - efi system partition on Windows drive, so you do not even have to add an ESP on Ubuntu drive.

Most find Boot-Repair easier, although you also can chroot into system. But you need to boot Ubuntu live installer in UEFI boot mode.
Lets see details, use ppa version with your live installer (2nd option) or any working install,  not Boot-Repair ISO:
Please copy & paste the pastebin link to the Boot-info summary report ( do not post report), do not run the auto fix till reviewed.
 [https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair) & 
[https://sourceforge.net/p/boot-repair/home/Home/](https://sourceforge.net/p/boot-repair/home/Home/)

Long term plan on converting drive to gpt & reinstalling in UEFI boot mode.

---

### Post by MarcoPau on 2021-06-26
[https://paste.ubuntu.com/p/gwCQS65pBy/](https://paste.ubuntu.com/p/gwCQS65pBy/)

Please note that I would like to move the ubuntu installation from the 2.5 SSD to the new M.2 drive that came with the Lenovo PC and where Windows is installed.

I am now on ubuntu live and that's the link to the boot repair info. I am taking advantage of the live boot to resize the M.2 drive and create the ext4 partitions.

I used to have a big swap on a secondary 2 TB 2.5 drive I will fit into the Lenovo after finishing the migration. Do you think it is a good idea to keep the swap on the secondary HD instead of creating a swap partition on the M.2 drive?

Cheers.

---

### Post by tea for one on 2021-06-26
Therefore, you want both operating systems on your nvme drive?
If so, use [COLOR="#0000FF"]Windows tools[/COLOR] to shrink the Windows partition to make free space.

_General Observations for Dual Boot Windows 10 & Ubuntu Family_

Not all are applicable in every case.

Backup your data
Both systems in UEFI mode with GPT
[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

_UEFI settings_

Disable Secure Boot
Disable Fast boot 
Disable Legacy mode 
Check that Legacy USB Support is enabled
Change SATA mode to AHCI where the default is RAID or Intel RST (Windows may need AHCI driver)
Disable TPM

_Windows 10_

Backup your data
Turn off Bitlocker
Disable Fast Start Up i.e. Windows is not hibernating
Disable applications which manage Intel Optane memory & storage
Disk must be GPT
Install Windows 10 in UEFI mode
Check via System Information > System Summary > BIOS mode > UEFI
Windows will have  an EFI partition (needed by Ubuntu later)
Use Windows tools to reduce Windows partition size and create free space
Reboot Windows to allow chkdsk to run
Windows may need AHCI driver
[https://discourse.ubuntu.com/t/ubuntu-installation-on-computers-with-intel-r-rst-enabled/15347](https://discourse.ubuntu.com/t/ubuntu-installation-on-computers-with-intel-r-rst-enabled/15347)

_Ubuntu Family_

Boot into a live session in UEFI mode (how you boot determines the installation mode)
Check wifi, sound, graphics, mouse, keypad etc
Use gparted to create a GPT (GUID Partition Table)
Install Ubuntu in the free space previously created (or your own partition scheme e.g. separate root and home)
Allow the installer to automatically create the necessary partitions.
Grub will find the EFI partition already used by Windows
Sometimes (although very rare) internet connection prevents clean installation

---

### Post by MarcoPau on 2021-06-26
Exactly, I would like to move my Ubuntu from the 2.5 SSD to the nvme drive where Windows is now installed. Don't care about the Windows I have on my 2.5 SSD since I rarely boot Windows, I keep it installed just in case...

Wouldn't you use gparted to resize the Windows partition and make free space for Linux?

How should I manage copying my Ubuntu from 2.5 SSD to nvme drive?

Thanks for helping!

---

### Post by oldfred on 2021-06-26
While gparted may be able to resize a NTFS partition, on occassion some corruption occurs. Users blame Linux, but almost always a Windows issue that existed before.
So best to use Windows to resize NTFS partitions and reboot immediately into Windows and run chkdsk on any resized partitions. 
Windows tools for Windows, Linux tools for Linux.

I have always believed in new install & restore from your normal backup.
That confirms you backups are complete as you still have old drive to get anything you missed.
With gpt difficult to image copy a partition as GUIDs are in primary partition table, backup partition table & partition. While possibly repairable to resync them, best to not to try to copy partition.

---

### Post by tea for one on 2021-06-26
> **MarcoPau said:**
> Wouldn't you use gparted to resize the Windows partition and make free space for Linux?

As mentioned by [COLOR="#0000FF"]oldfred[/COLOR], Windows tools to manipulate Windows partitions.

> **MarcoPau said:**
> How should I manage copying my Ubuntu from 2.5 SSD to nvme drive?

It will be painful (almost impossible) to cleanly copy a BIOS Ubuntu installation to a drive where Windows is installed in UEFI mode.

This approach will inevitably lead to boot problems.

New installation of Ubuntu is the only answer.

Did you not take notice of this info [https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)?

Have you backed up your data?

---

### Post by tea for one on 2021-06-26
Another thought.

Which OS do you use (or intend to use) most frequently?
Two drives + two operating systems, it would be ideal to have two completely separate installations (each on an individual drive.).

Priority OS on the faster nvme drive?

Reduces problems with Grub because you can boot via UEFI.

---

### Post by MarcoPau on 2021-06-26
> **tea for one said:**
> Another thought.

Which OS do you use (or intend to use) most frequently?
Two drives + two operating systems, it would be ideal to have two completely separate installations (each on an individual drive.).

Priority OS on the faster nvme drive?


Like I said, I rarely (almost never) boot Windows.

Priority is Linux on nvme, being faster. I will then use the 2.5 inch slot for my 2 TB HD for general data.

---

### Post by tea for one on 2021-06-26
Then, what is preventing you installing Ubuntu on your nvme drive removing Windows in the process?

---

### Post by MarcoPau on 2021-06-27
> **tea for one said:**
> Then, what is preventing you installing Ubuntu on your nvme drive removing Windows in the process?
The fact that once in a while I need Windows.

---

### Post by MarcoPau on 2021-06-27
Or were you maybe meaning I could get rid of windows momentarily and reinstall it afterwards (on the 2TB HD in case?)?

In this case, it'd be easy to copy my Linux from the 2.5 inch ssd to a virgin nvme?

---

### Post by tea for one on 2021-06-27
No, not really, I was suggesting that you remove Windows completely as it seemed you did not really need it.

Anyway, you are in a privileged position with two drives and you should be able to decide:-

Each OS on a separate drive?
Both OS on your nvme drive?

Was Windows 10 pre-installed on the nvme drive (it is often tied to the hardware by the manufacturer and probably difficult to relocate to your second drive)?

I notice that you have not yet confirmed that you have data back-ups.
Have you done this essential task?

---

### Post by MarcoPau on 2021-06-27
Sure I backed up already, sorry if I didn't answer explicitly.

Don't know if Win10 is tied to the hw, thou it is pre installed.

Don't have a preference between having both os's on the same nvme or each on a different drive. I'd care about making it simpler, since I am not so keen for hacking on the computer for hours in order to run my Linux on the new computer :-)

---

### Post by tea for one on 2021-06-27
I also crave simplicity.

Therefore, this is my suggestion:-

Leave Windows 10 on the nvme drive (it is already UEFI and GPT) and install Ubuntu on your second drive.

Refer to the observations in my post 10 about UEFI and Windows 10 settings.

_Existing Windows and then Ubuntu on Separate Disks_

De-activate, disconnect, isolate or physically remove existing OS drive so that only the target drive is accessible
Boot Ubuntu live and check that you are in [COLOR="#0000FF"]UEFI[/COLOR] mode:-
```
[ -d /sys/firmware/efi ] && echo "UEFI" || echo "Legacy"
```
Create GPT on your target disk using gparted
Open gparted > Device > Create Partition Table > Select [COLOR="#0000FF"]gpt[/COLOR]
Allow the installer to automatically create the necessary partitions (or your preferred configuration)
Boot each system independently via UEFI boot screen (ideal not cumbersome)
Boot priority can be controlled by UEFI
Each OS should be installed in UEFI mode with GPT
Each drive should have EFI partition
Each drive should have boot manager (Windows Boot Manager and Grub for Ubuntu)
De-activate, disconnect, isolate or physically remove one drive so that you can check if the other boots independently (and vice versa)

---

### Post by MarcoPau on 2021-06-27
Yeah but this means I am going to have to install Linux on my HD instead of the nvme.

And this is not the priority we were talking about: having my mostly used os (Linux) on the fastest drive.

---

### Post by tea for one on 2021-06-27
> **MarcoPau said:**
> Don't have a preference between having both os's on the same nvme or each on a different drive. I'd care about making it simpler, since I am not so keen for hacking on the computer for hours in order to run my Linux on the new computer :-)

You mentioned that you don't have a preference, yet you do have a preference.

Both OS on same drive, please refer to observations in post 10.

---

### Post by MarcoPau on 2021-06-27
Yep, I wasn't considering the option of having Linux on the second drive since priority was to have Linux on the fast nvme drive.

Great, so I assume I am going to have to start from scratch and then rsync (or cp?) all my home directory and manually install all the packages? Or maybe firstly install packages, then rsync/cp home dir in order to overwrite the settings files...?

Isn't there any tool that allows to somehow automate the installation of the packages, settings files, graphic environment settings, etc?

---

### Post by oldfred on 2021-06-27
My rsync backup script file includes this export also. The dpkg list is a very long text list of all applications and the dependencies. 
If upgrading, you may want to edit it to remove obsolete, old kernels or others. It will not re-install anything already installed.
[https://help.ubuntu.com/community/ReinstallingSamePackages](https://help.ubuntu.com/community/ReinstallingSamePackages)

Follow all the suggestions by tea for one as those are what we have found need to be done.
Remove esp flag from Windows before install to second or external drive - Tim Richardson
[https://askubuntu.com/questions/16988/how-do-i-install-ubuntu-to-a-usb-key-without-using-startup-disk-creator/1056079#1056079](https://askubuntu.com/questions/16988/how-do-i-install-ubuntu-to-a-usb-key-without-using-startup-disk-creator/1056079#1056079)

Posted work around to manually unmount & mount correct ESP during install #55 or( #23 & #26)
 [https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1396379](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1396379)
Others suggest disconnecting all other drives physically or logically in UEFI settings, so install drive is first drive.
Or removing boot flag/esp flag from first drive, so only ESP is install drive. (I have not had that work, but others have.)
Or if you have ESP on second or external drive, you can just reinstall grub, either manually or using Boot-Repair's advanced mode & full reinstall of grub to correct drive.

---

### Post by teddymills on 2021-06-27
I stopped doing OS migrations. I just did new OS installs and installed whatever apps were needed. It was much faster.

---

### Post by MarcoPau on 2021-06-27
> **oldfred said:**
> My rsync backup script file includes this export also. The dpkg list is a very long text list of all applications and the dependencies. 
If upgrading, you may want to edit it to remove obsolete, old kernels or others. It will not re-install anything already installed.
[https://help.ubuntu.com/community/ReinstallingSamePackages](https://help.ubuntu.com/community/ReinstallingSamePackages)


Hi, I am trying this dpkg command but when I do set selections I get a whole list of "unknown packages".

I need to say that I am going from groovy to hirsute, but I guess it doesn't really matter.

---

### Post by oldfred on 2021-06-27
Exported file should look like this:

```
accountsservice                    install
acl                        install
acpi-support                    install
acpid                        install
adduser                        install
adwaita-icon-theme                install
```

#IF you get this error:
dpkg: warning: package not in database
sudo apt-get install dselect
sudo dselect 
   -> Update
   -> Install

---

### Post by MarcoPau on 2021-06-27
Done, and rsynced the home dir.

Was incredibly fast considering the new nvme drive.

Your script looked like skipping lxqt, but then manually installed.

This time I ended up using one single partition for / and home, opposite to what I've been used to.

Windows is booting also.

Thanks for helping me out!

---

