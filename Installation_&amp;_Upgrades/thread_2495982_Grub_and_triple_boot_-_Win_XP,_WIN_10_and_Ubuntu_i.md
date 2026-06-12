---
title: "Grub and triple boot - Win XP, WIN 10 and Ubuntu issue"
date: 2024-03-10
forum: Installation &amp; Upgrades
---

### Post by tomtomek on 2024-03-10
Hi guys,

So I have been using Grub with dual boot setup for Win 10 and Ubuntu for quite some time. Due to some legacy reasons I needed Win XP installation and therefore I decided to install XP on an un-allocated space on my HDD. Once done I was able to boot to it without issues. Obviously Grub stopped working. If I use the Boot-Repair ISO, I can get back Grub but only Ubuntu works. Both Windows 10 and Win XP come up with an error when booting. When booting off Win 10 install USB I can fix the BCD and get Win 10 to boot, but then WinXP still errors out. If I reinstall XP, then only XP boots and WIN10/Ubuntu are not 'visible. How can I fix this? I will paste the boot-info details in a minute once I can upload them from boot-repair procedure. Your help is much appreciated.


EDIT: Boot info:

[https://*******.us/AhK7kA](https://*******.us/AhK7kA)

Not sure how can I paste the boot info link here.

Regards,
Tom

---

### Post by oldfred on 2024-03-10
Not a valid site.
You have a word that is in the Forum's list of words not allowed in US.
Boot-Repair suggests using pastebin which we prefer.

You have old BIOS/MBR configuraiton.
Windows normally updates BCD to dual boot two Windows, but then you only have one grub entry.
Windows XP NTFS partition must have a XP type NTFS boot sector that calls out ntldr & Windows 10 requires an updated NTFS that calls out bootmgr.

I once ran Windows 7 chkdsk on my XP, when XP's chkdsk would not fix it. But it converted it to Windows 7 that also used bootmgr. Only figured out issue with testdisk and detail dump of boot sectors. 

BIOS/Grub/Ubuntu  boot process
[http://www.thegeekstuff.com/2011/02/linux-boot-process/](http://www.thegeekstuff.com/2011/02/linux-boot-process/)
A user who installed two windows & it worked to boot from grub directly
[http://ubuntuforums.org/showthread.php?t=1271600](http://ubuntuforums.org/showthread.php?t=1271600)
Another user who disconnected and used a second drive 
[http://ubuntuforums.org/showthread.php?t=1334346](http://ubuntuforums.org/showthread.php?t=1334346)

Because of old MBR and then only having one place for BIOS to start boot, you need both Ubuntu live installer & Windows repair flash drives.
When Windows breaks, you may need to restore Windows boot loader to MBR, fix Windows, and then use live installer to restore grub.
New systems since 2012 and release of Windows 8 use UEFI with gpt partitioning. Windows requires MBR for BIOS boot and gpt for UEFI boot. But with UEFI you can have multiple boot loader all installed at once.

---

### Post by tomtomek on 2024-03-10
Hi, I used boot-repair which provided this link. Nevertheless, I have uploaded it to paste bin now: [https://pastebin.com/9Er4QDWi](https://pastebin.com/9Er4QDWi) does this provide any more insight?

---

### Post by MAFoElffen on 2024-03-10
I was thinking about letting others answer before blurting something out about Windows Boot Manager in /dev/sda1... But why not, right?

I'm thinking that installing Windows XP after a pre-existing install of Win 10 overwrote the Windows Boot Configuration Data (BCD) store for BIOS-based... And if you repair that to include Win10, then it might be fine. The reason I suspect that, is that Win 10 did not exist when XP was out. To Win 10, XP, Vista and Win 7, 8.x were legacy... No that they supported direct release updates over multiple version steps, but still...

Albeit, it is an MS-DOS partition type drive in Legacy Boot mode, running Win 10, which the normal, most popular boot method for Win 10 is UEFI. But Win 10 still boots from legacy through the BCD store database.

Note that get good backups first. Repairing the BCD there is going to boink Grub2 again (because Windows has an Ego), and will need to be repaired again after that.

At least that is what I see and suspect. oldfred might see something else. As i remember he has had other experiences with that.

---

### Post by tomtomek on 2024-03-11
I repaired the BCD from within the Windows 10 boot disk and I can now boot to Windows 10 but I do not see an option to boot to Windows XP. Grub is broken now obviously. I have also used EasyBCD but this did not fix things and even made them worse. So now I am booting to Win 10 but not able to boot to XP nor Ubuntu. Any suggestions on next steps?

---

### Post by yancek on 2024-03-11
Windows bootloaders are backward compatible so that installing a Legacy windows 10 with an already installed Legacy version of Xp should have worked to boot both.  Installing XP after windows 10 was pointless and would never work.

sda2 has the windows 10 boot files while sda3 has the XP boot files.  sda1 has both and that isn't right.  sda1 also shows as a recovery windows partition which it may have been for windows 10.   

The simplest option you could have used would have been to have XP installed in a virtual machine on either Ubuntu or windows.  I don't know what your sda1 partition is so that could be a problem.  You might try putting  entries in the grub.cfg file on Ubuntu shown in the examples for both XP and windows 10 at the site from the link below.  Put those entries in the /boot/grub/grub.cfg file and save the changes.  Do NOT update-grub, just reboot to test.  If they don't work, you will need to reinstall both XP (first) and then windows 10 and try to figure out exactly what sda1 is and why it has boot files for both XP and windows 10.

[https://wiki.gentoo.org/wiki/GRUB/Chainloading](https://wiki.gentoo.org/wiki/GRUB/Chainloading)

---

### Post by oldfred on 2024-03-11
You may need to run Windows XP chkdsk on XP and Windows 10 chkdsk on Windows 10 to fix the bootsector.

Windows BIOS Boot files:
WinXP
/boot.ini /ntldr /NTDETECT.COM
Vista/7/8/10 BIOS (with 7, 8 or 10 the first two files are usually in a separate 100MB boot partition)
/bootmgr /Boot/BCD /Windows/System32/winload.exe 

Windows 10 would have had a boot partition with boot files. Did you move boot flag to new XP partition when you installed it, to keep its boot files in its partition. And move boot flag back. Then update Windows 10 to add Windows XP to its BCD?

Windows 10 does not have to have separate boot partition, but then all boot files must be in the one partition with boot flag.

Grub does not use boot flag. If when you install or repair each Windows so it has all its boot files in one partition, or XP's files in XP, then grub can directly boot both Windows. Windows only boots from partition with boot flag and that BCD would have to have both entries.

To get each MS to have its own boot loader make a primary NTFS partition and set its boot flag on, then install the 2nd product in it. Multibooters, Pictures here worth 1000+ words Older Windows but same for all BIOS versions.
[http://www.multibooters.co.uk/multiboot.html](http://www.multibooters.co.uk/multiboot.html)
[http://www.multibooters.com/guides/visual-guide-to-the-boot-sequence.html](http://www.multibooters.com/guides/visual-guide-to-the-boot-sequence.html)

---

### Post by tomtomek on 2024-03-11
> **oldfred said:**
> You may need to run Windows XP chkdsk on XP and Windows 10 chkdsk on Windows 10 to fix the bootsector.

Windows BIOS Boot files:
WinXP
/boot.ini /ntldr /NTDETECT.COM
Vista/7/8/10 BIOS (with 7, 8 or 10 the first two files are usually in a separate 100MB boot partition)
/bootmgr /Boot/BCD /Windows/System32/winload.exe 

Windows 10 would have had a boot partition with boot files. Did you move boot flag to new XP partition when you installed it, to keep its boot files in its partition. And move boot flag back. Then update Windows 10 to add Windows XP to its BCD?

Windows 10 does not have to have separate boot partition, but then all boot files must be in the one partition with boot flag.

Grub does not use boot flag. If when you install or repair each Windows so it has all its boot files in one partition, or XP's files in XP, then grub can directly boot both Windows. Windows only boots from partition with boot flag and that BCD would have to have both entries.

To get each MS to have its own boot loader make a primary NTFS partition and set its boot flag on, then install the 2nd product in it. Multibooters, Pictures here worth 1000+ words Older Windows but same for all BIOS versions.
[http://www.multibooters.co.uk/multiboot.html](http://www.multibooters.co.uk/multiboot.html)
[http://www.multibooters.com/guides/visual-guide-to-the-boot-sequence.html](http://www.multibooters.com/guides/visual-guide-to-the-boot-sequence.html)

I have now managed to boot to Windows 10 but I do not have an option to boot to XP anymore, I would have to try to reinstall it, which will then overwrite the windows 10 boot loader.

Can I try to run check disk for XP from Win XP Recovery, pointing at the local disk?

I did not move any boot flags, I suspect the boot flag is set for System Reserved first partition. Shall I reinstall the XP and then maybe use Gparted to change the boot flag to System reserved partition? Now in Windows 10 I have assigned a letter to this reserved partition and I can see the following files and directories there: [https://www.pastebin.com/Qc7Gnmrg](https://www.pastebin.com/Qc7Gnmrg)

Will check the referenced links in a minute. Thank you!

EDIT: Just skimmed through the pages you referenced, wow! This is very useful! thank you. now need to get my head round this and try to set this correctly.

---

### Post by MAFoElffen on 2024-03-11
Since you are thinking about reinstalling XP... I don't know your use case but...

Why not install it as a VM Guest within either Windows Hyper-V or Ubuntu with KVM?

XP has been EOS since April 14th 2014... To give a perspective, that would be like running Ubuntu Hardy Heron 8.04. It would be safer and more protected within a VM.

---

### Post by tomtomek on 2024-03-11
I need XP for legacy car diagnostic software, which uses rs232, best would be native to the host but may try to do it via VirtualBox or something similar.

---

### Post by oldfred on 2024-03-11
If you reinstall XP, move boot flag first. Install will put XP's boot loader in MBR and find boot flag to boot XP.
Then move it back and run Windows 10 repairs, that will put Windows 10's boot loader in MBR & allow it to boot.

Then you should be able to run grub repairs to put it into MBR and multiple boot.

Only use XP to fix XP partition & only use Windows 10 to repair its partition(s).
Partition Boot sectors are different between XP & later versions, so chkdsk from other install may convert it and break install.

Grub does not use boot flag & jumps to partition boot sector which loads the Windows boot files.

---

### Post by tomtomek on 2024-03-11
So I understand this correctly:
1 Just now I have Win 10 booting fine.
2. I shall reinstall XP, boot to it and then change boot flag to Win 10 partition.
3. Once done I shall boot to Win 10 and run checkdisk.
4. Once I can boot to Windows 10 I shall run grub to redo the multiboot.

is this correct? Thank you.

---

### Post by yancek on 2024-03-12
Reading the post by oldfred, I would think that you would need to mark the XP partition as 'boot' or 'active' before reinstalling it then reboot to verify it works.  Then change the windows 10 partition to 'boot' or 'active' and use the windows 10 repair disk to fix windows 10, the boot code to the MBR.  Reboot to test, run chkdsk and leave the windows 10 partition marked as 'boot' or 'active' partition.  If this works, boot your Ubuntu and update Grub.

---

### Post by tomtomek on 2024-03-13
Thank you! I have set the boot flag to XP partition and reinstalled the OS. It boiots fine now. I will continue with next steps tomorrow and report back, just need to use XP in the morning for car diagnostics, before I break it again :)

Cheers!

---

### Post by MAFoElffen on 2024-03-14
The easiest to use as a VM, if it uses RS232, would be to use a USB/RS232 serial adapter.

I ran into the opposite, were as my paid car diagnostics programs and my chip uploader programs upgraded from XP/Vista to newer Windows... When that happened, it forced me to upgrade the OS.

---

### Post by tomtomek on 2024-03-14
Update:
SUCCESS, SUCCESS, SUCCESS!

Thank you all for your help, especially big thanks to oldfred for providing the steps to fix this and also to yancek for clearing up the approach for me. I have now a Triple boot system and all systems are booting fine via Grub.

Have a great day everyone. Thread can be closed.

---

