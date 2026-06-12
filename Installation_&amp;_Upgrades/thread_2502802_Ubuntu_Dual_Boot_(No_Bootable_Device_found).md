---
title: "Ubuntu Dual Boot (No Bootable Device found)"
date: 2024-11-30
forum: Installation &amp; Upgrades
---

### Post by mahadi025 on 2024-11-30
I installed ubuntu on my machine. Installation went fine. After installation was complete i was asked to remove the installation media and press enter. Then it rebooted the machine but instead of opening the ubuntu it loads into Windows 11, then I rebooted the machine and by pressing F12 I opened the boot menu from there I selected Ubuntu. After clicking ubuntu it shows error message "No bootable device found". I am using Dell G3 Laptop. After doing some research most of the solution points me that I should select UEFI and legacy from the boot sequence menu but on my boot menu I do not see the options. It is completely blank. Also, I used ubuntu alongside windows 11 before with this laptop. Below is the link boot repair summary that I did using "Try Ubuntu" (after installing the ubuntu). I have attached the Boot Sequence Menu Page. From the picture u can see that boot sequence option is empty (Sorry for the image quality)

[Ubuntu Pastebin]("https://paste.ubuntu.com/p/nvwjGV4nbd/")

---

### Post by grahammechanical on 2024-11-30
I have had to press PgDn 8 times to reach the end of your post so as to reply. Please put in your post the link to Pastebin so that I can read the Boot Repair summary in a separate web browser tab.

you say this:

> After doing some research most of the solution points me that I should select UEFI and legacy from the boot sequence menu

That cannot be the right thing to do. It is my understanding that Windows 11 would be installed in UEFI mode and not BIOS/Legacy/CSM (compatibility Support Mode). The rule with dual booting Windows and Ubuntu is that Ubuntu must be installed in the same mode as Windows. So, it cannot be right that you should install Ubuntu in Legacy mode. How we load the Ubuntu install media by using the UEFI settings utility and selecting either UEFI mode or Legacy mode determines the mode Ubuntu is installed in.

Another rule is to turn off Fast Start up in Windows as it is a form of hibernation and the Ubuntu installer cannot read the Windows file system when it is hibernated. Normally, the Linux boot loader (Grub) would detect the boot files of both Ubuntu and Windows and create a boot menu that would appear soon after the machine started loading and the we get options as to which operating system to boot. This detection of Boot files cannot happen when Windows is hibernated by Fast Start Up.

Regards

---

### Post by mahadi025 on 2024-11-30
Okay Thanks I added the Pastebin link.
 I tried turning off the fast boot, but still the same error.

---

### Post by yancek on 2024-11-30
Is your windows OS on /dev/sda?  You show windows partitions on both sda and the nvme drive.  Line 102 of boot repair shows nvme0n1p2: ubuntu install.  Line 110  shows nvme0n1p3 as an  efi partition with only ubuntu files.  Both droves are GPT so windows should be UEFI.  I think at least part of the problems is that bitlocker is on in windows and if you look at line 64, it shows nvram is locked so you will need to change that and there is no single, simple way to do that.  You could try an online search for unlocking nvram on Dell or something similar.

---

### Post by oldfred on 2024-11-30
What model Dell?
Did you update UEFI firmware & NVMe firmware?

I do not see anything in Report, maybe someone else will.
Error on updating UEFI variables should not matter as you have valid UEFI boot entry that refers to correct ESP. 
You can see that from live installer in UEFI mode with this which is in report
sudo efibootmgr
UEFI entries refer to ESP by partuuid or GUID. 
You can see partuuids with this which are in report.
lsblk -e 7 -o name,mountpoint,label,size,fstype,uuid,partuuid 

Most Dell work without issue.
Very new Dell are UEFI only, only some  old Dell with early UEFI, seemed to need both UEFI & Legacy on and then choose to boot in UEFI mode.

---

