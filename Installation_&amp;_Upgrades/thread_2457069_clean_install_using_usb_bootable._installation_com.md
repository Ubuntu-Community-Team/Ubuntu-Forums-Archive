---
title: "clean install using usb bootable. installation complete. no &quot;boot file&quot; or drive"
date: 2021-01-25
forum: Installation &amp; Upgrades
---

### Post by rgperon2 on 2021-01-25
not a dual boot, not a cd install. brand new drive that used to be data only (no op system).  sometimes it says no boot file, sometime no bootable drive.  installed 4 times, correctly configured bios all times.

---

### Post by CelticWarrior on 2021-01-25
Welcome.

Please post the hardware specifications and how did you made the USB installer.

---

### Post by oldfred on 2021-01-25
Was drive a RAID data drive? If so you need to remove RAID meta-data.

UEFI or BIOS install?
gpt or MBR partitioning?

---

### Post by rgperon2 on 2021-01-25
Intel D945GCLF board. 
used rufus to create the bootable usb and put the ubuntu server iso on it.  
It installs each time.  if i leave it to boot via the internet, get the pxe error code of no boot file.  if i set the bios to boot from hdd, get the no bootable device message.  if i put the usb drive back in, it starts the install process again.
no raid, bios install, partitioned via the install process.

---

### Post by oldfred on 2021-01-25
Rufus creates just a BIOS installer or an UEFI installer.
If you want or need BIOS, you must select MBR & CSM(non-UEFI) when creating install flash drive.

Shows BIOS non-CSM

[https://ubuntu.com/tutorials/create-a-usb-stick-on-windows#3-usb-selection](https://ubuntu.com/tutorials/create-a-usb-stick-on-windows#3-usb-selection)
[https://rufus.ie/](https://rufus.ie/)

Shows UEFI
[https://askubuntu.com/questions/1278772/unable-to-access-ubuntu-from-uefi](https://askubuntu.com/questions/1278772/unable-to-access-ubuntu-from-uefi)

If only installing Ubuntu still better to use gpt, but you then need a bios_grub partition for grub to correctly install.
If drive is already gpt, installer will create a bios_grub with a BIOS/CSM/Legacy type install. But if partitioned in advance installer assumes you have created the partitions you need.

---

### Post by rgperon2 on 2021-01-25
implication from oldfred is that a bios usb bootable installation iso does NOT add boot capability when installing? how can i make changes to use 'gpt' if its not booting up?

---

### Post by CelticWarrior on 2021-01-25
> **rgperon2 said:**
> implication from oldfred is that a bios usb bootable installation iso does NOT add boot capability when installing? how can i make changes to use 'gpt' if its not booting up?
No, A BIOS bootable installation ISO used in Rufus with the BIOS options will boot in BIOS hardware such as yours.

---

### Post by oldfred on 2021-01-25
The only issue would be is if you partitioned in advance a gpt drive, but did not include a bios_grub partition.
Typically you get a full install, and at very end failure of grub to install.
You just need to add the bios_grub partition, if using gparted. It is unformatted, 1 or 2MB anywhere within the first 2TB of a drive, so you can just shrink any partition by 4MB to make room for it.
If using gdisk for partitioning it is not called a bios_grub partition but code ef02 setting.
Actual gpt  for partition type for the grub  is a very long GUID.

You then do not even have to reinstall, just install grub.

---

### Post by rgperon2 on 2021-01-26
spotted rufus option for gpt, so will try that this time....thanks for the hints.

didn't work....just got flashing underscore...trying bios with "added fixes for old BIOSes"

---

### Post by oldfred on 2021-01-26
The Rufus version with gpt is for UEFI boot only on installer. And how you boot install media UEFI or BIOS is then how it installs.

Whether your drive is gpt or MBR for your install does not matter with Ubuntu.
Windows has required gpt for UEFI installs since 2012.
I have used gpt with BIOS starting in 2010.

---

### Post by rgperon2 on 2021-01-26
does it matter that there was no op system on the HD?  i think last bios update was about 2005 :(  it's a discontinued atom board.

ah well, back to "no bootable device" :(  i know it's loading up the HD since i've watched the load details.

when i put it in an external box and hooked it up the my win 7 pro lappy, it doesn't even see it (figured since it now was formatted as linux)

---

### Post by CelticWarrior on 2021-01-26
```

```> **rgperon2 said:**
> does it matter that there was no op system on the HD?  i think last bios update was about 2005 :(  it's a discontinued atom board

No, whatever OS is already installed or none never matters.
[COLOR=#000000][Intel D945GCLF]("https://ark.intel.com/content/www/us/en/ark/products/42490/intel-desktop-board-d945gclf.html") is from Q2 2008, according to Intel.[/COLOR] Unfortunately discontinued and Intel no longer provides *any* download for it other than a PDF telling you "it's game over". Google found this [https://drivers.softpedia.com/get/BIOS/Intel/Intel-D945GCNL-BIOS-0027.shtml](https://drivers.softpedia.com/get/BIOS/Intel/Intel-D945GCNL-BIOS-0027.shtml) but I'm certainly not advicing you to try it although Softpedia isn't know for publishing malware.

Please note that this board has BIOS. So, BIOS related options is what you should be looking for at all times, not something UEFI related. This is particularly important when using Rufus as explained before. If you want you may try the multi-platform Balena Etcher that uses DD therefore it produces a 1:1 copy of the ISO, just like if it was burned into optical media (and the USB will behave the same way). Ubuntu ISOs are hybrid, i.e., they boot in BIOS or UEFI. This should be fool-proof.

---

### Post by rgperon2 on 2021-01-26
no luck :(  thanks for all your ideas guys.  still shows 'no boot drive'.

---

