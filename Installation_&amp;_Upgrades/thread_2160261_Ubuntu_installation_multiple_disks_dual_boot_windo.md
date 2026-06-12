---
title: "Ubuntu installation multiple disks dual boot windows 8"
date: 2013-07-06
forum: Installation &amp; Upgrades
---

### Post by m1dnight on 2013-07-06
Hello there,

I've been trying to install ubuntu on my system for a week now and I think it's time to call in some help :)

My setup:

Asus P8-Z68 with an Intel I5 2500K
Hdd's: 
1 60GB OCZ (/dev/sda) (for windows) 
1 320 GB hdd (/dev/sdb)(for ubuntu) and 
1 500 gb hdd (for data).
nvidia GF 8800GTS

So I've made a bootable usb-stick with ubuntu 13.04 on it. 

I boot from the usb stick in uefi mode. When I install and I select "something else" I create a new partition table on the 320 gb hdd (/dev/sdb). I then make a partition of 4 gb for swap, and the rest is formatted in ext4 as a primary partition with mountpoint /. (I optionally tried to create a bios_boot partition of 1 mb but that didn't work either).

The installation always goes well. From a previous article I read, I used easybcd to create a bootentry for Ubuntu on my windows pc. So there is an option for Ubuntu when I boot my pc.

When i select this option i always enter grub command line"grub4dos". I think this should be the grub2 menu where i select ubuntu?

So i tried a lot of things to fix this but nohting works.

I tried booting into the live version and then running boot-repair. This says "found GPT table" and that it can't work with that. So that won't help either.

Today, I figured I'd give it another shot but now my live usb freezes when I boot into it. I'm figuring this has something to do with the nvidia card I have..

So I'm really really stuck here at this point. 

When I boot into the live CD it loads the unity interface (except the taskbar) and then freezes.

Could somebody help me out here? Thanks!

Edit:
My live usb check came out clean, containing no errors.

--> I tried creating a grub2 boot entry for sdb1 (bios_boot) and sdb3 (the ubuntu partition) but neither worked for booting, still entering grub4dos.

---

### Post by fantab on 2013-07-06
So, Windows is already installed on /dev/sda, which is 60GB OCZ SSD, right?
What mode is Windows installed in? UEFI or BIOS?
If it was installed in UEFI mode with a separate EFI partition then, it will be better if you also install Ubuntu in UEFI mode. Its not a good idea to boot one OS in UEFI and another in BIOS mode.
To boot in UEFI the HDD/SSD must use GUID Partition Table [GPT].
To install Ubuntu in UEFI mode you need to boot and install Ubuntu in UEFI mode. [If you see a Black Screen with options then you've booted in UEFI mode, if not its legacy/BIOS mode].

To Boot in UEFI mode you will need a 200-300 MB EFI Partition formatted with FAT32. If you have multiple HDDs then, its a good idea to have an EFI Partition on the HDD with Ubuntu install as well. OR you can use the EFI Partition on Windows HDD.

For more info on Installing with UEFI: [http://ubuntuforums.org/showthread.php?t=2147295](http://ubuntuforums.org/showthread.php?t=2147295)

If you can boot with Ubuntu LiveDVD/USB, then from TERMINAL [Ctrl+Alt+T] run the following:
```
sudo parted -l
```
.... and post the output here. That should give us a fair idea of your HDDs and partitions.

If you supect a Graphics issue with NVIDIA then use 'nomodeset' option during boot. 'Nomodeset' option is temporary, meaning you have use it everytime you boot Ubuntu, until you install required drivers. (However I don't think its a Graphic issue in your case).
For more details about 'NOMODESET': [http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)

---

### Post by m1dnight on 2013-07-06
Hello there,

I found out about the EFI partition just now and I tried installing using that. It actually worked! (I had indeed the black screen).One thing I messed up now is that I selected "install boot manager" to install on my OCZ drive by accident. (the windows drive that is)

Now when I boot my computer it shows GRUB2 with the options for 

> Ubuntu
Advanced options for ubuntu
Windows 8 (loader) /dev/sda1
Windows 8 (loader) /dev/sda2.

But I suspect that windows 8 is not installed in EFI mode, since I get this error for both Windows entries:

> 
error: can't find command 'drivemap'.
error: invalid EFI file path


Boot-repair once again complains about a GPT so I didn't try anything. Just to not make things worse. 

The output for "sudo parted -l": [http://pastebin.com/LGGzxdQA](http://pastebin.com/LGGzxdQA) (pastebin, for readability)

So as you said, I now have an msdos partition table for windows, and a GPT for Ubuntu. Damnit.

For the NVIDIA part: I had the same problem when I booted in my fresh Ubuntu install, but these commands fixed the freezing interface:

> sudo add-apt-repository ppa:ubuntu-x-swat/x-updates
sudo apt-get update
sudo apt-get install nvidia-current



Edit:

Okay, I don't know what is going on (obviously) but this is the status:

I have the following boot options when I open the boot menu from bios:

- Windows Boot Manager (P3: WDC WD3200KS-00PFB0) (ie the 320 gb hdd)
- ubuntu (P3: WDC WD3200KS-00PFB0) (ie the 320 gb hdd)
- ubuntu (P3: WDC WD3200KS-00PFB0) (ie the 320 gb hdd)
- P4: WDC WD500AAKS-00TMA0
- P1: OCZ-VERTEX3
- P3: WDC WD3200KS-00PFB0

The first one, second one and third one go to the GRUB where I can select "Ubuntu" or 2 Windows entries, but neither work.
The fourth one fails but we can disregard this one as this is a data disk, with seemingly some remains of a boot partition.
The fifth one (OCZ) boots to the Windows Boot Manager, where I can select only windows 8, and then get into Windows.
The sixth one boots to "BOOTMGR is missing, press ctrl+alt+delete" to continue

---

### Post by m1dnight on 2013-07-08
I fixed my problem.

I created an msdos partition table using Gparted in the live instance of Ubuntu. I set the bootloader on the 60 GB hdd.

Next I just created a swap partition and a defualt partition mounted at / for ubuntu. I installed and then I ran Boot-Repair in the live instance. I selected automatic repair and it installed GRUB2 properly on my OCZ drive where I can now select Windows and Ubuntu.

---

### Post by fantab on 2013-07-08
I am glad that you fixed your problem.

Isn't OCZ where you have Windows? By installing Grub (Bootloader) there you have corrupted Windows boot. Nothing to worry about, you are good for now. But in case you decide to remove Ubuntu in future then your Windows will not boot until you've fixed your MBR.

An alternative would have been to install GRUB on the HDD where you installed your Ubuntu. Then from BIOS/UEFI you could have changed HDD boot priority to boot your Ubuntu-HDD first. By doing this your Ubuntu HDD with Grub will boot first/automatically and Grub will boot both Ubuntu and Windows. While the boot-loader on OCZ, this windows partition will be safe. If we remove Ubuntu then just changing the HDD boot order in BIOS will boot Windows.

You can use the above tip in future.

Good Luck...

---

