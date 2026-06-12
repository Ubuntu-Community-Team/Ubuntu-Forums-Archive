---
title: "***SOLVED *** Dual Boot Windows 10 with Ubuntu no grub"
date: 2016-07-30
forum: Installation &amp; Upgrades
---

### Post by rickhunt on 2016-07-30
Hello, trying to dual boot Windows 10 and Ubuntu,

 I have read several posts and tried several things and no matter what I do, it boots windows 10 every time.

The only way I can get it to go to Ubuntu is to hold down F12 while powering on, then I get an option to start:

Windows Boot Manager
ubuntu
ubuntu

if I choose ubuntu, then it goes to Grub.  I want to start Ubuntu by default and have the option to choose Windows 10 and I dont want to have to press F12 every time.

I have tried "Boot Repair Disk", I have tried rEFInd, and I even tried "EasyUEFI" for Windows.

I read somewhere that Lenovo has a bug that it will only load a boot manager if it is named "Windows Boot Manager" or "Red Hat Enterprise Linux", even tried renaming them...still goes in to Windows with no option to choose anything else.

From Windows, I go to where you can set default operating system and Windows is the only option.

Computer is the Lenovo H30, I picked it up as a spare computer to play with, thought I would try dual booting...thinking that wasn't a good idea, because I am totally frustrated now.

Wouldnt be so bad if I had to press F12 to get to Windows, but I want Ubuntu to start by default without having to press a bunch of keys to get to it.

I am new to the whole UEFI stuff, this is the first computer I have had with UEFI.Secure Boot is disabled and it is set to boot UEFI and not legacy...I dont know what else to try.

Hopefully someone can point me in the right direction.Let me know what to check and I will post the output here.

Thanks
Rick

---

### Post by rickhunt on 2016-07-30
Ooops, it ran everything together with no line breaks the first time, had to edit. :-)

---

### Post by ubfan1 on 2016-07-30
From Ubuntu, run sudo efibootmgr -v to see the boot order, then you may change the order to what you want with efibootmgr, see instructions from the man pages: man efibootmgr.

---

### Post by rickhunt on 2016-07-30
Ok...I will try that when I get back home..I had to walk away for a while...spent hours messing with it and.not getting anywhere. Lol

---

### Post by rickhunt on 2016-07-31
Ok, so I tried once already to set boot order and Windows still loaded with no option...but I have 2 ubuntu entries and not sure which one I should set to default...last time I booted the current was number 6, this time the current is number 1 so here is what I did....I am gonna try and restart...but I am betting Windows 10 will still load without any options unless I press F12 at power on...that is the only way to get any options...but we'll see.

This shows what it was and what I changed it to

BootCurrent: 0001
Timeout: 0 seconds
BootOrder: 0000,0001,0006,0004,0005
Boot0000* Windows Boot Manager    HD(1,GPT,61dfd980-6863-40eb-ab97-4192328daa20,0x800,0x82000)/File(\EFI\MICROSOFT\BOOT\BOOTMGFW.EFI)WINDOWS.........x...B.C.D.O.B.J.E.C.T.=.{.9.d.e.a.8.6.2.c.-.5.c.d.d.-.4.e.7.0.-.a.c.c.1.-.f.3.2.b.3.4.4.d.4.7.9.5.}....................
Boot0001* ubuntu    HD(1,GPT,61dfd980-6863-40eb-ab97-4192328daa20,0x800,0x82000)/File(\EFI\UBUNTU\SHIMX64.EFI)
Boot0004* Generic Usb Device    VenHw(99e275e7-75a0-4b37-a2e6-c5385e6c00cb)
Boot0005* CD/DVD Device    VenHw(99e275e7-75a0-4b37-a2e6-c5385e6c00cb)
Boot0006* ubuntu    HD(1,GPT,61dfd980-6863-40eb-ab97-4192328daa20,0x800,0x82000)/File(\EFI\UBUNTU\GRUBX64.EFI)..BO
rick@rick-Lenovo-H30-05:~$ sudo efibootmgr -o 0001,0000,0006,0004,0005
BootCurrent: 0001
Timeout: 0 seconds
BootOrder: 0001,0000,0006,0004,0005
Boot0000* Windows Boot Manager
Boot0001* ubuntu
Boot0004* Generic Usb Device
Boot0005* CD/DVD Device
Boot0006* ubuntu

---

