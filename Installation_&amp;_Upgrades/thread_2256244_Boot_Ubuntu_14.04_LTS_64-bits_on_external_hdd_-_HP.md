---
title: "Boot Ubuntu 14.04 LTS 64-bits on external hdd - HP Envy 17 w/Windows 8.1"
date: 2014-12-10
forum: Installation &amp; Upgrades
---

### Post by Aurelio_Morales on 2014-12-10
Hello community,

Most people try to install Ubuntu along side Windows and sometimes you run into problems such as not having Windows boot or others, but I prefer to have a second disk with Ubuntu. 
I'm sharing my experience with a new HP Envy 17 Leap Motion laptop with Windows 8.1 pre-configured.

**1) Problem:**
Laptop  HP Envy 17 Leap motion with Windows 8.1 pre-configured, does not boot  Ubuntu 14.04 64-bits LTS on external USB hard disk (Seagate 1TB). Laptop  has UEFI and secure boot enabled.
To avoid problems with  Windows boot loader, I shutdown Windows 8.1 (fast startup is disabled,  hibernation was disabled by executing "powercfg.exe -h off", as recommended in
 [http://askubuntu.com/questions/221835/installing-ubuntu-on-a-pre-installed-windows-8-64-bit-system-uefi-supported](http://askubuntu.com/questions/221835/installing-ubuntu-on-a-pre-installed-windows-8-64-bit-system-uefi-supported) )  disconnected the battery, disconnected internal disk, 
connected the  battery, connected external USB disk, and booted Live DVD Ubuntu 14.04  64-bits LTS, and installed Ubuntu 14.04 LTS 64-bits w/o problems on  external disk. 
I shutdown Ubuntu after installation, boot up again and  shutdown several times with no problem.
The problem seems to arise when  I disconnect the external disk (laptop is shutdown, no battery or AC  connected), I connect internal disk, connect the battery, boot Windows  8.1, 
shutdown Windows 8.1 (fast startup and hibernation are disabled),  extract internal disk, connect again external disk and Ubuntu does not  boot any more. 
Laptop shows the following screen message:

Boot Device Not Found
Please Install an operating system on your hard disk
Hard disk (3F0)
F2 System Diagnostic
For more information, please visit: [www.hp.com/go/techcenter/startup]("http://www.hp.com/go/techcenter/startup")

F2 does not work for external disk, and the URL is for problems with internal disk and for Windows.

At this moment, I thought that Windows Boot loader made something on BIOS, so I tried step 2) but actually you don't need to do it unless you are sure your 
Ubuntu external disk is not bootable at all. 
I include step 2) anyways because It is what I did, but I don't think my Ubuntu was broken.

**2) Boot-Repair**
To  solve the problem in 1) I put the Live DVD Ubuntu 14.04 LTS and boot  again the DVD, while the external disk was connected (internal disk was  extracted), but this time 
I did "try Ubuntu" instead of install. After  the DVD ended up the boot process, I downloaded and installed  Boot-Repair. I launched Boot-Repair and selected the 
"Recommended  Repair" button, created the BootInfo link [http://paste.ubuntu.com/9435308/](http://paste.ubuntu.com/9435308/) , shutdown the laptop,  extracted the Live DVD Ubuntu, and power on 
again the laptop, and Ubuntu  was alive again, showing the grub menu. I shutdown several times the  laptop and always the external disk was able to boot Ubuntu. 

**3) Problem after using Boot-Repair's "Recommended Repair"**
To  test that the problem was solved by following step 2), I shutdown Ubuntu on external disk,  disconnected the external disk, disconnected the battery, installed  again the internal disk, installed the battery, boot Windows 8.1  (external disk was not connected), shutdown Windows 8.1 (fast startup is  disabled and hibernation is disabled),  disconnected battery,  disconnected internal disk, connected battery, connected external disk,  and Ubuntu does not boot again and the previous screen message appears  again (Boot device Not Found).

I checked that Ubuntu was running in EFI mode before shutting down and the disk has GPT partition table.
Here I show the output of "parted" on /dev/sda when Ubuntu was running:

