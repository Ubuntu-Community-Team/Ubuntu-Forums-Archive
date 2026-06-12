---
title: "ubuntu windows nothing only a &quot;-&quot;"
date: 2013-07-11
forum: Installation &amp; Upgrades
---

### Post by andreisid on 2013-07-11
Hi

Yesterday i tried to install ubuntu on a different partition but on the same hdd with windows 7. I thought it will work like duo boot. I restarted my computer, and after that pc don t boot. 'Multiple partitions active' . Or appears something with network and please insert '. I read about but i can t do nothing on my pc. I tried to boot ubunto from stick usb, but it doesn t load, appears only '-'.
what should i do? I don t have livecd with windows because it was preinstal. Sorry for english but i write from phone.

---

### Post by oldfred on 2013-07-11
You cannot have multiple partitions with boot flag (active partition in Windows). Windows has to have a boot flag to know what partition has the rest of the boot code. Grub does not use boot code but also has more boot code & menu in Ubuntu partition. Some BIOS will not let you boot without a boot flag on one primary partition, so we suggest one boot flag per hard drive even if just using Linux.

You should make a Windows repairCD or flash drive. Some repairs cannot be made from a Linux repairCD or flash drive.

       Post the link to the BootInfo report that this creates. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)
Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration and diagnose advanced problems.
LighterWeight (Lubuntu based) Boot-RepairCD
[http://sourceforge.net/projects/boot-repair-cd/files/](http://sourceforge.net/projects/boot-repair-cd/files/)
Full Ubuntu 13.04 liveDVD or USB Install with Boot-Repair included (for newer computers) 
[URL="https://help.ubuntu.com/community/LinuxSecureRemix"]https://help.ubuntu.com/community/LinuxSecureRemix

[/URL] Make your own Windows repairCD (not vendor recovery):
[http://forums.techarena.in/guides-tutorials/1114725.htm](http://forums.techarena.in/guides-tutorials/1114725.htm)
Windows users only - Silverlight
[http://windows.microsoft.com/en-GB/windows7/Create-a-system-repair-disc](http://windows.microsoft.com/en-GB/windows7/Create-a-system-repair-disc)

   Windows 7 repair USB, Also Vista if service pack installed
[http://www.intowindows.com/how-to-repair-windows-7-from-usb-flash-drive-repair-without-installation-dvd-disc/](http://www.intowindows.com/how-to-repair-windows-7-from-usb-flash-drive-repair-without-installation-dvd-disc/)
[http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html](http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html)

[URL="https://help.ubuntu.com/community/LinuxSecureRemix"]
[/URL]

---

### Post by andreisid on 2013-07-11
I have one laptop. A ßtick with ubuntu bootable. Error booting. I don t care about windows or flags. I want to install ubunto on my hard disc. I cant acces or diwnload those stuff because i don t have another pc.

---

### Post by fantab on 2013-07-11
Boot with Ubuntu DVD/USB and 'Try Ubuntu Without installing"... after the desktop is ready open Terminal and run the following command:

```
sudo parted -l
```

and post its output here. You can copy-paste.

---

### Post by andreisid on 2013-07-11
And why if i selected usb hdd don t load? What is atapi cdrom or usb fdd or network boot or usb cdrom? And how to format the hdd if i cannot boot the sistem?

---

### Post by andreisid on 2013-07-11
It black screeen with -.

---

### Post by fantab on 2013-07-11
The Ubuntu USB doesn't need HDD to boot. It should boot.

---

### Post by andreisid on 2013-07-11
It should but it doesn t. Shhould i open the notebook and try to discinect the hdd with windows?

---

### Post by andreisid on 2013-07-11
And d2d acer and alt plus f10 still black screen with -

---

### Post by fantab on 2013-07-11
What graphics do you have on your Laptop/desktop?

Try the 'NOMODESET' option; here's a [**how to**]("http://ubuntuforums.org/showthread.php?t=1613132").

---

### Post by andreisid on 2013-07-11
Cpu amd c60 with radeon hd graphic
ram 1gb

---

### Post by fantab on 2013-07-11
Try 'nomodeset' opttion and get back.

A side note: With only 1gb RAM your system will be a bit hard pressed to run Ubuntu comfortably. Instead you must consider, [XUBUNTU]("http://xubuntu.org/") or [LUBUNTU]("http://lubuntu.net/"). These are Ubuntu flavors with XFCE and LXDE, respectively. They are very light in the system resource consumption than Ubuntu with Unity.

---

### Post by andreisid on 2013-07-11
To be clear:
1 hdd with multiple partition (1. Win 2. Ubuntu)
2. Pc doesn t boot
3. Error multiple active partition
Or something mac and a lot of numers and pxe 
Or insert a bootable disk
and now only a -.
4. I cannot acces a system or another
5. I tried to load ubuntu from a stick usb but even if i put it like 1 priority still doesn t load ( maybe is a problsm with the stick?)

---

### Post by andreisid on 2013-07-11
If i reinstal bios?

---

### Post by fantab on 2013-07-11
Ok lets start from scratch...

Have you checked the integrity of your downloaded .iso ubuntu with MD5Sum check. This check will tell you if your dowloaded .iso is good. If not you will have download again.
Have you tried another USB? How did you burn the ubuntu.iso to the USB?

If you are getting 'insert bootable disc' then perhaps you didn't burn the .iso to USB properly. Use instructions [HERE]("http://www.ubuntu.com/download/desktop/create-a-usb-stick-on-windows").

---

### Post by diazepamkit on 2013-07-11
> **andreisid said:**
> I have one laptop. A ßtick with ubuntu bootable. Error booting.** I don t care about windows or flags. I want to install ubunto on my hard disc.** I cant acces or diwnload those stuff because i don t have another pc.

referring to this then you should format your hd, re-download ubuntu create the live-cd insert the cd and install it

---

### Post by andreisid on 2013-07-11
A friend did it for me

---

### Post by andreisid on 2013-07-11
But still black and - like amy winehouse

---

