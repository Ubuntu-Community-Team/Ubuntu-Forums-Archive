---
title: "can only boot from bios menu"
date: 2018-07-03
forum: Installation &amp; Upgrades
---

### Post by bart-burroughs-cox on 2018-07-03
I have a strange situation. I purchased a new HP Omen desktop with Windows installed on a 256GB solid state drive and a 1TB SCSI drive as well. I turned off secure boot in the bios and I installed Ubuntu 18.04 in UEFI mode using the existing efi partition on the solid state drive by setting the flag to boot in gparted and then installing Ubuntu on the 1 TB SCSI drive using 2 partitions a root and home partition. everything installed fine and I can boot into Ubuntu just fine but only if I hit the esc key every time I boot and then continue from the bios popup screen which then gives me the grub menu to boot into ubuntu or windows. If I let it attempt to boot without that step I get a black screen with a grub prompt and no grub menu which is a minor inconvenience but makes it impossible to reboot remotely if I am vnc'd into the machine. Any idea why I don't get the grub menu unless I use the bios popup first?

---

### Post by TheFu on 2018-07-03
HP doesn't follow the standard for EFI booting.  You'll need to copy and rename a few files under /boot/EFI/ ... somewhere.  Look for what HP demands.

I had this issue with a Toshiba Chromebook. Here are my files:
```
/boot/efi/EFI# find .
.
./ubuntu
./ubuntu/fw
./ubuntu/fwupx64.efi
./ubuntu/grubx64.efi
./ubuntu/grub.cfg
./ubuntu/shimx64.efi
./ubuntu/mmx64.efi
./BOOT
./BOOT/BOOTX64.efi
```
Sorry, I don't remember which file was copied where, but I'd guess this was it:
```
/boot/efi/EFI# ll BOOT/BOOTX64.efi 
-rwx------ 1 root root 1134456 Mar  3 19:33 BOOT/BOOTX64.efi*
```
That date seems to be about the right date when I fixed the issue.

I would guess that ./ubuntu/grubx64.efi is the copied file into ./BOOT/BOOTX64.efi - but that is just a guess.

You'll want to find HP-specific instructions.  "Ubuntu UEFI HP" is the google search I'd use.

---

### Post by oldfred on 2018-07-03
If you run Boot-Repair, it automatically copies shimx64.efi to /EFI/Boot/bootx64.efi. 
You really only need shimx64.efi, if Secure boot is on. Shimx64.efi & grubx64.efi both work if UEFI Secure boot is off.

The /EFI/Boot/bootx64.efi is a fallback or hard drive boot entry. That also is the entry UEFI requires for all external drives.
Most HP violate UEFI spec and boot by description and of course only valid description is "Windows Boot Manager". Some with newer HP, have been able to set UEFI boot order from inside HP's UEFI, but use of efibootmgr to set boot order (which is used by installer), does not work.

Lots of details in link in my signature.
Similar info:
       Copy shimx64.efi to /EFI/Boot/bootx64.efi
[http://ubuntuforums.org/showthread.php?t=2247186](http://ubuntuforums.org/showthread.php?t=2247186)
Boot-Repair should automatically do copy file with 'use standard EFI file':
[http://askubuntu.com/questions/150174/sony-vaio-with-insyde-h2o-efi-bios-will-not-boot-into-grub-efi](http://askubuntu.com/questions/150174/sony-vaio-with-insyde-h2o-efi-bios-will-not-boot-into-grub-efi)
Sony, HP & others workarounds:
[http://askubuntu.com/questions/486752/dual-boot-win-8-ubuntu-loads-only-win/486789#486789](http://askubuntu.com/questions/486752/dual-boot-win-8-ubuntu-loads-only-win/486789#486789)

Before Boot-Repair copied files, users manually copied them.
       
 HP ProBook 450 G1 Custom UEFI boot or copy to bootx64.efi, delay of a so called "Express Multiboot menu"
[http://forums.linuxmint.com/viewtopic.php?f=46&t=164076](http://forums.linuxmint.com/viewtopic.php?f=46&t=164076)
HP Probook 4545s Secure boot off, manually copy files.
[http://ubuntuforums.org/showthread.php?t=2133796](http://ubuntuforums.org/showthread.php?t=2133796)
HP Manually renamed files to make it work.
[http://ubuntuforums.org/showthread.php?t=2131886](http://ubuntuforums.org/showthread.php?t=2131886)

---

### Post by kazakore on 2018-07-03
Check if there is a Custom Boot option in your BIOS (UEFI.) Set this to the boot path, IIRC I had to set mine to EFI/ubuntu/grubx64.efi but I may be wrong....You should be able to find out by selecting Boot Options when you power on the machine and checking against the path you follow there to correctly boot via EFI.

---

### Post by bart-burroughs-cox on 2018-07-03
Thanks for all of the replies, I need to leave secure boot off so VMWare player will install but I will give the suggestions a try. thanks much.

installed via ppa and ran boot-repair but get this message:
GPT detected. Please create a BIOS-Boot partition (>1MB, unformatted filesystem, bios_grub flag). This can be performed via tools such as Gparted. Then try again.
Alternatively, you can retry after activating the [Separate /boot/efi partition:] option.

here is the pastebin address:
Please write on a paper the following URL:
[http://paste.ubuntu.com/p/k6pmTzrQfY/](http://paste.ubuntu.com/p/k6pmTzrQfY/)




If you are experiencing boot issues, indicate this URL to people who help you. For example on forums

---

### Post by TheFu on 2018-07-03
/boot/efi must be FAT32.
/boot/ should be ext2/3

---

### Post by oldfred on 2018-07-03
You either need FAT32 for ESP - efi system partition for UEFI boot.
Or a bios_grub partition which is 1 or 2MB unformatted with bios_grub flag to have grub install in BIOS boot mode.

Note that Windows only boots from MBR with BIOS and only from gpt with UEFI.
Generally best to have all systems installed in same boot mode, but not required.
And if UEFI secure boot mode is on, you cannot install proprietary drivers or boot any system in BIOS mode.
You show BIOS boot loaders in MBR of several of your drives.

Script does not show all the details on NVMe drives.
Is this your ESP?
/dev/nvme0n1p2   48DC-6D85

---

