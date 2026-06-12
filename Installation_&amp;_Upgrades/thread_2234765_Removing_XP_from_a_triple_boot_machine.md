---
title: "Removing XP from a triple boot machine"
date: 2014-07-16
forum: Installation &amp; Upgrades
---

### Post by J Tinsby on 2014-07-16
Hello,

First I wanted to build the machine this way and now I'd like to get rid of XP from the 3 OS's. <sigh>

I currently have XP, Win 7 and Ubuntu 14.04 in that boot order, it's working fine but I am ready to let XP, sometimes called "XPired" go it's merry way. The boot flag is on the XP partition and I have EasyBCD on XP handling the boot order.
My idea was to move the boot flag to the 7 partition and allow the install disc of 7 to re-create an MBR, or EasyBCD, since right now that 7 boot info is written to XP. After I have proven I can boot to 7, I'd install EasyBCD there to point it to Ubuntu and format the XP partition.

Note: My Grub is NOT in control of the boot up of any OS except Ubuntu, since it resides on the / partition not on /sda. The Windows MBR is intact even though it's on XP.

So the question is will my idea work or not? I DO have an image of the entire HD so if this goes off the rails I can restore it to the way it is now.

Can it be done that easily or am I in for a tortuous journey?

Thanks,

J T

---

### Post by yancek on 2014-07-16
>  since right now that 7 boot info is written to XP

That's the only problem I can see.  Your order is correct, using windows 7 install disk first before any other changes to ensure you can boot.  You need to first verify that windows 7 is on a primary partition as windows needs boot files on a primary.

---

### Post by Mark Phelps on 2014-07-17
> The Windows MBR is intact even though it's on XP.

The MBR is not on any of the OSs; instead, it is in a separate area of the hard drive.  Removing XP will not affect the MBR.

However, the problem is that with XP on the drive, the Win7 disk is most likely only going to rewrite the boot loader stuff that is already in the XP partition -- because that is where it sees it.

You probably need to remove XP, boot from the Win7 disk, and THEN do the Startup Repair.  You may have to run that three times to get it working.

---

### Post by J Tinsby on 2014-07-17
> **yancek said:**
> That's the only problem I can see.  Your order is correct, using windows 7 install disk first before any other changes to ensure you can boot.  You need to first verify that windows 7 is on a primary partition as windows needs boot files on a primary.

Do you agree with moving the boot flag to 7 or should I simply let it alone? 7 is on a primary partition.

Thanks

J T

---

### Post by Bucky Ball on 2014-07-17
Leave boot flags and everything else as they are.

Boot into Ubuntu, open Gparted and delete the XP partition.

Open a terminal:

```
sudo grub-install /dev/sda
```

Reboot. If you have issues, boot from the LiveDVD/USB again and run the command above from a terminal again. Reboot.

If still issues, Boot Repair is your friend:

[https://help.ubuntu.com/community/Boot-Repair#Getting_Boot-Repair](https://help.ubuntu.com/community/Boot-Repair#Getting_Boot-Repair)

Removing a Win install can be problematic, but never usually drastic. Just takes some tweaking sometimes. When you boot Win7 after the removal and other stuff getting it to boot again, you may need to run chkdsk manually or it may do it of its own accord. If it does, don't be alarmed. That is a good sign.

---

### Post by oldfred on 2014-07-17
I think it is best to move boot flag as that is the active partition with Windows. And that partition has the boot files for all Windows installs.

And move boot files from XP partition to Windows 7 partition and make sure you have your Windows 7 repairCD or flash drive handy to run Windows repairs.
Grub really only boots working Windows.

       Windows BIOS Boot files:
WinXP
/boot.ini /ntldr /NTDETECT.COM
Vista/7/8 (with 7or 8 the first two files are usually in a separate 100MB boot partition)
/bootmgr /Boot/BCD /Windows/System32/winload.exe 

      
 To get each MS to have its own boot loader make a second primary NTFS partition and set its boot flag on, then install the 2nd product in it. Multibooters, Pictures here worth 1000+ words - Vista but all Windows with BIOS/MBR
[http://www.multibooters.co.uk/articles/windows_seven.html](http://www.multibooters.co.uk/articles/windows_seven.html)
[http://www.multibooters.co.uk/multiboot.html](http://www.multibooters.co.uk/multiboot.html)
More tech info - BIOS boot process & some UEFI
[http://homepage.ntlworld.com./jonathan.deboynepollard/FGA/windows-nt-6-boot-process.html](http://homepage.ntlworld.com./jonathan.deboynepollard/FGA/windows-nt-6-boot-process.html)
BIOS/Grub/Ubuntu  boot process
[http://www.thegeekstuff.com/2011/02/linux-boot-process/](http://www.thegeekstuff.com/2011/02/linux-boot-process/)
A user who installed two windows & it worked to boot from grub directly
[http://ubuntuforums.org/showthread.php?t=1271600](http://ubuntuforums.org/showthread.php?t=1271600)

---

