---
title: "wont boot after Install"
date: 2016-02-02
forum: Installation &amp; Upgrades
---

### Post by Johnathan_Simpson on 2016-02-02
System Specs
Amd 4350 O
8gb Ram 
R9 290 windforce
990fxaud5t

This is the install steps I take
[INDENT]Downloaded the 15.10 64bit from the Ubuntu website for desktop
Used unetbootin, rufus, and universal usb installer to make a bootable usb(4gb formatted to Fat32)
Booted into UEFI boot menu by pressing F12
Select UEFI Cruze Glide
Select Try Ubuntu
Everything works including Bluetooth and Ethernet
Open the installer
Select English
Select to install both options about flash and 3rd party products
Select Something else
These are my drives[/INDENT]
[INDENT=2]Sda is windows 10
Sdb is a storage drive used in windows 10
Sdc tartget for install of Ubuntu[/INDENT]
[INDENT]So I select Sdc and select new partition
Select free space and add partition as primary / 71834mb[/INDENT]
[INDENT=2]Makes partition[/INDENT]
[INDENT]Select free space again and add partition primary swaparea 8192mb[/INDENT]
[INDENT=2]Makes partition[/INDENT]
[INDENT]Select to install bootloader to Sdc
Select partition / 
Select Install[/INDENT]

Everything goes right like it should. but when everything is done I try and boot via grub normally, nomodeset, or different kernel and I get an error bus9-4 descriptor error and I cant get past it. if I hit ctrl+alt+F1 I can get terminal. I had other trouble with another issue but that seems to be fixed now cause I can actually install it. Any thoughts? Maybe i'm doing something wrong?

---

### Post by yancek on 2016-02-02
> Select to install bootloader to Sdc

I don't think that would work as that would mean installing Grub boot code to the MBR which you don't do with an EFI install.  Rather, you install the Grub files to the EFI partition.  I'm not sure if you would create a separate EFI partition on sdc with Ubuntu or put it on the windows EFI partition.  Actually, you never say whether windows 10 is EFI.  Is it?  You might get the boot repair script and run it to post more info here while you are waiting for someone with more knowledge about UEFI.

  [https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

### Post by Johnathan_Simpson on 2016-02-02
Windows 10 is UEFI. I'll get that script this evening.

Little more info here in case it matters:
I'm trying not to mess with the windows EFI partition so I would select Ubuntu via boot menu instead of windows via grub. Most guides for install don't even mention the installing bootloader on a partition other then sda cause they use the same drive as windows anyways by resizing hdd for a Ubuntu partition. I've left it as Sda and all it did was mess something up to where windows wouldn't boot from grub. Had to boot windows boot manager via boot menu. I've also tried unplugging my other hdd and letting the installer install it to that drive it makes a / partition, E?? something partition(its 3 letters), and a SwapArea partition but that doesn't work either. What is the E?? partition? is that the EFI boot partition?

---

### Post by yancek on 2016-02-02
If windows 10 is UEFI, then you must also install Ubuntu UEFI.  If you don't then either Ubuntu or windows will not boot or maybe neither will boot.
You need to either install to an already existing EFI partition which you would have on sda for windows or create an EFI partition on sdc on which to install the Grub efi files.  I'm not sure where you are seeing an "E" partition.  That's a windows naming convention.  Linux names drives sda, sdb, sdc relating to the first, second and third hard drives with the numbers after referring to the partition.

I don't use EFI but my understanding is that you should have an option to select to use EFI when installing.  If you removed or unplugged the windows drive, you should be able to install Ubuntu EFI.  The link below has some info on dual booting Ubuntu and windows using UEFI.

 [https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

---

### Post by Vladlenin5000 on 2016-02-02
The E?? is probably ESP (**E**FI **S**ystem **P**artition) as it is usually named by several disk utilities...

---

### Post by Johnathan_Simpson on 2016-02-02
@yancek they are both installed via UEFI

@Vladlenin5000 Yes that's the one. So should I create a partition on Sdc for ESP and point the bootloader installation to the ESP partition? And if so what size is needed?

---

### Post by Johnathan_Simpson on 2016-02-03
ok I tried a few things and I finally sourced the problem. SSD that windows is installed on... it not being able to be accessed via try Ubuntu was oblivious to me till I tried to acess it last night and it saying that it cant load that dbus device. so I unplugged both ssd(windows Drive) and slave drive which left the target drive for the Ubuntu install. installed it and I get a different issue now. I don't get to where Ubuntu with the dots instead it does some wording on the top /dev/sda clean XXXXXXX/XXXXXXX ..... and I get this weither normal or nomodeset.

Edit: fsck /dev/sda clean xxxx/xxxx

---

### Post by Johnathan_Simpson on 2016-02-04
Ok got it solved. Found out that if you uncheck the hibernation the files that it uses are still there and ubuntu acts weird about it. also found out that the hdd that i was using was junk. it would format and install but wouldnt boot. i tried installing windows too it and i got a bunch of errors. so i guess due to the failed hdd and finding out about the hibernation thing its solved. partitioned sda(SSD) with a 20gb mounted to / and sdb with 50gb mounted to /home. rebooted just fine. no issues at all. thanks for the help but it looks like I was the error lol.

---

