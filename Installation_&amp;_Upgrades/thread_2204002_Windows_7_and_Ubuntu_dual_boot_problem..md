---
title: "Windows 7 and Ubuntu dual boot problem."
date: 2014-02-06
forum: Installation &amp; Upgrades
---

### Post by didier2 on 2014-02-06
Hi,

I've first installed W7 followed by Ubuntu 12.04. (2 different disks).
First disk as a 100MB efi partition on it and Windows, second disk has a linux swap and unbuntu.

Ubuntu works fine.

But when I try to get back in Windows using the grub menu, Windows starts loading but I get a 0xc0000225 error message.

Browsing the net, I came across this:  [http://askubuntu.com/questions/193144/dual-boot-uefi-windows-7-and-ubuntu-12-04-both-64-bits-w7-entry-doesnt-appea](http://askubuntu.com/questions/193144/dual-boot-uefi-windows-7-and-ubuntu-12-04-both-64-bits-w7-entry-doesnt-appea)

The problem is that when I try this command:  [FONT=Ubuntu Mono]grub-probe --target=fs_uuid /boot/efi/efi/Microsoft/Boot/bootmgfw.efi
I get an error message telling it didn't find the disk (or something similar, working from memory here), reverting to /dev/sda1 

What I found is that if I nuke the Ubuntu partition (using gparted from the boot disk ), I can get Windows started (using the boot menu on the PC after a bootrec /fixmbr ).

I tried boot-repair (but I do not have the logs in pastebin yet ... you guys need a challenge). Seriously, I'll try to add that tonight if needed.
I've tried a few things with Boot-repair, but no luck so far ...

Any ideas or pointers are welcome. I've been at it for a few nights now, I'm in too deep to re-install everything and run ubuntu in a VM.

Thanks for reading.


[/FONT]

---

### Post by Gregory_Hovagim on 2014-02-06
I had this terrible problem where I updated from v13.4 to 13.10 and it blew away my Windows partition. I have a Windows 7 disk at home which I'll try to use and repair the problem. Not sure it'll work though.

---

### Post by oldfred on 2014-02-06
Did you install Windows 7 in BIOS mode and Ubuntu in UEFI mode?

Best to see details:
       Post the link to the Create BootInfo report. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)


 Only 64 bit supported for UEFI boot
[http://www.sevenforums.com/tutorials/186875-uefi-unified-extensible-firmware-interface-install-windows-7-a.html](http://www.sevenforums.com/tutorials/186875-uefi-unified-extensible-firmware-interface-install-windows-7-a.html)
Prepare an usb thumb drive, to boot windows 7 in UEFI mode
[http://forums.lenovo.com/t5/tkb/articleprintpage/tkb-id/Beta_OS@tkb/article-id/177](http://forums.lenovo.com/t5/tkb/articleprintpage/tkb-id/Beta_OS@tkb/article-id/177)
[http://technet.microsoft.com/en-us/library/hh304353%28v=ws.10%29.aspx](http://technet.microsoft.com/en-us/library/hh304353%28v=ws.10%29.aspx)

---

### Post by didier2 on 2014-02-06
Hi,

Both OS were installed in EUFI mode. 

Here are the detail from boot-repair : [http://pastebin.ubuntu.com/6887169](http://pastebin.ubuntu.com/6887169)

I'll keep digging using the links you gave me in the mean time.

---

### Post by oldfred on 2014-02-06
You have both systems in UEFI mode, but Ubuntu is on a MBR(msdos) partitioned drive with efi boot files in the gpt partitioned drive.
Not sure if that works. Normally UEFI only works with gpt partitioned drives. Not seen anyone use MBR or a mix like you have.
Probably best to convert sdb to gpt.

       GPT fdisk Tutorial - user srs5694 in forums
[http://ubuntuforums.org/showthread.php?t=1439794](http://ubuntuforums.org/showthread.php?t=1439794)
[http://www.rodsbooks.com/gdisk/](http://www.rodsbooks.com/gdisk/)


 Converting to or from GPT
[http://www.rodsbooks.com/gdisk/mbr2gpt.html](http://www.rodsbooks.com/gdisk/mbr2gpt.html)
You then need to use gdisk to convert from gpt to MBR
[http://www.rodsbooks.com/gdisk/mbr2gpt.html#gpt2mbr](http://www.rodsbooks.com/gdisk/mbr2gpt.html#gpt2mbr)

I prefer to have an efi partition on every drive. Then you can have each system boot without the other drive, so when (not if) one drive fails you can still boot the other drive.

You do have BIOS boot entries in MBR of both drives, those should never be used, and you should always boot with UEFI, so system does not try to boot from them. They will not cause any issues unless you try to use them.

---

### Post by didier2 on 2014-02-06
Gosh you're quick :)

Yes that was the issue, converting the second disk to gpt got my Windows booting again.

It now make sense why I was able to get windows back up if I deleted all partitions on the 2nd disk.

Thanks a million for your help.
From what I've seen around, I'm not the first one you pulled out of the hole. Respect.

---

