---
title: "cannot boot into Windows 8.1 after boot-repair"
date: 2015-03-18
forum: Installation &amp; Upgrades
---

### Post by daytonajohn2 on 2015-03-18
I installed Ubuntu 14.10 alongside Windows 8.1 on a new HP envy, and was surprised at how smoothly it went after reading so many horror stories. After installation, the boot menu showed both WIndows 8.1 and Ubuntu and both worked fine. Then my troubles began. I do some work using Android Studio, which performs better if virtualization is enabled in the BIOS, so I enabled it (making no other changes). On next reboot, I could not boot into Ubuntu, only Windows 8.1.  I found that I could get to Ubuntu through the BIOS "boot device selection". I googled a bit and learned about boot-repair and EascyBCD. I tried boot-repair, but it didn't make any difference, so I tried EasyBCD, and that also made no improvement. After a bit more research, I saw recommendations that I should re-run EasyBCD to restore the backup I had made. After doing that I could not access Windows at all. On power-up I get the "Windows failed to start" message from the Windows Boot Manager (no oppurtuniity to select an OS). I can still get into Ubuntu via the BIOS "boot device selection", but even if I select Windows in the "boot device selection", I get the same "Windows failed to start" message. The Windows Boot Manager window on the failure says:
   File: \BCD
   status: 0xc0000098
   BCD does not contain valid information