### Post by rickhunt on 2016-07-31
Tried to reboot....and went right in to windows...restarted again pressing F12 and selecting ubuntu and you can see, it changed the order again.

rick@rick-Lenovo-H30-05:~$ sudo efibootmgr -v
[sudo] password for rick: 
BootCurrent: 0001
Timeout: 0 seconds
BootOrder: 0000,0001,0006,0004,0005
Boot0000* Windows Boot Manager    HD(1,GPT,61dfd980-6863-40eb-ab97-4192328daa20,0x800,0x82000)/File(\EFI\MICROSOFT\BOOT\BOOTMGFW.EFI)WINDOWS.........x...B.C.D.O.B.J.E.C.T.=.{.9.d.e.a.8.6.2.c.-.5.c.d.d.-.4.e.7.0.-.a.c.c.1.-.f.3.2.b.3.4.4.d.4.7.9.5.}....................
Boot0001* ubuntu    HD(1,GPT,61dfd980-6863-40eb-ab97-4192328daa20,0x800,0x82000)/File(\EFI\UBUNTU\SHIMX64.EFI)
Boot0004* Generic Usb Device    VenHw(99e275e7-75a0-4b37-a2e6-c5385e6c00cb)
Boot0005* CD/DVD Device    VenHw(99e275e7-75a0-4b37-a2e6-c5385e6c00cb)
Boot0006* ubuntu    HD(1,GPT,61dfd980-6863-40eb-ab97-4192328daa20,0x800,0x82000)/File(\EFI\UBUNTU\GRUBX64.EFI)..BO

Now I am wondering about what I read that says there is a glitch with Lenovo where it will only accept a boot loader if it is named Windows Boot Manager or Red Hat Enterprise Linux...I am sure I can probably use efibootmgr to rename the ubuntu entry. Not gonna try any more tonight...have to work in the morning.

---

### Post by oldfred on 2016-07-31
Some Lenovo's have a locked boot order setting in UEFI, so efibootmgr does not work.

Only those not booting Windows should rename the Ubuntu entry to Windows.
UEFI has a fallback or hard drive boot entry. Yours does not show that entry in UEFI, yet, some systems have it by default.
In the ESP - efi system partition it is /EFI/Boot/bootx64.efi and usually is just a copy of Windows .efi boot file. But we can make it copy of shim instead.

Boot-Repair now creates  bkpbootx64.efi and copies shimx64.efi as bootx64.efi. This is a hard drive default or fallback boot entry in UEFI.      'Use the standard EFI file' in advanced options.
 [https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

Also 
Windows BCD syncs with UEFI entries. That may be why your boot order keeps getting reset. 

 Lenovo rename files
[http://ubuntuforums.org/showthread.php?t=2302170](http://ubuntuforums.org/showthread.php?t=2302170) 
      
 Lenovo Thinkpad E531 - turn off locked boot order setting in UEFI
[http://ubuntuforums.org/showthread.php?t=2255746](http://ubuntuforums.org/showthread.php?t=2255746)

---

### Post by rickhunt on 2016-08-01
Solved....I feel like an idiot...it was super simple...I was missing the "Startup sequence" in the actual bios...Duh...new computer for me, new Bios layout...I thought the boot order was controlled at a windows or linux level only...had no idea I could set it in the BIOS. Working fine now...just had to move Ubuntu to the top in the actual bios.

I found it by mistake...I was trying to boot up a USB stick and it didn't work, so I went in to Bios to enable Compatibility Support for legacy OS and I didnt arrow down far enough and clicked on Boot Sequence by mistake and it was staring me in the face...I though OMG...REALLY. Haha..I will mark this thread solved...thanks to all.

---

### Post by Bucky Ball on 2016-08-01
Thanks for marking as solved in the title, but could you also do it using the Thread Tools function at the top right of the page or follow the instructions in my signature, please? Cheers. :)

If we don't make mistakes, we don't learn much, so you're in good company here! Part of being humanoid. :)

---

### Post by rickhunt on 2016-08-01
Only issue I have now...is the clock in Windows and Ubuntu dont match...haha...should be an easy fix...My hardware clock is probably set to UTC and windows is probably local time...I will figure that out now that its boot properly :-)

---

### Post by rickhunt on 2016-08-01
done...used Thread Tools to indicate it was solved.

---

### Post by Bucky Ball on 2016-08-01
:) This will help others. Thanks.

---

