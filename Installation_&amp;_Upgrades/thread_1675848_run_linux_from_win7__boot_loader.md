---
title: "run linux from win7  boot loader?"
date: 2011-01-26
forum: Installation &amp; Upgrades
---

### Post by ulao on 2011-01-26
Is this possible? I have to Install linux on a drive in the wrong channel. I just want to install it on a drive, put my drives back the way I need them and boot to this drive from win7 boot loader and not use grub? Or how can I edit the grub one I'm done and point to the right disc.

Is there a way to install umbuntu to the super node of the partition rather then the MBR

---

### Post by sikander3786 on 2011-01-26
There is a Windows based bootloader for Linux called EasyBCD.

[http://neosmart.net/dl.php?id=1](http://neosmart.net/dl.php?id=1)

I couldn't fully understand your current situation. How are you planning to install, what is going to be installed and where? Do you plan not to install Grub or is it installed already?

It would be very helpful if you could boot an Ubuntu Live CD/USB and post the output of bootinfoscript as per instructions here.

[http://bootinfoscript.sourceforge.net](http://bootinfoscript.sourceforge.net)

It would let us dig deep in your problem and thus, we'll be able to offer a better solution.

---

### Post by Grenage on 2011-01-26
> **ulao said:**
> Is this possible? I have to Install linux on a drive in the wrong channel. I just want to install it on a drive, put my drives back the way I need them and boot to this drive from win7 boot loader and not use grub? Or how can I edit the grub one I'm done and point to the right disc.

Is there a way to install umbuntu to the super node of the partition rather then the MBR

I suppose that if you have one drive with Windows installed on it, then you install Linux on *another* drive, you could install grub on that *other* drive.  Grub could point to both the Windows and Linux installations, and you would make that *other* drive the boot choice in the BIOS.

Should you change your mind and remove the second drive, the old bootloader info would still be there or the first drive.

---

### Post by ajgreeny on 2011-01-26
Yes I agree that you should run the boot-info-script, but I would also ask before we get the printout from that, do you have just one disk or more than one?  I am not talking about partitions on a single disk, but separate hard disks.

If you have more than one disk and can quickly swap between them at boot time with the press of a key, eg F8, you may be able to leave the windows bootloader files untouched on disk 1 and put grub for ubuntu on disk 2.

I'll await the RESULTS.txt printout before telling you any more.

---

### Post by ulao on 2011-01-26
Thx for the suggestions just one to try this first. Maybe its pointless. 

Sort of like Grenage was saying but with the win7 loader instead. I'm told I can do something like this

  [boot loader] 
     timeout=30 
     default=multi(0)disk(0)rdisk(0)partition(1)\WINNT 
     [operating systems] 
     multi(0)disk(0)rdisk(0)partition(1)\WINNT="Microsoft Windows 2000 Professional" /fastdetect 
     c:\boot.lnx="Puppy Linux" 

from my win loader. I know how to edit it, but a bit confused how to point it to my linux partition. I installed the kumbuntu with the advanced grub option and told it to put the grub on my kumbuntu partition. Assuming windows boot will see it as e:\ or somthing what would  the file name be?

BTW: my boot loader is win7's boot loader and win7 is rather stubborn about using it. I want to ovoid the menu to menu thing. Just one menu all 4 OS's ( win764, xp, xp64, linux )  Each on there own drive. I have all but linux so for. If linux needs the grub I can live with that but want to load the grub from the win boot if possible.

---

### Post by ulao on 2011-01-26
Ok looks like the install just installed the entire grub to the Kumbuntu partition. I tried to boot to it via win7 boot with no grub option. It looked for a file and report it was not found. So I then tried to boot to that drive assuming there was a grub installed and it just restart the system. I guess there system didnt like that?

So back to the none grub I see this in the win boot
\NST\AutoNeoGrub.mbr 

Does that hold any meaning to anyone?

Ok here is the entire boot layout

Default: Windows 7
Timeout: 5 seconds
Boot Drive: D:\

Entry #1
Name: Windows 7
BCD ID: {current}
Drive: C:\
Bootloader Path: \Windows\system32\winload.exe

Entry #2
Name: XP 32
BCD ID: {8e1e0512-5458-11d7-84d4-fbb3b78929e8}
Drive: D:\
Bootloader Path: \NST\easyldr1

Entry #3
Name: XP 64
BCD ID: {8e1e0513-5458-11d7-84d4-fbb3b78929e8}
Drive: D:\
Bootloader Path: \NST\easyldr2

Entry #4
Name: kumbuntu
BCD ID: {8e1e0518-5458-11d7-84d4-fbb3b78929e8}
Drive: D:\
Bootloader Path: \NST\AutoNeoGrub0.mbr


**Ahh got it with grub2 see entry 4;)**

---