### Post by jeremy31 on 2024-11-30
```
Boot0003* Windows Boot Manager	HD(1,GPT,4431fc30-3bca-4733-a83f-98d02c43a58a,0x800,0x32000)/File(\EFI\Microsoft\Boot\bootmgfw.efi)57494e444f5753000100000088000000780000004200430044004f0042004a004500430054003d007b00390064006500610038003600320063002d0035006300640064002d0034006500370030002d0061006300630031002d006600330032006200330034003400640034003700390035007d00000031000100000010000000040000007fff0400
Boot0004* UEFI: HP SSD S700 Pro 512GB, Partition 3	PciRoot(0x0)/Pci(0x17,0x0)/Sata(0,65535,0)/HD(3,GPT,78a8fd39-0d1b-40b1-bc04-084db544fb29,0x117cc800,0x1b6000)0000424f
Boot0005* Ubuntu	HD(3,GPT,78a8fd39-0d1b-40b1-bc04-084db544fb29,0x117cc800,0x1b6000)/File(\EFI\ubuntu\shimx64.efi)
```

The Boot0004 and Boot0005 have a partition ID that matches this
```
&#9500;&#9472;sda3      ntfs      FE5043345042F347                     78a8fd39-0d1b-40b1-bc04-084db544fb29   
```
When I would expect it to match
```
&#9500;&#9472;sda1      vfat      FE2A-2806                            4431fc30-3bca-4733-a83f-98d02c43a58a             EFI system partition
```
or
```
&#9492;&#9472;nvme0n1p3 vfat      6909-BC9A                            a1f4e30b-8769-4a8c-aa92-1c9d111bae7a     
```
But the second one doesn't have the EFI system partition set on it

---

### Post by mahadi025 on 2024-11-30
Okay I will try that

---

### Post by mahadi025 on 2024-11-30
My laptop is DellG3 3590. I didn't update any firmware. Dual boot was working fine like about a week ago. Then I had to remove all the bit locker encryption from all the drives. While decrypting the drives I was deleting the volumes and updating the partition size using "diskpart" it was my** mistake**. I should not have done it because of this the decryption process got stuck. So, I used "manage-bde" to pause the decryption and restarted the decryption again. After a while the drives were decrypted.

After that Ubuntu was not booting up, so I thought I must have messed up the decryption or something. After that I deleted the volume and installed Ubuntu again. From that moment I am facing this error. I also reset my Windows 11. 
I have two drives as shown in the screenshot. On disk0 I have windows installed and on disk 1 I have a partition for the Ubuntu (Last part 208 GB). For installing Ubuntu I had to remove the bit locker from disk 1 maybe that is the issue because as far as I am concern when I installed ubuntu like a year an ago I removed the bit locker from all the drives but this time i only removed it for disk1.

---

### Post by yancek on 2024-11-30
You should use your Ubuntu 'live' USB or some other Linux to mount the two vfat partitions to see what is in them.  Both partitions below look like EFI partitions but only nvme0n1-3 has EFI files and they are only Ubuntu.  sda1 is also a  vfat partition but nothing show in it so were the files for windows deleted or is th partition locked?

---

### Post by mahadi025 on 2024-11-30
Okay I will try that

---

### Post by mahadi025 on 2024-11-30
I have two hard drives installed. You can see that from the attachment. On disk 0 I have five partition, on this disk windows is installed. On disk 1 I have three partition, first partition (Drive E) is for windows, the last two are for Ubuntu. I formatted this before installing Ubuntu also removed bit locker from disk 1.

---

### Post by yancek on 2024-12-01
In post 6, you listed the partial output of the efibootmgr command but did not list the boot order.  Boot0005* Ubuntu	is to boot Ubuntu so do you have that set first in your BIOS?  If so, it should boot Ubuntu and if it does, you should be able to run sudo update-grub to add windows to the Grub boot menu and boot both Windows and Ubuntu.   If you look at the 2 EFI partitions, the one on the Ubuntu disk as well as the one on the windows disk you can check to see what is in the partitions.  Before you installed Ubuntu again, did you have the Ubuntu EFI files on the EFI partition on the first (windows) disk.

---

### Post by mahadi025 on 2024-12-01
I managed to solve it by adding new boot option and set the file name as **grubx64.efi**(as the secure boot is off) but for some reason the default Ubuntu was set us **shimx64.efi** which is for secure boot I think

---

### Post by oldfred on 2024-12-01
I have never had UEFI Secure boot on, but it uses shimx64.efi.
If Secure boot is off, it should not matter whether you use grubx64.efi or shimx64.efi.

---

### Post by mahadi025 on 2024-12-02
well right now my secure boot is off, if I use shimx64.efi it does not work. Anyway thanks for the help.

---

