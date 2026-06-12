---
title: "Help with boot-repair, please"
date: 2017-09-09
forum: Installation &amp; Upgrades
---

### Post by skamarla on 2017-09-09
Hello,

I have an Acer Swift 3, with dual boot Windows-Linux. After a BIOS update, I haven't been able to boot back into Linux. I have run boot-repair (last version) from the boot-repair rescue disk and it still keeps booting directly to Windows.

I have even tried to do the "bcdedit /set" thing that boot-repair recommends from Windows, to no avail.

The wifi driver didn't work directly in the boot repair disk, but I have posted the info here: [http://paste.ubuntu.com/25497932/](http://paste.ubuntu.com/25497932/)

Please help.

---

### Post by oldfred on 2017-09-09
When you updated the old BIOS all settings were reset to default. 
UEFI has NVRAM, but only may save some settings, so not sure if you need to redo some or not.
I document all changes I make in UEFI so I can be sure they are the same.

With Acer you have to enable a UEFI supervisory password and set "trust" on the Ubuntu/grub/shim boot files. You need to have one named device but two unnamed devices as shown by efibootmgr -v in script.

You have UEFI with the new NVMe SSD type drive.
You may want to turn off Secure Boot, but some say it needs to be on to set trust.

       Acer Trust Settings - details, some now report that then secure boot has to be on to set trust:
[https://ubuntuforums.org/showthread.php?t=2358003](https://ubuntuforums.org/showthread.php?t=2358003)
[https://ubuntuforums.org/showthread.php?t=2291335&p=13341757#post13341757](https://ubuntuforums.org/showthread.php?t=2291335&p=13341757#post13341757)
[https://ubuntuforums.org/showthread.php?t=2342323](https://ubuntuforums.org/showthread.php?t=2342323)
[http://ubuntuforums.org/showthread.php?t=2297947&p=13369742#post13369742](http://ubuntuforums.org/showthread.php?t=2297947&p=13369742#post13369742)
Acer Cloudbook shows screen for selecting trust
[http://bernaerts.dyndns.org/linux/74-ubuntu/340-ubuntu-install-acer-aspire-cloudbook-431](http://bernaerts.dyndns.org/linux/74-ubuntu/340-ubuntu-install-acer-aspire-cloudbook-431)
[http://community.acer.com/t5/Predator-Laptops/Dual-Boot-Ubuntu-Win10-Step-by-step-guide/m-p/430392#U430392](http://community.acer.com/t5/Predator-Laptops/Dual-Boot-Ubuntu-Win10-Step-by-step-guide/m-p/430392#U430392)

Windows 10 must also have fast start up off which is really just hibernation. 
But updates which may be in back ground also may turn it back on, so if grub does not boot Windows, directly boot with UEFI can turn off fast start up.


 Fast Start up off (always on hibernation)
[http://ubuntuforums.org/showthread.php?t=2324331&p=13488472#post13488472](http://ubuntuforums.org/showthread.php?t=2324331&p=13488472#post13488472)
[http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html](http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html)
[http://www.tenforums.com/tutorials/2859-hibernate-enable-disable-windows-10-a.html](http://www.tenforums.com/tutorials/2859-hibernate-enable-disable-windows-10-a.html)

---

### Post by skamarla on 2017-09-10
Thanks a lot!

I can confirm that the key is setting a supervisor password at the BIOS. I never disabled Secure Boot. 

As a matter of fact, boot-repair did warn that you had to set some files as secure in the BIOS, but I couldn't find the option. It's only available if you set the supervisor password.

What I did:
- first, run boot-repair
- back in Windows, press Shift while going through the restart menu. Keep holding shift, until you get a blue screen asking what you want to do. There select "solve problems", and "system configuration" (or so, I don't have it in front of me, and it wasn't in English anyway).
- in the "InsydeH20 Setup Utility", go to the Security tab and "Set Supervisor Password". Once set (you have to enter the new password twice, as usual, with a carriage return in between), you may "Select an UEFI file as trusted for executing". There, you get a primitive file browser. The first directory is EMMC, select it, then EFI, and then you get a few directories: in mine, ubuntu, OEM, Microsoft, Boot and Insyde. I selected ubuntu, and there I had shimx64.efi, grub64.efi and mmx64.efi ready for selection. I did the process twice, once for shimx64.efi (the file boot-repair had flagged as necessary) and once for grubx64.efi (because it's grub, what the hell).
- then, still in the Setup Utility, go to the Boot tab, and change the Boot priority order. Notice you have two new options (the EFI files I had just selected as secure). I set the top slot to the Grub file, Windows second.
- finally, F10, Save and Exit.

Now the PC boots to the grub screen and I can select Linux, Windows or whatever. Also, while booting, F2 works if you need to bring up the BIOS (but you have to give it the password you just set, of course).

Thanks a lot for your help!

---

### Post by oldfred on 2017-09-10
Glad you got it working.

With UEFI Secure Boot on, only the "shim" entry should work.
If you turn off Secure boot then either shim or grub should work.

---

