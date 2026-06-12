---
title: "Installing Ubuntu isn't going well..."
date: 2020-07-16
forum: Installation &amp; Upgrades
---

### Post by lycosa on 2020-07-16
Hello everyone, thank you for taking the time to read this. I've been attempting to install Ubuntu for a couple days now. It's not going well. The problem is, I find tidbits of advice all over the internet saying 'try this it worked for me' and a couple of times I've had to completely restore the computer to factory settings because I almost bricked my laptop. 

So here I am... asking for mercy to get this project over with.

My specs on the laptop:

HP Omen laptop 15-ek0013dx
Intel i7 - 10750H processor
512gb Intel SSD 
32gb Intel optane
16gb ddr4
Windows 10
Nvidia GeForce 2060 RTX 6gb vram
Bios vendor: AMI
Bios Revision: F.01

I'm trying to install Ubuntu 20.04

I've tried a lot of different things in quite a few install guides. I've tried shrinking the volume and it finally installed, but couldn't get the grub menu and nothing I did to enable grub, including boot-repair from the live usb fixed that. Currently, I've removed the volume created for Ubuntu and have fatory reset everything. If there's an install guide out there that I haven't seen that addresses issues that I might run into with my particular laptop, I'd appreciate a pointer to that article as I haven't found one yet. I've installed Ubuntu along side Windows several times before but I've never had any issues. This time I couldn't get Ubuntu to see that I had Windows installed no matter what tricks I tried and the only time it did show up as an option was when I shrank the windows volume and suddenly after reboot Ubuntu saw the Windows installation and allowed me to 'install alongside Windows'. However, grub was no where to be found and it booted straight to Windows regardless of how many articles and supposed solutions I tried. 

I'm taking a couple classes that require me to use Linux and I'm really in need of getting this done. There's obviously something I'm doing wrong and it seems to be specific to my computer. Any solid help would be greatly appreciated! Thanks

---

### Post by CatKiller on 2020-07-16
There are two things about your machine that make things difficult.

Optimus setups, where you have both Intel and Nvidia graphics, are just a pain. Intel's graphics driver is open source and integrates well with the wider Linux graphics stack, and Nvidia's graphics driver is neither. Getting them to work together hasn't been a priority for Nvidia, and no one else can really do it because the driver is proprietary.

You're trying to dual boot, and Windows makes that difficult by leaving its partitions in a dirty state which can't be modified. It's because Windows hibernates rather than shutting down properly. They call it Fast Startup. 

You can't just run magical incantations that you find on the Internet and expect them to work. You need some understanding of the behaviour of your machine and what you're trying to achieve.

---

### Post by oldfred on 2020-07-16
HP is not the easiest to dual boot.

Have you updated UEFI from HP?
Many have said that helps.

You often cannot use efibootmgr to set boot order and grub uses efibootmgr to set Ubuntu as first in boot order. HP or Windows then resets to Windows first. Some say changing in UEFI settings works. Others just live with using one time UEFI boot key to choose Ubuntu as they do not reboot a lot or mostly use Windows.

Better to have posted link to Summary Report from Boot-Repair, to fix grub & then see if UEFI settings corrected it.

After you reinstall, run Boot-Repair from Ubuntu live installer & post link to Summary Report. Do not post report.

See also link in my signature for general UEFI install instructions.

Some other HP threads, issues often by vendor, and then vary if Intel or AMD. And if nVidia.

