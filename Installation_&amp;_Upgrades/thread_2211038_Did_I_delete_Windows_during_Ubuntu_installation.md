---
title: "Did I delete Windows during Ubuntu installation?"
date: 2014-03-13
forum: Installation &amp; Upgrades
---

### Post by carpenter.katie.e on 2014-03-13
Hi all,

I am an absolute Ubuntu newbie, so please bear with me. I believe I accidentally deleted Windows from my computer. Here's what I did:

1. I had Ubuntu 12.04 and Windows 7 installed side by side.
2. I installed Ubuntu 13.10 onto a USB to boot and upgrade (because wireless didn't work in 12.04).
3. When I switched the boot order in BIOS, instead of just changing the order, I made the USB the first boot option and accidentally disabled the second option, which would have been my SSD.
4. I installed the Ubuntu upgrade using the USB.
5. When I started up my computer without the USB, I got the "error: file not found   grub rescue>" message.
6. I booted again from the USB, connected to the internet and ran Boot Repair PPA.
7. When I rebooted my computer without the USB, the only option in grub is Ubuntu, which works fine without the USB (hooray!), but I see no Windows 7.

When I run 

```
sudo fdisk -lu
```

here is what I get:

```
   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63   140101797    70050867+   7  HPFS/NTFS/exFAT
/dev/sda2       232187445   250067789     8940172+  1c  Hidden W95 FAT32 (LBA)
/dev/sda3       140103678   232185855    46041089    5  Extended
/dev/sda5       140103680   223997951    41947136   83  Linux
/dev/sda6       224000000   232185855     4092928   82  Linux swap / Solaris
```

Another thing: if I do need to reinstall Windows....I don't have a CD drive. Any other options?

Thanks so much for any help!

---

### Post by Bashing-om on 2014-03-13
carpenter.katie.e Hello ;

From that output, windows is still alive and well.

Try this:
boot up ubuntu to the desk top, key combo ctl+alt+t -> terminal:

Enter terminal commands:
```

sudo apt-get update
sudo apt-get upgrade
sudo update-grub

```
update to sync your data base with that of the mirror (package management system);
upgrade to insall the updated versions of all packages on your system
update-grub to activate os-prober and hunt up Windows and chainload the Window's boot loader to that of grub.

Reboot the system and see if Windows now appears in the grub boot menu.

[INDENT][INDENT]ain't nothing but a thing
[/INDENT][/INDENT]

---

### Post by carpenter.katie.e on 2014-03-13
That worked! What a relief. Thank you so much, Bashing-om.

---

### Post by Bashing-om on 2014-03-13
carpenter.katie.e; Great !

It is all in knowing how ( hey, I had great teachers !).

As this little episode is a success story and is now concluded, please mark this thread as solved: 1st post -> thread tools .

[INDENT]just keep on
[INDENT][INDENT]keep'n on
[/INDENT][/INDENT][/INDENT]

---

