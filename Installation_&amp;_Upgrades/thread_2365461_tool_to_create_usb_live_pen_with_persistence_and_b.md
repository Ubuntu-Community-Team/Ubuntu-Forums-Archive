---
title: "tool to create usb live pen with persistence and bootable from uefi and bios"
date: 2017-07-07
forum: Installation &amp; Upgrades
---

### Post by kerrygee on 2017-07-07
Hi,

i made some investigation on this topic so far, but i couldnt find a solution yet. By the word solution, i am looking for some gui tool that can easily create a live usb pen drive with persistence, bootable from legacy bios and uefi systems from the same pen drive. the source linux is a kubuntu iso. The best solution would be some easy to use windows application, but a gui linux tool would be fine as well. In my case i am pretty ok with editing files and doing terminal stuff, but the gui tool should be usable from novice users with the aid of some tutorial or something like that, that is to say, some easy to use application for everybody.

Any recommendations for this issue would be very nice.

Thanks in advance

K.

---

### Post by yancek on 2017-07-07
Have you tried mkusb?

[https://help.ubuntu.com/community/mkusb](https://help.ubuntu.com/community/mkusb)

Booting Legacy or UEFI would seem to be an option of your BIOS on the hardware.  Newer releases of Ubuntu should be able to boot/install either.

---

### Post by C.S.Cameron on 2017-07-07
+1 mkusb.
It is one of the few bootable USB makers that can create persistent partitions that allow over 4GB of persistence.

---

### Post by kerrygee on 2017-07-07
> **yancek said:**
> Have you tried mkusb?

[https://help.ubuntu.com/community/mkusb](https://help.ubuntu.com/community/mkusb)

Booting Legacy or UEFI would seem to be an option of your BIOS on the hardware.  Newer releases of Ubuntu should be able to boot/install either.

Hi yancek,

thanks for the link. Most new systems run in UEFI mode and secure boot turn on, so starting a dd created live only iso like new kubuntu or ubuntu would always work fine. The only difference you see is the boot screen/splash which differs when started from legacy bios over uefi. The aim is to have a 64bit system capable of booting from legacy bios and extended firmware with secure boot either turned on or off. This seems to be an option: [https://help.ubuntu.com/community/mkusb/persistent](https://help.ubuntu.com/community/mkusb/persistent) and this [https://help.ubuntu.com/community/grub-n-iso](https://help.ubuntu.com/community/grub-n-iso)

Looks like its not a trivial task or can be easily automated in one tool.

---

### Post by yancek on 2017-07-07
I'm not sure what the question/problem is.  I used mkusb to create an installable Ubuntu 16.04 on a flash drive.  I booted it and saw the purple Ubuntu screen which indicated to me from the Ubuntu documentation that it was booting in Legacy mode.  Re-booted and change BIOS settings to UEFI and booted and installed UEFI.

---

### Post by kerrygee on 2017-07-07
> **yancek said:**
> I'm not sure what the question/problem is.  I used mkusb to create an installable Ubuntu 16.04 on a flash drive.  I booted it and saw the purple Ubuntu screen which indicated to me from the Ubuntu documentation that it was booting in Legacy mode.  Re-booted and change BIOS settings to UEFI and booted and installed UEFI.

Its not about installation. If i wanted to simply install the os, then a quick iso to the usb with dd and simply booting from it would be pretty much do it. The problem is: Whenever i create a persistent USB drive with guidus using a kubuntu16.04.02 x64 iso, guidus creates a EFI bootable only pen drive, that only starts from UEFI enabled systems. On BIOS systems, the screen stucks at a blinking cursor with that same pen drive. Obviously a clear sign, that the usb pen is prepared for Extended Firmware Interface systems only. So the problem is: What exactly are the steps/do i have to go, to make the pen drive BIOS and UEFI bootable with guidus?

best

K.

---

### Post by monkeybrain20122 on 2017-07-07
I use [multi-system]("http://liveusb.info/dotclear/index.php?pages/install")

---

### Post by yancek on 2017-07-07
>  What exactly are the steps/do i have to go, to make the pen drive BIOS and UEFI bootable with guidus?


mkusb.  In my earlier post I indicated that I used mkusb to create a bootable usb.  I then booted that usb Legacy boot and later booted the same usb UEFI.  I didn't use it with Kubuntu but I would not expect that to matter.  If you are unable to boot Legacy using this software, I'm not sure what the problem would be as it worked for me.

---

### Post by mc4man on 2017-07-07
Without actually knowing (have no use for persistence & personally just use Disk Image Writer), I'd take a guess that if you are using mkusb on a UEFI install you can't make a boot usb with grub-pc. 
So if that's the case then maybe make your usb from a live session. That's what I take from the message as seen in screen

---

### Post by sudodus on 2017-07-10
> **mc4man said:**
> Without actually knowing (have no use for persistence & personally just use Disk Image Writer), I'd take a guess that if you are using mkusb on a UEFI install you can't make a boot usb with grub-pc. 
So if that's the case then maybe make your usb from a live session. That's what I take from the message as seen in screen

+1

You can find such systems already prepared with mkusb and packed as compressed image files at the following link,

[Compressed image file with a persistent live system](https://help.ubuntu.com/community/mkusb/persistent#Compressed_image_file_with_a_persistent_live_system)

---

### Post by kerrygee on 2017-07-14
Many thanks for all the nice replies and supporting help. I finally decided to use [URL="https://www.pendrivelinux.com/yumi-multiboot-usb-creator/"]YUMI &#8211; Multiboot USB Creator
[/URL]
It is capable in creating a BIOS and UEFI bootable pen drive with persistence inside a casper-rw file. Thats for sure limited to 4GB due to FAT32 limitation but its perfectly ok to me. External and shareable data will be stored on a second partition formatted in NTFS or FAT32.

best regards and have a nice day

K.

---

### Post by C.S.Cameron on 2017-07-15
The FAT32 or NTFS partition needs to be the first partition on the drive in order to be seen by Windows, this may conflict with the syslinux requirements of Yumi, that also require the first partition.

Windows can save to the Yumi partition, however these files are read only while booted from the Yumi drive.

---

### Post by kerrygee on 2017-07-16
> **C.S.Cameron said:**
> The FAT32 or NTFS partition needs to be the first partition on the drive in order to be seen by Windows, this may conflict with the syslinux requirements of Yumi, that also require the first partition.

Windows can save to the Yumi partition, however these files are read only while booted from the Yumi drive.

Yes, this is true, but for now, it works just fine. I am partitioning the USB drive into two partitions: One for the YUMI and another for the data i want to be able to save and share with my windows system. Whenever i create some file, i save it on the second partition, so i can access it from in- and outside the live system at will. Both partitions are formatted FAT32. It works just fine!

best

K.

---