amorales@hpenvy17:/sys/firmware$ sudo parted /dev/sda
[sudo] password for amorales: 
GNU Parted 2.3
Using /dev/sda
Welcome to GNU Parted! Type 'help' to view a list of commands.
(parted) print                                                            
Model: Seagate BUP Slim BL (scsi)
Disk /dev/sda: 1000GB
Sector size (logical/physical): 512B/512B
Partition Table: gpt

Number  Start   End     Size    File system     Name  Flags
 1      1049kB  538MB   537MB   fat32                 boot
 2      538MB   983GB   983GB   ext4
 3      983GB   1000GB  17,1GB  linux-swap(v1)

(parted) quit

So, actually sda1 is the EFI partition, FAT32, and with the boot flag, as recommended in many posts.

Here are the details of BIOS on the HP Envy 17 Leap Motion laptop: InsydeH20 Setup Utility Rev 3.7


Legacy Support: Disabled    (don't change it)
Secure Boot: Enabled    (don't change it)


UEFI Boot order:
   USB diskette on Key/USB Hard Disk
   Internal CD/DVD Rom Drive
  OS boot Manager
  USB CD/DVD Rom Drive

Legacy Boot order (disabled)
   Notebook Hard Drive
   Internal CD/DVD Rom Drive
   USB Diskette on Key/USB Hard Disk
   USB CD/DVD Rom Drive

Ubuntu 14.04 LTS 64-bits is UEFI and secure boot enabled, so I expected not to have problems. 
Actually the problem is not in the order in UEFI menu, but how you select the boot device.

Here is what you can do for this brand of HP laptop. Similar procedure may be followed for other laptops with similar BIOS. 
Is manual procedure, but actually you did not have to modify your BIOS at all.

What you need to do is press ESC while powering up the laptop, then you cause to pause the normal boot process and then you can select the boot device. 

a) Immediately press ESC when you power up the laptop
b) A menu appears, select: F9 (Boot Device Option)
c) Another menu appears (Boot Option Menu) with the following options
       OS Boot Manager
       Boot from EFI File

select the second option. The first option is for booting Windows 8.1

d) Select the device which shows Usb (not Sata) and press Enter. My options were:
   No Volume LABEL, [Acpi(PNPA03,0)/ Pci(1410/Usb (10.0)/HD (Part1, Sig2C5CDEE0-DE1E-4D1E-BD01-C627858D793A)]
   No Volume LABEL, [Acpi(PNP0A03,0)/Pci(1FI2)/Sata(0,0,0)/HD (Part2, Sig82A9DD80-D12E-479D-968F-115EFB584C6C]

e) next screen show <EFI>, press Enter
f) next screen shows <ubuntu>, press Enter
g) In the next screen selects shimx64.efi, and press Enter,
h) Grub menu appears! Select Ubuntu, and Ubuntu boots!

Actually what you did is select manually how to boot Ubuntu. The shimx64.efi file is located in /boot/efi/EFI/ubuntu/ as it is shown in the next lines:

amorales@hpenvy17:/boot/efi/EFI/ubuntu$ ls -l
total 3416
-rwxr-xr-x 1 root root        126 dic  9 02:28 grub.cfg
-rwxr-xr-x 1 root root   956792 dic  9 02:28 grubx64.efi
-rwxr-xr-x 1 root root 1178240 dic  9 02:28 MokManager.efi
-rwxr-xr-x 1 root root 1355736 dic  9 02:28 shimx64.efi
amorales@hpenvy17:/boot/efi/EFI/ubuntu$ 

I  tested Ubuntu, It sees Windows 8.1 disks (OS and Recovery), I shutdown  Ubuntu, power on  the laptop w/o ESC, booted Windows 8.1, shutdown, 
power up with  ESC, followed again steps b) to h) and got Ubuntu running. Even though is kind of manual dual boot, I'm happy :p!

Hope this helps others with similar problem.

Regards,

---

### Post by robertj20112 on 2014-12-23
Thanks, Aurelio.  I stumbled upon that same solution by a somewhat different route.  The real problem is this "hardwired" HP boot process which it seems cannot be "cracked" so we can have an elegant, permanent solution.  Don't think I'll be buying another HP product, ever!!

---

