---
title: "Problem about installing ubuntu 14.04 on a fresh WD Green 1 TB hard disk"
date: 2014-07-10
forum: Installation &amp; Upgrades
---

### Post by barteg105 on 2014-07-10
Hi,

after i upgraded my desktop's hard disk to WD Green 1 TB, i spent to much time to get Ubuntu to work on my device ... i tried too many different versions to get the PC works as 12 , 14 , 11 either 64 bits and 32 bits ... but its always no use and i still facing errors

i tried to install it from DVD/CD/USB Flash drive but it still giving the same error
]the error is that when i start the installation its works till the installation type page , i tried "install beside another version" which isn't working and i tried the "erase and re-install" ... the result is always the same >> the error window "installation filed" showed up with [error 5] input/output error "the installer encountered an error coping files to the hard desk"
]sometimes when i choose "Erase and Re-install" from the Installation type page >> the screen gets blackout and the "Hard Disk LED which in front of the PC's case to indicates the hard disk activity" keeps blinks too long

i think the problem is Ubuntu can't work with the hard desk WD Green 1TB or maybe my Device

the hard disk works super fine when i attaching it to my windows machine as an external Hard Disk

my Device hardware components are:

"CPU" Intel Pentium E5200 dual cores which support 64 bit as well as 32 bit
"Mother Board" Gigabyte G41M-ES2L]4GB DDR2 "Ram" memory
internal wlan network card ,CD/DVD Drive , USB Bluetooth ,USB mouse , Keyboard and of Course an LCD monitor using VGA Port

---

### Post by oldfred on 2014-07-11
I have a slightly newer Gigabyte board  EP43-UD3L with Intel(R) Core(TM)2 CPU 6600 @ 2.40GHz and have had no issues once I got over the issue that no USB entry boots my flash drive and it is just another hard drive.
My last hard drive from 2009 is Western Digital WD Green WD6400AACS 640GB 7200, but my boot drive now is a SSD.

What video card are you using?

Newer Gigabyte have had these issues:
       Needed F6 to set ACPI=Off.and nomodeset
Gigabyte UEFI boot issues - The partition size of the created USB Installer device needs to be under that of 4GB. 
Others found UEFI/BIOS update solved issue of 4GB FAT limit.
turns out the IOMMU needs to be enabled in the BIOS. This problems seems to be exclusive to Gigabyte boards.

    
I now only use 64bit Ubuntu with gpt partitioned drives. But if gpt you have to have a newer system with UEFI if you want to boot Windows from same drive with gpt. Ubuntu boots from gpt with either BIOS or UEFI, but Windows only boots with UEFI.

I also prefer to partition in advance with gparted so I have control over partition sizes and it is a bit easier to set up with gparted. But you still have to use Something Else and change button to select which partition is / (root) and its format. I use data partitions not /home as separate partition for data, but that can only be done after install. If using /home you also press change and mount & format it. If reusing a /home you DO NOT tick the format button.

Post this:
sudo parted -l

---

### Post by chrischavez on 2014-07-12
This sounds like possibly an issue either with the hard drive or installation media, but since you mention trying both DVD and USB flash, it may be the hard drive. Is it possible for you to paste the output of dmesg after the install fails? This will likely detail the input/output error and help identify what was causing it.
Did you verify your Ubuntu download? (See [http://askubuntu.com/questions/17764/how-can-i-check-the-integrity-of-a-downloaded-ubuntu-cd](http://askubuntu.com/questions/17764/how-can-i-check-the-integrity-of-a-downloaded-ubuntu-cd))
Looking around, some have said that defective RAM was responsible, so you may want to check that as well:
[http://askubuntu.com/questions/65830/errno-5-input-output-error-when-trying-to-install](http://askubuntu.com/questions/65830/errno-5-input-output-error-when-trying-to-install)

---

