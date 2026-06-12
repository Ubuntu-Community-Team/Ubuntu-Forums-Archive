---
title: "Ubuntu 12.10 boot problems"
date: 2013-03-03
forum: Installation &amp; Upgrades
---

### Post by diemdma on 2013-03-03
I have a new Acer Predator that came with Windows 8 pre-installed -- I took out the hard drive it came with and installed a SSD in its place - I installed the 64bit version of Ubuntu 12.10 to the new SSD and for the life of me, I can not get Ubuntu to boot from this drive - I get a "Reboot and select proper boot device or insert boot media in selected..." error.


I tried to make adjustments as suggested on the following site: [https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI) with little to no success at all.


this is all a bit over my head - I hope the URL below contains all the information with which someone could help me troubleshoot this issue.


[http://paste.ubuntu.com/5582525/](http://paste.ubuntu.com/5582525/)


Any assistance would surely be appreciated!

---

### Post by darkod on 2013-03-03
If you took out the hdd and replaced it with a ssd, what is /dev/sdb? Does it has two disks?

Ubuntu looks installed correctly in uefi mode. But now you also have EFI system partition on sda, not just on sdb. Not sure if this is how it's supposed to be since I don't use uefi. I think there should be only one.

You might need to open some type of UEFI Boot manager in bios and make a new entry for ubuntu manually.

---

### Post by oldfred on 2013-03-03
Do you have secure boot on or off?
Some systems only let you into UEFI menu from Windows unless you turn off fast boot.
Did you install in UEFI or BIOS mode, and is UEFI still in that mode?

       Post the link to the BootInfo report that this creates. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)
Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration and diagnose advanced problems.
Install in Ubuntu liveCD or USB or Full RepairCD with Boot-Repair (for newer computers)

---

### Post by diemdma on 2013-03-03
Thank for your reply Darko - I've attached a screenshot of what my disk set up looks like in gparted.

[ATTACH=CONFIG]239707[/ATTACH][ATTACH=CONFIG]239706[/ATTACH]

---

### Post by diemdma on 2013-03-03
> **oldfred said:**
> Do you have secure boot on or off?
Some systems only let you into UEFI menu from Windows unless you turn off fast boot.
Did you install in UEFI or BIOS mode, and is UEFI still in that mode?

       Post the link to the BootInfo report that this creates. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)
Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration and diagnose advanced problems.
Install in Ubuntu liveCD or USB or Full RepairCD with Boot-Repair (for newer computers)

Thanks Oldfred!

