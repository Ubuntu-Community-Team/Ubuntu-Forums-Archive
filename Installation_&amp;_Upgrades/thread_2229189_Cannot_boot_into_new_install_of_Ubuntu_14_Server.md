---
title: "Cannot boot into new install of Ubuntu 14 Server"
date: 2014-06-11
forum: Installation &amp; Upgrades
---

### Post by rob67 on 2014-06-11
[FONT=arial][COLOR=#333333]Seems like a fair few people have had similar problems, but I've tried all the suggestions in other threads to no avail.
[/COLOR]
[COLOR=#333333]I have installed Ubuntu 14.04 on a HP ProLiant ML310e Server via burning ISO of the Ubuntu Server and following the process.
[/COLOR]
[COLOR=#333333]I have 2 HDDs which I want to set up as RAID 1, and during the Ubunutu Server install, it gave me the option to set this up as it installed, so I did.[/COLOR]
[COLOR=#333333]Install processed fine, with no reported errors.
[/COLOR]
[COLOR=#333333]Upon rebooting, the system does not even attempt to boot from HDD, and just from CDROM and NIC, both of which obviously fail.
[/COLOR]
[COLOR=#333333]I then booted into Live CD and ran Boot Repair which gave me a heap of commands to run in Terminal and eventually game me this report: [http://paste.ubuntu.com/7630512/](http://paste.ubuntu.com/7630512/)
[/COLOR]
[COLOR=#333333]Then in the DISK Utility it shows my two physical drives each partitioned as "master boot record" "Linux Raid auto (bootable) and Linux Raid Member (dev/sda1 and dev/sdb1)
[/COLOR]
[COLOR=#333333]One drive (sda) has partition 1 (main, linux raid member), plus extended partition 2, plus swap partition 5 plus free space 1.1MB
[/COLOR]
[COLOR=#333333]Second drive (sdb) has just partition 1 (main linux raid member) plus free space 1.1MB
[/COLOR]
[COLOR=#333333]Disk Utility also shows the RAID Array, /dev/md/0, contents ext4 mounted at /mnt/boot-sav/md0
[/COLOR]
[/FONT][COLOR=#333333][FONT=UbuntuRegular][FONT=arial]Here are some screenshots: 
[/FONT]
[IMG]http://i.imgur.com/UgSP6Wb.png[/IMG]
[IMG]http://i.imgur.com/ZtmGXAP.png[/IMG][IMG]http://i.imgur.com/uaEM3Mo.png[/IMG]

[/FONT][/COLOR]
[FONT=arial][COLOR=#333333]And still, upon restart, it just won't boot - just goes straight to CDROM and NIC.
[/COLOR]
[COLOR=#333333]The BIOS boot order has Hard Drive C: (See Boot Controller Order) as #1 And Boot Controller Order just has one option, which is PCI Embedeed HP Dynamic Smart Array B120i Controller.[/COLOR]
[COLOR=#333333]Wonder if this is anything to do with it, as I'm not using the HP's own Raid software (tried that, also didn't work).
[/COLOR]
[COLOR=#333333]If I use the boot override to force it to boot from HDD, it doesn't even look like it tries and goes straight to attempting to book from CD-ROM
[/COLOR]
[COLOR=#333333]Any advice, most appreciated. Have been trying / reinstalling / trying for days now!
[/COLOR]
[COLOR=#333333]Thanks[/COLOR][/FONT]
[COLOR=#333333][FONT=UbuntuRegular]
[/FONT][/COLOR]

---

### Post by oldfred on 2014-06-11
Please attach screen shots not post in line. Not everyone has high speed Internet and it locks up their system.
You can easily attach with Go Advanced editor and the paperclip icon.

I do not know RAID, but normally you install grub to the root of the RAID not the normal MBR of the drive.

Boot-Repair says it did this to both sda & sdb
 Reinstall the GRUB of md0 into the MBR of sda

I know with BIOS RAID, it installs this way, you mount the partition p1 and install to the root or beginning of the RAID:

 sudo mount /dev/mapper/isw_cdjacjeebj_VOLUME_0[COLOR=#ff0000]p1[/COLOR] /mnt
sudo grub-install --root-directory=/mnt /dev/mapper/isw_cdjacjeebj_VOLUME_0

Are drives connected to the RAID controller or directly to motherboard ports?

Not sure if your hardware is part of the issue or not.

---

### Post by rob67 on 2014-06-11
Hi,

Thanks for the reply.

Have solved this now, after talking to HP Support.

Was actually, as you suggested, a Hardware (well BIOS) setting issue. The BIOS was set to only show the HP Smart Array Controller, so the system could not see the SATA HDDs on boot at all (I am not using the HP Smart Array Controller).

Had to switch up the SATA settings in BIOS from using Smart Array to using SATA AHCI Support.

Now it all works!

Thanks anyway

---

