---
title: "Ubuntu 14.04 won't boot except with live USB"
date: 2015-01-10
forum: Installation &amp; Upgrades
---

### Post by lorecupe on 2015-01-10
Hello. I have recently bought a Toshiba Satellite NB10-A-102 laptop with Windows 8 preinstalled. I didn't want it so I have used a USB stick to install Ubuntu 14.04 64bit through Unetbootin. Installation apparently went well but, when I try to boot the laptop without the stick inserted, it won't boot. Instead it says "no media found please insert boot media" something like that. I've tried several methods found searching through the internet, but so far none worked. 
Many suggest the use of boot-repair, and I've used it, with no success. This is the link of the output: [http://paste.ubuntu.com/9704264/](http://paste.ubuntu.com/9704264/)
Actually, when I try to reinstall Ubuntu, it boots without the stick for 1 time only. If I reboot it will say the "no media found" thing. I've secureboot off and uefi mode on.
Another issue that I don't know if is related to this main problem is that, almost half of the times, when I choose "try ubuntu without installing" with the stick inserted, it gives me a SQUASHFS error. I've briefly searched for this and it seems related to a problem with the stick or the usb slot, but I think this can't be the case, cause both laptop and stick are brand new.
Hope someone can help me with this. Thank you.

---

### Post by sudodus on 2015-01-10
You have removed Windows, and if I understand correctly, that was also your intention.

Then it will be easier to install Ubuntu without UEFI, to boot the computer in BIOS alias CSM mode. I suggest that you try to switch to CSM mode. With a GUID partition table, GPT, you will need a small (1 MB) partition with no file system and the flag bios_grub. See this link

[https://help.ubuntu.com/community/DiskSpace](https://help.ubuntu.com/community/DiskSpace)

Don't make a very complicated partition table. With the old style MSDOS partition table, you can let Ubuntu do it automatically, and it will install one big root partition and one small swap partition. In addition to that you might want a data partition or a home partition. Avoid other system partitions!

With GPT, you need also the minimal bios_grub partition described earlier.

-o-

Create a (new) partition table or edit partitions with ***gparted*** when booted from the Ubuntu install DVD/USB drive.

-o-

I have a Toshiba laptop bought in April 2013, and it is fairly easy to install Ubuntu in both UEFI and CSM mode, and to switch in the setup menus (pressing F12 during boot). But I have read that new models of Toshiba 'do not want to boot anything but Windows'. This is described in the following tutorial.
[URL="http://ubuntuforums.org/showthread.php?t=2147295"]
UEFI Installing - Tips[/URL]

If not possible to switch to BIOS alias CSM mode, maybe you can use the trick to rename a file and 'make UEFI think it is booting Windows'.

-o-

The squashfs error is probably unrelated unless the install system is corrupted. Did you check with md5sum, that the download was good? See this link

[https://help.ubuntu.com/community/UbuntuHashes](https://help.ubuntu.com/community/UbuntuHashes)

***Edit***: I recommend the version 14.04.**1** LTS, which is more debugged and polished than the original 14.04 LTS. Unetbootin usually works. Are you running it in linux or Windows?

---

### Post by lorecupe on 2015-01-10
Thank you for your answer. I will immediately try what you suggest.
 It is possible to switch from uefi to csm in the bios menu. Regarding unetbootin, when I made the stick I was in linux, the live version I have on the stick is already 14.04.1 and the md5sum is correct.

---

### Post by sudodus on 2015-01-10
Squashfs is a huge compressed file that contains most of the packages of the installed system. After booting into a simple system squashfs is expanded and its packages are installed into RAM drive for a live system or into an internal drive when making an installed system. I don't know what kind of error is causing your problem. Errors that come and go are not nice. What happens when you

- shut down the computer completely,
- wait for at least 30 seconds,
- unplug the pendrive,
- wait for 5 seconds,
- replug the pendrive
- and boot again

(in contrast to rebooting, when the computer is not shut down, 'only' rebooted)?

-o-

You can also test the RAM with memtest from the boot menu - test overnight. One single error is too much.

---

### Post by lorecupe on 2015-01-10
Did what you suggested and now I can finally boot without the live usb. Thank you. Is there anything else I should do to keep this optimal situation?
For squashfs, I will memtest tonight.

---

### Post by sudodus on 2015-01-10
Yes, ***backup*** this working system to an external drive or an internet cloud service. Make regular backups. If you have an extra hard disk drive or SSD, test that the backup really works. Otherwise you don't really know.

Keep the system updated/upgraded (without upgrading to the next version, so keep it within 14.04.{1,2,3,4,5} LTS, but not 14.10).

***Install*** application programs from the repositories, avoid downloaded packages unless you know what you are doing. Use the Software Center, Synaptic or command line tools (apt-get). You may want ubuntu-restricted-extras for better multimedia experience.

Shutdown the computer softly, according to this link, if it should get unresponsive.

[https://en.wikipedia.org/wiki/Magic_SysRq_key](https://en.wikipedia.org/wiki/Magic_SysRq_key)

Avoid hard reboots or shutdowns.

---

