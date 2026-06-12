---
title: "Start up disk creator  failure"
date: 2014-11-01
forum: Installation &amp; Upgrades
---

### Post by exodus3 on 2014-11-01
i am trying to re-instal the ubuntu OS onto my jump drive again [don't ask]  but its just not working 
when i plug the jump into the port ,disk creator says there is not enough room and i have to reformat it,even tho i just did a full format on windows first 
so i go ahead and lead disk creator re-format the jump drive ,after 15 secs this window pops up,but it is still showing as erasing 

after  20 mins the erasing is done, but i am back at square one again  


[ATTACH=CONFIG]257686[/ATTACH]

---

### Post by yancek on 2014-11-01
Not sure what the error means.  Have you tried formatting with GParted.  If you were formatting from windows does that mean a vfat filesystem?

---

### Post by exodus3 on 2014-11-02
my jump has always been formatted in the NTFS  format

---

### Post by sudodus on 2014-11-02
Is jump another word for USB pendrive, USB stick, USB flash drive?

The Ubuntu Startup Disk Creator wants the USB drive to be formated with FAT32 (or FAT16). See this link

[https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)

You can use ***gparted*** to create the FAT32 file system (in Ubuntu). If you are working in Windows, you can use the Windows own tool to format it to FAT32.

If you want persistence and want to install Ubuntu 14.10, use ***Unetbootin***. There is a bug (for 14.10) in the Startup Disk Creator, but if you want to install Ubuntu 14.04.1 LTS, it will work.

-o-

Otherwise, if you 'only' want a live drive and to install Ubuntu from it, use ***mkusb*** from Ubuntu or ***Win32 Disk Imager*** from Windows. Those tools need no formatting because they simply clone the iso file to the USB drive. See this link

[https://help.ubuntu.com/community/Installation/FromUSBStick#Known_Issues](https://help.ubuntu.com/community/Installation/FromUSBStick#Known_Issues)

---

### Post by exodus3 on 2014-11-02
> **sudodus said:**
> Is jump another word for USB pendrive, USB stick, USB flash drive?

The Ubuntu Startup Disk Creator wants the USB drive to be formated with FAT32 (or FAT16). See this link




[PHP]Is jump another word for USB pendrive, USB stick, USB flash drive[/PHP]

all of the above  and i've also heard it called a thumb drive,,seems the U does not apply to what people call it 


format the jump to fat32 solved the disk creator problem ..thanks

---

