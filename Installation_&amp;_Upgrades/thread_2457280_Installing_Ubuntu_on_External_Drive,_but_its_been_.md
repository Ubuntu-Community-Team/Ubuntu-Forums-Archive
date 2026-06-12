---
title: "Installing Ubuntu on External Drive, but its been stuck on write partition changes"
date: 2021-01-29
forum: Installation &amp; Upgrades
---

### Post by cyberspace-ace0 on 2021-01-29
Hey,

Thanks for any help in advance.

I am installing Ubuntu onto my external SSD through a Usb to Sata cable, it has been on the write partition stages for over 10hrs now.

when this first happened i quit the process about 1hr30 in cause i thought it should not have took that long but after doing some research it tool some folks 4hrs before...
so then i tried it again yesterday evening but now its been 10+ hrs... not sure if im doing something wrong...

SSD info:

Crucial MX500 2.5in 1tb SSD 

and am using a Dtech Slim USB to SATA 2.0 adapter

Please let me know if anymore info is needed

---

### Post by tea for one on 2021-01-29
10 hours to create partitions suggests that something is amiss.

Is this the first time that you have installed Ubuntu?
Is this a default installation i.e. erase the disk and install Ubuntu?

If you chose to create certain partitions, can you let us know your intentions?

Lastly, installing Ubuntu on an external drive can create boot problems if the drive is not attached to the PC.
There are methods to avoid this and you should include your goals in your next post?

What operating systems are installed on your PC at the moment?

---

### Post by cyberspace-ace0 on 2021-01-29
hey,

Its not my first time installing ubuntu, but it is my first time installing on a SSD through an adapter.

i choose the something else option so that i may choose the SSD.

My intentions is to install ubuntu on this SSD and then actually put it in my desktop along side HDD that host my Win10. i wanrt to be able to boot to it when i want to. i just wamted to have it on its own drive rather than dual boot.

Right now im using Win10 Pro, i have the external SSD connected the whole time through the adapter.

i formatted the drive in windows to use the ntfs file before starting the install, more so as just a test to see if the adapter worked, it was successfull.
Could that be an issue ?

---

### Post by tea for one on 2021-01-29
> **cyberspace-ace0 said:**
> hey,

Its not my first time installing ubuntu, but it is my first time installing on a SSD through an adapter.

i choose the something else option so that i may choose the SSD.

My intentions is to install ubuntu on this SSD and then actually put it in my desktop along side HDD that host my Win10. i wanrt to be able to boot to it when i want to. i just wamted to have it on its own drive rather than dual boot.

Right now im using Win10 Pro, i have the external SSD connected the whole time through the adapter.

i formatted the drive in windows to use the ntfs file before starting the install, more so as just a test to see if the adapter worked, it was successfull.
Could that be an issue ?

Looks like your first attempt at dual booting - it can be daunting but manageable with care.

My best advice when installing to an external drive:-
Make sure that you have backups of your data.
[COLOR="#0000FF"]Isolate, de-activate or physically remove[/COLOR] your internal Windows drive to avoid human error.
Ubuntu will install the boot loader to the first drive and if your Windows drive is accessible, you will only be able to boot Windows with the external drive attached i.e. inflexible situation.
You must boot the installer in [COLOR="#0000FF"]UEFI mode[/COLOR] to be compatible with Windows 10.
Use gparted to create GPT on your external drive.
Ubuntu does **not** use ntfs - the installer will kindly create an EFI partition and an ext4 file system.
Ubuntu will be able to read files on ntfs but you cannot install Linux systems on ntfs.

More info here [https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

Dual boot with each OS on a separate device is ideal but, during the installation of Ubuntu, please [COLOR="#0000FF"]only have the target drive available[/COLOR] and your Windows OS will be preserved.
You will be able to boot each OS via your PC's dedicated key to access UEFI boot options e.g. F9 for HP or F10 for Intel.

Do you know the dedicated key for your PC?

If you are unfamiliar with anything that I have mentioned, please ask because there are some very knowledgeable and helpful users here.

---

### Post by oldfred on 2021-01-29
I have an old 60GB SSD from my old BIOS system.
Decided to try to use an adapter to use it just as a boot drive to test an install.
Even more surprised when it installed in about 10 min, which was only a bit slower than install to internal SSD and less than internal HDD.

But I partition in advance and use toram parameter so installer ends up totally in RAM. Then install goes very quickly.
You have to partition in advance to have an ESP - efi system partition on external drive. 
External drives boot from ESP using /EFI/Boot/bootx64.efi. Entry in UEFI will be a device/drive, just like the installer.
Internal drives boot from /EFI/ubuntu/boot/grub.cfg. Entry in UEFI will be "ubuntu". 

Ubuntu's ubiquity installer will default install an ubuntu entry into the internal drive, if UEFI. Does not matter what you select during install on grub boot loader location. Selection options only work with BIOS installs.
In your case default may be ok, if you are moving SSD to internal SATA port & not trying to boot directly in same or other systems.
But I like to have an ESP on every drive, even those currently without an install. So in future I can easily add an install if desired.

Posted work around to manually unmount & mount correct ESP during install #23 & #26
 [https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1396379](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1396379)
Others suggest disconnecting all other drives physically or logically in UEFI settings, so install drive is first drive.
Or removing boot flag/esp flag from first drive, so only ESP is install drive. (I have not had that work, but others have.)
Or if you have ESP on second or external drive, you can just reinstall grub, either manually or using Boot-Repair's advanced mode & full reinstall of grub to correct drive.

---

### Post by ubfan1 on 2021-01-30
[[COLOR=#000000]And do go to the bug [/COLOR]https://bugs.launchpad.net/ubuntu/+s...y/+bug/1396379]("https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1396379") and add yourself to the "Does this affect me?" list at the upper left.  The bug is seven years old, and is a superset of an even older bug for USB, so it looks like turning up the heat is the only way it will be fixed.

---