HP with optane
[https://askubuntu.com/questions/1257230/dual-boot-ubuntu-with-windows-cannot-change-from-raid-to-ahci-through-bios?noredirect=1#comment2125560_1257230](https://askubuntu.com/questions/1257230/dual-boot-ubuntu-with-windows-cannot-change-from-raid-to-ahci-through-bios?noredirect=1#comment2125560_1257230)
HP change boot order in UEFI boot
[https://ubuntuforums.org/showthread.php?t=2441981&p=13952881#post13952881](https://ubuntuforums.org/showthread.php?t=2441981&p=13952881#post13952881)
HP UEFI update - extract .bin from .exe file and copy into FAT32 partition.
[https://askubuntu.com/questions/539120/how-to-perform-a-hp-bios-upgrade-with-only-ubuntu/1234098#1234098](https://askubuntu.com/questions/539120/how-to-perform-a-hp-bios-upgrade-with-only-ubuntu/1234098#1234098)
[https://h30434.www3.hp.com/t5/Notebooks-Archive-Read-Only/How-to-update-BIOS-on-Linux/m-p/5441775#M1205498](https://h30434.www3.hp.com/t5/Notebooks-Archive-Read-Only/How-to-update-BIOS-on-Linux/m-p/5441775#M1205498)
HP Elitebook 840 G5 gpt issues - 
HP put a fail-safe gpt recovery into the UEFI Settings,  go into the UEFI Menu in Security -> Hard Drive Utilities -> Uncheck "Save/restore GPT System of Hard Drive"
[https://ubuntuforums.org/showthread.php?t=2436271](https://ubuntuforums.org/showthread.php?t=2436271)

---

### Post by lycosa on 2020-07-16
I've tried disabling fast boot and that didn't work either. I truly understand that magical incantations will not work. I'm usually very hesitant to ask for help without exhausting my own efforts. This just happens to be a point where the knowledge required is beyond my current comprehension. There are multitudes of posts out there saying 'this worked for me' when referring to the problems I'm having. I thought I'd try my own hand at it before posting here and being told that the information is out there if I just practiced 'google-fu'. Anyway, I appreciate the effort. I just hope the cure isn't some mammoth time investment in educating myself when I'm already booked solid on time...

---

### Post by lycosa on 2020-07-16
Thank you. I had no idea it would turn out to be such a pain or I might have purchased a different laptop. Looks like there's a lot of work in figuring this out. Something I don't really have time for but I suppose it's something I have no other choice but to do. I need Ubuntu installed and I don't want to run a VM for linux. Thank you for the links, I'll head down that road asap. i do appreciate you taking the time to respond.

---

### Post by oldfred on 2020-07-16
Some also like to use an external SSD, so totally separate. I have used flash drives, but they are slow. I was a bit surprised how fast a SSD in USB3 port was. I thought USB3 port was part of slowness, but most from flash drive.

A full UEFI install to the external SSD requires a bit of configuration before hand and you have to manually select in UEFI whenever you want to boot it.
If interested in that we can explain further.

---

### Post by CatKiller on 2020-07-16
> **lycosa said:**
> I've tried disabling fast boot and that didn't work either. 

Fast Boot is a UEFI setting that disables hardware checks at boot on the assumption that nothing has changed. Fast Startup is a Windows setting that hibernates Windows rather than shutting down. They are not the same thing at all.

---

### Post by lycosa on 2020-07-16
Well...you learn something new everyday. At this point, I have no idea if that was part of the problem or not. I know I disabled fast startup in Windows. I disabled secure boot in Bios.... and a host of other 'advice' I seen posted thoughout the web. At this point, everything including the BIOS is back to factory defaults and until I'm armed with enough knowledge or a step-by-step guide, I'm leaving it that way. I think I caused more problems than I solved on this little adventure.

---

### Post by lycosa on 2020-07-16
> **oldfred said:**
> Some also like to use an external SSD, so totally separate. I have used flash drives, but they are slow. I was a bit surprised how fast a SSD in USB3 port was. I thought USB3 port was part of slowness, but most from flash drive.

A full UEFI install to the external SSD requires a bit of configuration before hand and you have to manually select in UEFI whenever you want to boot it.
If interested in that we can explain further.


I've seen that mentioned and honestly, that might be the way to go. I'm taking some pentesting certification classes that use Linux a lot. While I know that mostly what I'll be running are VM's of linux distros, the class has already covered some very hardware dependent processing that my new laptop can handle. Other than perhaps a little bit slower to load, it may be the simplest solution while still allowing the horsepower of the laptop to be useful.

---

### Post by oldfred on 2020-07-16
If you use an external drive with UEFI, you must partition in advance with gpt partitioning and an ESP - efi system partition. 
Best to either physically disconnect all other drives or in UEFI disable drives. Then auto install can create ESP & / (root) as default install, or you can manually partition to add /home and or data partition(s). 

If you either cannot disconnect drives, or prefer not to, then you have to either reinstall grub to external drive or see the (now old) bug report & the work around.
External drives only directly boot from ESP on external drive and /EFI/Boot/bootx64.efi file. Same file name, but slightly different version of grub is bootx64.efi on the installer. Windows installer also uses bootx64.efi.

Posted work around to manually unmount & mount correct ESP during install #23 & #26
 [https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1396379](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1396379)
I just installed Kubuntu 20.04 to my internal but sdb drive and had to do this work around. I also had to unmount /isodevice as that was on sdb for some unknown reason. I try not to overwrite my main working install's efi boot files in the ESP on sda.

Ubuntu's Ubiquity installer only installs grub boot files to first drive's ESP, usually sda or first NVMe drive and it usually has an ESP from Windows. That will work, but external drive has no boot files and can only boot on the same drive as you used to install it.

You then can use Boot-Repair to reinstall grub to correct drive, if you have formatted in advance and have the ESP (FAT32 formatted, greater than 250MB, but smaller will work if small drive).

---

### Post by lycosa on 2020-07-17
> **oldfred said:**
> If you use an external drive with UEFI, you must partition in advance with gpt partitioning and an ESP - efi system partition. 
Best to either physically disconnect all other drives or in UEFI disable drives. Then auto install can create ESP & / (root) as default install, or you can manually partition to add /home and or data partition(s). 

If you either cannot disconnect drives, or prefer not to, then you have to either reinstall grub to external drive or see the (now old) bug report & the work around.
External drives only directly boot from ESP on external drive and /EFI/Boot/bootx64.efi file. Same file name, but slightly different version of grub is bootx64.efi on the installer. Windows installer also uses bootx64.efi.

Posted work around to manually unmount & mount correct ESP during install #23 & #26
 [https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1396379](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1396379)
I just installed Kubuntu 20.04 to my internal but sdb drive and had to do this work around. I also had to unmount /isodevice as that was on sdb for some unknown reason. I try not to overwrite my main working install's efi boot files in the ESP on sda.

Ubuntu's Ubiquity installer only installs grub boot files to first drive's ESP, usually sda or first NVMe drive and it usually has an ESP from Windows. That will work, but external drive has no boot files and can only boot on the same drive as you used to install it.

You then can use Boot-Repair to reinstall grub to correct drive, if you have formatted in advance and have the ESP (FAT32 formatted, greater than 250MB, but smaller will work if small drive).

One last question before I order the drive. For speed, I have a thunderbolt USB and this is the external hard drive I'm considering: [https://smile.amazon.com/gp/product/B078STRHBX/ref=ox_sc_saved_title_1?smid=ATVPDKIKX0DER&psc=1](https://smile.amazon.com/gp/product/B078STRHBX/ref=ox_sc_saved_title_1?smid=ATVPDKIKX0DER&psc=1) 

In case you'd rather not click the link, the advertised details are:
**[SIZE=2]SanDisk 1TB Extreme Portable External SSD - Up to 550MB/s - USB-C, USB 3.1 - SDSSDE60-1T00-G25[/SIZE]**

Would that be a good candidate? I'd hate to buy something that just made it even more difficult. 
Thank you for your time and patience. I do appreciate it very much.

---

### Post by oldfred on 2020-07-17
Do not know details of any specific brand.
Those designed as external drives have some advantages over my methods.

My external SSDs are either an SATA to USB adapter (no case) or a M.2 case and my older internal M.2 SATA drive as I upgraded to faster NVMe M.2 drive. The M.2 is smaller, but not really ruggedized or waterproof.

If that large of a drive, you have room for multiple partitions.
Only if gpt -  all partitions in gpt are primary (no logicals):
gpt: 300-500 MB efi FAT32 w/boot flag (ESP for UEFI boot or future use for UEFI, you only can have one per drive, so if already existing do not attempt another)
gpt: 1 or 2 MB No Format w/bios_grub flag (for BIOS boot not required for UEFI)
for gpt(GUID) or MBR(msdos) partitioning
Ubuntu partitions - smaller root only where hard drive space is limited.
If total space less than about 30 to 50GB just use / not separate /home or standard install.
1. 30+ GB Mountpoint / primary or logical beginning ext4
2. all but 2 GB or all (See below if 18.04 or later) Mountpoint /home logical beginning ext4
3. 2 GB Mountpoint swap logical (not required with 17.04 and later uses a swap file, if no swap partition found)
4. You do not need to create swap, as it either finds existing swap partition, or creates in fstab the following swapfile entry:
5. No swap partition for 18.04 or later, it uses a swap file like this entry in fstab:
     /swapfile                                 none            swap    sw              0       0

When partitioning often better to have some idea of amount of space you may need. But with a 1TB drive you have room for /home or data partition(s) and you could leave room for NTFS shared data partition for some of your Windows data. But have to have Windows fast start up off or it sets hibernation flag and the Linux NTFS driver will not mount it read/write. And Windows turns fast start up back on with some updates.

---

### Post by SeijiSensei on 2020-07-18
I suggest installing VirtualBox on Windows, then creating a virtual machine to run Ubuntu. I have one dual-boot system for games. Otherwise I much prefer virtual machines.

[https://download.virtualbox.org/virtualbox/6.1.12/VirtualBox-6.1.12-139181-Win.exe](https://download.virtualbox.org/virtualbox/6.1.12/VirtualBox-6.1.12-139181-Win.exe)

---

