---
title: "LUbuntu OS and the drive on which it was installed both MISSING!"
date: 2014-12-14
forum: Installation &amp; Upgrades
---

### Post by bapu2 on 2014-12-14
Hi,

I have 2 hard drives on my machine. One 500GB(master drive)  and one 40GB(slave drive).  I originally had Windows 7 installed on my first drive(i.e. 500GB  drive). I am planning to install LUbuntu alongaside Windows 7. Now i installed LUbuntu on my machine. I wanted to keep LUbuntu  completely seperate from my windows installation and hence wanted to  install it on the 40GB drive. So during installation I select the 3rd  option and in that I select the bootloader installation drive as this  40GB drive. I follow all the steps as mentioned on LUbuntu site for  installation. The installation proceeded smoothly and PC restarted. 


  [B]However after installation I don't see LUbuntu anywhere. I  didn't get any option during startup to select OS.  And to my horror, the 40GB drive is missing from my "My Computer" window  if I run Windows OS. My Windows OS still works perfectly normal. But  the LUbuntu OS and the drive on which it was installed both disappeard.
:confused::confused::confused::shock::-?:-?:-?:-k
[/B]

  Please help me resolve the issue as I want to start working on LUbuntu. Please help.

---

### Post by sudodus on 2014-12-14
Welcome to the Ubuntu Forums :-)

Please specify your computer

- Brand name and model
- CPU
- RAM (size)
- graphics chip/card
- wifi chip/card

and also specify which version of Windows you are running now (still Windows 7?) Are you running the computer in old style BIOS mode or UEFI mode?

The answers will make it possible to give better advice.

-o-

You can also try to identify the drives and partitions when booted from the Lubuntu install CD/DVD/USB drive.

---

### Post by ajgreeny on 2014-12-14
I suspect that the machine is still booting with the Windows disk as first priority, thus booting straight into Windows, as its own bootloader has not been overwritten by grub, and Windows can not see Linux partitions and OS.

Go into the BIOS setup and change the disk that has first priority to the 40GB Ubuntu disk, or use whatever key-press is available to select the boot disk on the fly (often F8 or F11, but could be something else) and with luck you will see a grub menu and be able to boot to either Ubuntu or Windows from that

---

