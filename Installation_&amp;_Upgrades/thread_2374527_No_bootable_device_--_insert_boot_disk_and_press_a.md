---
title: "No bootable device -- insert boot disk and press any key"
date: 2017-10-16
forum: Installation &amp; Upgrades
---

### Post by adamtocher on 2017-10-16
Hi there. Ivery recently installed ubuntu on my gigabyte t1125n laptop. I did a full format of the windows 8 beta that was still on there fromantic agges ago and installed ubuntu after installing I got this message "No bootable device -- insert boot disk and press any key" I reinstalled it again figuring something went wrong none such luck. I've tried a range of different things that were suggested on the this forum. revolving around the grub and boot repair using the tey without installing feature to acsess the terminal with no such luck...the hard drive appears in the bios and when you go to reinstall Ubuntu it sees the current intsall but won't run it...I have had ubuntu work on this machine in the past. here are the links to the two logs from the two times I ran boot repair
[http://paste.ubuntu.com/25734751/](http://paste.ubuntu.com/25734751/)
[http://paste.ubuntu.com/25734770](http://paste.ubuntu.com/25734770)
I would really appreciate some help figuring this out thanks in advanced

---

### Post by ubfan1 on 2017-10-17
Maybe try plugging in the disk so it is sda instead of sdb.  Do you even have sdb in the boot order?  What happens if you use the EFI menu (some function key at power-up) to select device or OS to boot -- can you select the sdb disk?  can you then select the ubuntu menu item?

---

### Post by adamtocher on 2017-10-17
> **ubfan1 said:**
> Maybe try plugging in the disk so it is sda instead of sdb.  Do you even have sdb in the boot order?  What happens if you use the EFI menu (some function key at power-up) to select device or OS to boot -- can you select the sdb disk?  can you then select the ubuntu menu item?

im not sure how to accsess the efi menu i can select boot order enter recovery(cant do that as i dont have the partition any more) or enter the bios on boot from pressing f keys. im not sure what sdb or sda means....im using an external dvd drive that came with the laptop to do the install and im sure the dvd and drive were plugged in when i ran the boot-repair as i was running in the try ubuntu mode running off the disk. how exactly would i plug "the disk" in so it is sda instead of sdb? and which disk? you mean the hard drive? as for the boot order all it gives is the options for is the hdd the dvd drive (when its pluged in) usb and the exernal sata port nothing about selecting sections of the hard drive which i have never seen on any computer. please elaborate further and if you could explain a bit of how to read the boot-repair log? thanks again

edit. also the options in the bios are very limited. you cant really change much in there at all other than the boot order and which things like bluetooth are turned on on start up

---

### Post by oldfred on 2017-10-17
You also show UEFI Secure Boot may be on, often better to have that off.

Drives are like sda for first drive, sdb for second drive etc.
Then partitions are numbers like sdb1 is first partition on second drive.

Normally UEFI sets drive order and that is by SATA port used on the motherboard. If laptop it may just have been randomly plugged into one of the two ports and they used second not first like they should have.

Does f10 or f12 show a choice of things to boot, the UEFI boot menu. Some systems use other keys, check manual.
Boot-Repair report shows an ubuntu entry has been added.

You should see these in  UEFI boot menu (just the name part):
efibootmgr -v
BootCurrent: 0002
BootOrder: 0000
Boot0000* ubuntu    HD(1,GPT,2242c5eb-15c8-4b9a-9c77-2dd2ba198ef3,0x800,0x100000)/File(EFIubuntushimx64.efi)
Boot0001* TOSHIBA MK3265GSX                           BBS(HD,,0x500)................-...........A..........................................

It looks like your laptop is a very early UEFI. Does vendor have UEFI update as vendor (as well as Windows & Ubuntu) often needed updates to work with the new UEFI over the old BIOS.

---

### Post by adamtocher on 2017-10-17
> **oldfred said:**
> You also show UEFI Secure Boot may be on, often better to have that off.

Drives are like sda for first drive, sdb for second drive etc.
Then partitions are numbers like sdb1 is first partition on second drive.

Normally UEFI sets drive order and that is by SATA port used on the motherboard. If laptop it may just have been randomly plugged into one of the two ports and they used second not first like they should have.

Does f10 or f12 show a choice of things to boot, the UEFI boot menu. Some systems use other keys, check manual.
Boot-Repair report shows an ubuntu entry has been added.

You should see these in  UEFI boot menu (just the name part):
efibootmgr -v
BootCurrent: 0002
BootOrder: 0000
Boot0000* ubuntu    HD(1,GPT,2242c5eb-15c8-4b9a-9c77-2dd2ba198ef3,0x800,0x100000)/File(EFIubuntushimx64.efi)
Boot0001* TOSHIBA MK3265GSX                           BBS(HD,,0x500)................-...........A..........................................

It looks like your laptop is a very early UEFI. Does vendor have UEFI update as vendor (as well as Windows & Ubuntu) often needed updates to work with the new UEFI over the old BIOS.

thanks fred
so i have setup utility on f2 system recovery on f9(but that partition is gone) and boot manager on f12 nothing on f10....so uefi replaces the old bios? i have no options like that in the f2 set up utility though and that jut looks like bios and i think even is just a bios as im on the latest bios version that gigabyte offer for the laptop from their site. im not sure why the hard drive shows up as sdb instead of sda either. 
there is also no mention of uefi in the manual 
[http://www.gigabyte.us/Laptop/T1125N#support-dl](http://www.gigabyte.us/Laptop/T1125N#support-dl) 
this is a link to the download page for the laptop

---

### Post by ubfan1 on 2017-10-17
Odd hardware setup. I see   usb-Generic-_Multi-Card_20090516388200000-0:0 -> ../../sda which looks like the SD card reader for sda.  I looks like secure boot was on for the installation.  That should be OK, and that setup should also boot with secure boot off, but check the EFI partition (gets mounted at /boot/efi ? when running the live media).  Look at the file sizes for .../EFI/Boot/bootx64.efi and .../EFI/ubuntu/shimx64.efi and .../EFI/ubuntu/grubx64.efi.  If the size matches grubx64.efi, then secure boot must be off to boot.  If the size matches the shimnx64.efi, then secure boot may be either way, but you MUST also have /EFI/Boot/grubx64.efi present.   The /EFI/Boot holds the default bootloaders for the device, so regardless of what nvram boot entries are in the efibootmgr list, the device should boot (getting to grub).   

EFI menus are pretty hardware specific, but some will have a two layer selection, first the device, then the OSes on that device.  Others just list all the choices on all devices.   If your /EFI/Boot is setup like the above, the device selection should boot (grub).  The grub boot kernels are the signed ones, so should boot regardless of whether secure boot is enabled or not.
Maybe the absence of an sda disk made no difference, since it looks like the bootloaders did get loaded into the EFI partition on sdb.  Laptops sometimes have a second slot for disks, but that's not common  except in the large ones.  More common is the ability to remove a DVD and replace it with a disk caddy for a second disk.  Your esata port makes adding an external disk easy, and will have much better performance than an added external USB disk.

---

### Post by oldfred on 2017-10-17
UEFI is the new replacement for BIOS. And has been with PC for about 5 years.
Microsoft required all vendors to use UEFI/gpt with all computers with Windows 8 pre-installed.
       Windows 8 release date: October 26, 2012. 
A few Windows 7 systems were installed in UEFI mode, I think vendors were just starting to test their UEFI.

Many vendors then (and some still now) call UEFI as BIOS since they think that is all users know.
And UEFI has a mode to boot in the now 35 year old BIOS/MBR configuration for backwards compatibility.

 CSM - UEFI Compatibility Support Module (CSM), which emulates a BIOS mode  

If called BIOS, just make sure you have the latest version.

---

### Post by adamtocher on 2017-10-18
managed to solve it by trying to install windows 7 which errored half way through due to the disk being scratched to hell but then when i went back to install ubuntu i selected not to us uefi mode when it prompted me then formatted off the failed windows install. its all working good now

---

