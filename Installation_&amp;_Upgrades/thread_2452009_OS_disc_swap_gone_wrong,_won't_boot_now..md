---
title: "OS disc swap gone wrong, won't boot now."
date: 2020-10-14
forum: Installation &amp; Upgrades
---

### Post by Steve Goodey on 2020-10-14
[https://paste.ubuntu.com/p/cQ6Jz886X7/]("https://paste.ubuntu.com/p/cQ6Jz886X7/")
 
Hello,
 
I wonder if someone can help me dig myself out of a hole I've created.
 
I had a mythbuntu 16.04 system working OS on /dev/sda2 with recordings on /dev/sdb1.
 
I wanted to swap the /dev/sda with a blank ssd and install xubuntu 20.04. The install went OK but then I put the old OS disk back and tried to boot from that. But I get an error message:-
 
Failed to open \EFI\BOOT\grub64.efi - Not Found
 
I would really appreciate it if you could help me get this original mythbuntu OS back up and booting, thanks.

-- 
Regards, Steve Goodey

---

### Post by oldfred on 2020-10-14
When you remove a drive, UEFI usually forgets the UEFI boot entry.

You show this in line 56:
> Boot0000* ubuntu	VenHw(99e275e7-75a0-4b37-a2e6-c5385e6c00cb)

that is not a typically UEFI boot entry.
And default entry is 001A which looks like a BIOS boot (BBS) of a CDROM drive.

Did you run the Boot-Repair reinstall of grub-efi-amd64  in UEFI boot mode?

---

### Post by Steve Goodey on 2020-10-15
oldfred ,

Thanks for your help. Things have now progressed and on boot I am presented with the grub menu.

This is what I am now getting:-

grub> set pager=1
grub> ls
(hd0) (hd1) (hd1,gpt3) (hd1,gpt2) (hd1,gpt1) (hd2) (hd2,msdos1) (hd3) error:
failure reading sector 0xfc from 'hd3'.
error: failure reading sector 0xe0 from 'hd3'.
error: failure reading sector 0x0 from 'hd3'.

grub> ls (hd0,1)/
error:invalid sector size 65535.
grub> ls (hd1,1)/
efi/
grub> ls (hd2,1)
,/ ../ lost+found/ banners/ bare-client/ coverart/ fanart/ livetv/ recordings/ screenshots/ streaming/ trailers/ videos/ db_backups/
grub> _

Am I right in thinking that the error about the invalid sector size on (hd0,1) is my problem?

Thanks for any help/pointers.

Steve.

---

### Post by oldfred on 2020-10-15
Is hd3, your live installer?
That often throws lots of errors as it is a hybrid DVD/flash drive image that does not use a standard partition table.
You can ignore any errors from live installer. And if it does not work, just recreate it.

---

### Post by Steve Goodey on 2020-10-21
Thanks for this [QUOTE=]For more info on UEFI boot install & repair - Regularly Updated :
[http://ubuntuforums.org/showthread.php?t=2147295](http://ubuntuforums.org/showthread.php?t=2147295)[/QUOTE]
Reading through that led me to rEFInd which I was able to use to get the system to boot.

Regards Steve.

---