Secure boot is on (Ubuntu doesn't load even if off)
fast boot is disabled
I installed in UEFI mode (I think) and it does say UEFI next to the hard drive I am trying to boot from.

screenshots of the BIOS: - sorry they are upside down

[ATTACH=CONFIG]239708[/ATTACH][ATTACH=CONFIG]239709[/ATTACH]

---

### Post by oldfred on 2013-03-03
Then under boot do you get the UEFI options of Boot, Windows & ubuntu?

Post link to BootInfo report.

---

### Post by diemdma on 2013-03-03
Hi Oldfred - 

I have it set to try to start up from the the SSD first, then the DVD drive, then the LAN -- I do not want to boot into Windows 8 at all - I am not looking to dual boot.

if I turn on the 'Boot Menu' option in the BIOS - I get the options:

UEFI: Samsung SSD 840 Series  <-- this is where I installed Ubuntu.
Windows Boot Manager
UEFI: ST2000DM001-1CH164 <-- this is where Windows 8 came preinstalled, I am using this as a secondary drive - it's in a hot-swap bay

when I select the 'UEFI: Samsung SSD 840 Series' option, I get the 'Reboot and Select proper Boot device or Insert Boot Meia in selected Boot device and press a key' error.

Here is my Boot Info Summary link:

[http://paste.ubuntu.com/5583191/](http://paste.ubuntu.com/5583191/)

thanks again

---

### Post by darkod on 2013-03-03
I'm not experienced with UEFI but I think there should be only one EFI partition with boot files. I see grub2 exists also on /dev/sdb2 which is the EFI partition on the other disk.

So, it doesn't matter that you are not trying to dual boot, have you tried booting from the hdd instead of the ssd? The UEFI files to boot seem to be there.

Even with the files there, you still might need to add an option for ubuntu manually if the UEFI manager didn't do it automatically. Don't forget, the OS is there but the boot manager might not know that.

---

### Post by oldfred on 2013-03-03
Boot Repair seems to think you boot from sdb2 or the Windows drive. It has added grub to that efi and your fstab show that efi's UUID. I think you want grub installed into sda1 not sdb2. Perhaps that is why booting from sda does not work?

Two drives with UEFI can get confusing. But some have made it work. But you may have to manually edit efi files and fstab.

       Installing Ubuntu 12.10 alongside Windows 8 on Asus K95V laptop HD/SSD (EFI) Two drives. Details in post #6
[http://ubuntuforums.org/showthread.php?t=2116610](http://ubuntuforums.org/showthread.php?t=2116610)
UEFI dual boot two drives - HP
[http://ubuntuforums.org/showthread.php?t=2072950](http://ubuntuforums.org/showthread.php?t=2072950)
UEFI dual boot two drives see #14 on how edit UUID to Windows efi partiton
[http://ubuntuforums.org/showthread.php?t=2031836](http://ubuntuforums.org/showthread.php?t=2031836)

---

### Post by diemdma on 2013-03-03
in an effort to un-confuse my boot options - i've removed the other drive entirely and ran Boot-Repair again.

now the SSD is the only option available - and it still doesn't want to boot into Ubuntu.

I get the error:
'Reboot and Select proper Boot device or Insert Boot Media in selected Boot device and press a key...'

here is the boot info summary:
[http://paste.ubuntu.com/5583925/](http://paste.ubuntu.com/5583925/)

I do appreciate all the advice - it would be great if I can get this up and running as i've planned; but some of the information provided is over my head -- I'll see if I can find more answers based on the advice given.

 I may ditch the SSD and try installing Ubuntu on the 2tb HDD in place of Windows 8 next.

if my latest Boot info URL sheds any more light on the subject, please let me know -- I've got to think that its something not all that complicated that I am just missing..

thanks again

---

### Post by oldfred on 2013-03-04
Some UEFI like yours dump some data:

>  BootOrder: 0009,000A,0000
Boot0000  Windows Boot Manager
Boot0009* UEFI: Samsung SSD 840 Series
Boot000A* UEFI: HL-DT-ST DVDRAM GH82N
BootCurrent: 000A
Timeout: 1 seconds
BootOrder: 0001,0009,000A,0000
Boot0000  Windows Boot Manager
Boot0009* UEFI: Samsung SSD 840 Series
Boot000A* UEFI: HL-DT-ST DVDRAM GH82N
Boot0001* ubuntu



It shows default on second list as 0001 or ubuntu, so why does it not boot ubuntu. But first list with 0009 seems to be the menu you are seeing. Or is there another menu or sub menu some where else in UEFI? Or is one secure boot on and the the off?

Beyond that, if your system is one that only boots Windows you can use boot repair to rename shim to the Windows file. Then UEFI thinks it is booting Windows when it is really booting Windows. Shim has Windows key so it works with secure boot.

 Boot-Repair - Updated Jan 1, 2013 to not rename first time, but rename if first time Windows does not boot. Post 706 and 711
[http://ubuntuforums.org/showthread.php?t=1769482&page=71](http://ubuntuforums.org/showthread.php?t=1769482&page=71)
 Boot-Repair copied /EFI/ubuntu/grubx64.efi to /EFI/Boot/bootx64.efi (in case the BIOS is hard-coded to boot into /EFI/Boot/bootx64.efi or secure boot
signed GRUB file shimx64.efi.

---

