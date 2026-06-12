---
title: "Windows 8 doesn't start anymore"
date: 2013-03-29
forum: Installation &amp; Upgrades
---

### Post by german640 on 2013-03-29
I'm trying to setup a dual boot of Kubuntu and Windows 8 in a new HP Envy m4.

Current BIOS settings: 
Legacy mode Disabled
Secure Boot Disabled

What did I do:
Enabling secure boot doesn't start the Ubuntu/Kubuntu LiveDVD, so I disabled Secure Boot, started Kubuntu (12.10) and installed it with the recommended partition option (it installed in EFI mode as far as I can tell).
Rebooted into Linux Secure Remix LiveDVD and ran Boot-Repair.
Rebooted and I'm presented with Grub with a bunch of options, Kubuntu starts fine. However, none of the Windows entries can boot Windows 8. Some of them start a Windows/HP "automatic system recovery" with some recovery options. None of them work. I even tried options like "Restore full system to factory defaults" or something like that but it fails saying a needed partition is missing. None of the options has affected Grub/Kubuntu, so it still starts fine. Other Windows entries in Grub try to start Windows, but it stays with a "loading" spinner forever.

If I enable Secure Boot, Grub doesn't even load and an error of "The system failed to authenticate itself" is shown, and the laptop shutdows itself.

I ran more than once Boot-Repair, but with the same effects.

Here is the Boot-Repair log:

[http://paste.ubuntu.com/5657210/](http://paste.ubuntu.com/5657210/)

---

### Post by oldfred on 2013-03-29
Use gparted and remove boot flag from sda4. In gpt partitioning only the efi partition has the boot flag. That is how gparted defines the efi partition.
In BIOS boot the Windows partition with boot files would have a boot flag, but in UEFI/GPT it cannot.

This entry is the one that should work to boot Windows. Try with secure boot on in UEFI.
>  
menuentry "Windows UEFI bkpbootmgfw.efi" {
search --fs-uuid --no-floppy --set=root 3C22-10F2
chainloader (${root})/EFI/Microsoft/Boot/bkpbootmgfw.efi
}



HP seems to put a lot of efi files into the efi partition and Boot repair finds them all. Once you get it booting you can backup and houseclean those you do not need. But someday you may need a repair or recovery entry. Not sure what all the other efi files do?

Grub2's os-prober does not yet work, so those two entries in 30_os_prober will not work. You can just turn os-prober off if you desire.
 grub2's os-prober creates wrong style (BIOS) chain boot entry
[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1024383](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1024383)
type of entry from Boot-Repair that should work.
'Windows UEFI loader'
Type of entry that does not work:
'Windows ...) (on /dev/sdXY)'

---

### Post by german640 on 2013-03-29
Sorry but the entry "Windows UEFI bkpbootmgfw.efi" tries to boot windows, but it hangs forever in the spinning icon.

In the end I used the HP recovery partition (which took a TON of time) which sort of reinstalled Windows, but it failed at the end leaving a more or less usable Windows 8 installation, with only the Administrator user. Of course it also nuked Kubuntu but it leaved Windows in its small partition and a big empty partition where Kubuntu was living. 

I reinstalled Kubuntu manually editing the partition table to make sure not to do any changes to Windows or HP partitions, rebooted, ran again Boot Repair and everything looks the same as before except for the fact that the entry corresponding to Windows is working now as far as I can tell.

Bottom line: I have the strong theory that resizing the windows partition (done by the Kubuntu installer) totally breaks Windows. I had the same experience some months ago after installing Ubuntu on a Toshiba without UEFI and with Windows 7, Windows hanged forever at startup and I had to reinstall it.

EDIT: Legacy Mode is disabled (so booting on UEFI), but Secure Mode is also disabled, enabling it doesn't start Grub at all.

---

### Post by oldfred on 2013-03-29
Glad you sorted it out. 

Some use the rename function with Boot-Repair to change the grub shim file to be the Windows boot loader. Then it may work with secure boot on. 

We normally suggest using Windows to resize Windows and to immediately reboot so it can run chkdsk and update to its new size. Then install Ubuntu into the unallocated space.

---