I ran boot-repair again, but it made no difference. Here is the pastebin URL: [http://paste.ubuntu.com/10624407](http://paste.ubuntu.com/10624407)
So, I can get into Ubuntu through the BIOS, but I can't boot windows at all. Any idea how I can get this fixed???  Thanks for any help!!!

---

### Post by oldfred on 2015-03-19
You really need your Windows repair flash drive or any Windows install with the repair/recovery tools.
From Linux you cannot fix/repair BCD. You may be able to use EasyBCD or Windows own BCDedit to fix BCD issues.

With UEFI best not to use EasyBCD as a boot manager, but some use it to make repairs.

Were you able to directly boot both Ubuntu & Windows from UEFI boot menu without any issue? If so you are the first HP user that has not had to do a work around to make it work.
What model HP Envy?

Boot-Repair should not normally be required with new installs. It used to be that grub could not correctly find correct UEFI Windows boot entry and many systems only boot the Windows efi file by description. Vendors modify UEFI to look for correct Windows decription which is not per UEFI.

But Boot-Repair is good for its summary report and sometimes for repairs.

But with HP, they have many HP efi files in the efi folder and Boot-Repair creates grub boot entries for all of them. You may later want to house clean out some or all of them.

Grub only boots working Windows, so best to have the Windows repair flash drive. Not sure but if you directly boot Windows from UEFI menu, does the f8 key get you into a repair console?

 HP Envy 700-430QE desktop used bcdedit to dual boot
[http://ubuntuforums.org/showthread.php?t=2260681](http://ubuntuforums.org/showthread.php?t=2260681)
Boot Ubuntu 14.04 LTS 64-bits on external hdd - HP Envy 17 w/Windows 8.1 Details
[http://ubuntuforums.org/showthread.php?t=2256244](http://ubuntuforums.org/showthread.php?t=2256244)
HP to get into UEFI/BIOS menu - escape then f10 as soon as it starts.
[http://h10025.www1.hp.com/ewfrf/wc/document?docname=c01443329&lc=en&cc=us&dlc=en&product=5171079](http://h10025.www1.hp.com/ewfrf/wc/document?docname=c01443329&lc=en&cc=us&dlc=en&product=5171079)

      
 Windows 8 UEFI fixes
[http://superuser.com/questions/460762/how-can-i-repair-the-windows-8-efi-bootloader](http://superuser.com/questions/460762/how-can-i-repair-the-windows-8-efi-bootloader)
Repair Windows 8 boot issues & repair CD or flash
[http://ubuntuforums.org/showthread.php?t=2105418](http://ubuntuforums.org/showthread.php?t=2105418)
[http://www.eightforums.com/tutorials/2855-system-repair-disc-create-windows-8-a.html](http://www.eightforums.com/tutorials/2855-system-repair-disc-create-windows-8-a.html)

---

### Post by daytonajohn2 on 2015-03-19
My laptop is an HP Envy m7-211dx. I used windows to shrink the windows partition, and then created root, swap, and home parititions during the Ubuntu 14.10 install (from the live CD). And yes, the dual boot worked fine for several days. On power-up, entries for both Windows and Ubuntu showed up, and both worked fine. I did not make ANY changes to the BIOS for the installation. Somehow, when I enabled virtualization in the BIOS, something else must have gotten changed, cause it all went bad after that.

This morning, I booted into Windows Recovery, got into a console, and used "bootrec /RebuildBcd" to fix the Windows BCD. Now the machine boots directly into Windows. Luckily, the "boot device" option in the BIOS still lets me get into Ubuntu. I got into Ubuntu and tried "boot-repair" again, hoping it woud add Ubuntu to the boot menu, but no luck. It did not appear to change anything, and it still boots directly into Windows. So next I tried EasyBCD again, and just set the Ubuntu shimx64.efi as the default. Now I see both Windows and Ubuntu on the boot menu. Selecting Windows works fine, but selecting Ubuntu gives me the now familiar "Windows failed to start" and "required file is missing or contins errors". I guess I can live with it like this (I will redo the "bootrec /RebuildBcd"), and my Ubuntu installation will be sort of a secret OS :p. If anyone has any ideas, please let me know.

Thanks for your reply oldfred. You are right about the HP boot entries. When I select Ubuntu in the BIOS "boot device" selection, I get a menu with nearly a full page of entries. By the way, on this machine, ESC after power-on gets me to a BIOS menu, with options like "Boot device", "BIOS settings", "Windows Recovery", and some others. So it is easy to get to the Windows Recovery. The "Boot device" option is F9. I will look at the threads you referenced to see if I can find a solution.

Thanks again!!!

---

### Post by oldfred on 2015-03-19
Not sure what menus you are seeing.
UEFI has a boot menu or boot manager. That should let you directly boot Windows or Ubuntu.
EasyBCD converts the BCD to a Boot manager. Windows normally only boots Windows.
Grub is both a boot manager & boot loader for Linux. And running Boot-Repair added many entries to that grub menu.

So with EasyBCD you end up with another menu and already have two.

---

### Post by daytonajohn2 on 2015-03-19
Thanks for your help oldfred. I think I will just leave my system as is. It appears that Windows is likely to undo any changes I make, so at least the current state is stable and I can get to both Windowws and Ubuntu.

---

### Post by daytonajohn2 on 2015-03-22
OK, so I didn't leave it as is :p. I noticed an entry under "BIOS Setup", under the "System Configuration" tab, under "Boot Options", under "UEFI Boot Order" entitled "OS boot Manager". This let me select the boot manager to load on power up. It showed two choices, Windows and Ubuntu. I changed it from Windows to Ubuntu. Now, power up takes me directly to the Ubuntu grub menu, where I can select Ubuntu or Windows, and all works nicely. Hoping that WIndows will not change this setting. I also deleted the "25_custom" (generated by boot-repair?) file from /etc/grub.d and ran "update-grub" to get a nice, clean, simple boot menu. In Windows, I also used bcdedit to restore the backup I had made early on. This resulted in a Windows BCD with only one entry, so when I select Windows in the grub menu, it boots into Windows without showing me another menu.

Thanks again for your help, oldfred. Your posts helped me understand what is going on a bit better, and gave me the confidence to tackle the problem.

---

### Post by oldfred on 2015-03-22
Glad you got it working.

It still is a good idea to backup efi partition and of course Windows & /home in Ubuntu.
And have both a current version repair flash drive for every system you have installed. Your Ubuntu live install works for that, but you have to separately create a repair disk for Windows.

---

