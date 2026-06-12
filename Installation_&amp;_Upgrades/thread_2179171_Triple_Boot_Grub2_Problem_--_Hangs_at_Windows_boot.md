---
title: "Triple Boot Grub2 Problem -- Hangs at Windows bootloader"
date: 2013-10-06
forum: Installation &amp; Upgrades
---

### Post by joeltrane on 2013-10-06
Hello,

Thank you very much for looking, I am having trouble getting windows to boot on my HP laptop. I have these operating systems installed on the computer: Windows 8, Ubuntu 13.10, Linux Mint 15 (Cinnamon). I reinstalled Windows 8 from HP recovery partition, then installed Mint followed by Ubuntu (after creating the appropriate partitions). I then attempted to chain load the linux partitions by following this tutorial that I found: [http://apcmag.com/how-to-dual-boot-windows-8-and-linux.htm](http://apcmag.com/how-to-dual-boot-windows-8-and-linux.htm)

That did not end so well as I did not get the same GUI as in the tutorial. At that point I could still boot the computer to GRUB2 and then select 'WINDOWS UEFI'. Upon selecting this I would be sent to the Windows Bootloader which presented me with these three selections: 

"Windows 8"
Linux Mint 15 Olivia
Ubuntu 13.10 Saucy

Which is what I had specified in EASYBCD while going through the above mentioned tutorial. The problem was, at this point I was left with a very sloppy windows 8 boot procedure. After deciding to just stick with the good ol' GRUB2, I went back into EasyBCD while in windows and try to remove the entries. Among the options I selected I am sure it was [Reset BCD configuration]("https://farm5.static.flickr.com/4080/4782813896_30dbaa6976.jpg") that caused the problem where I am at now.

When I boot up currently I am presented with an error in the Windows Bootloader that says I need to insert the media to repair it. I can still boot into Ubuntu and Mint by pressing f9 and selecting Ubuntu(Hitachi 12345....whatever comes next). This is where I am still presented with GRUB2 in order to boot.

 I do not have an disk image to restore windows and I cannot access the HP recovery drive for some reason it says the drive is locked. I was hoping there was a way to repair the Windows Bootloader so I can simply access windows from it.

I would be super grateful if someone could help me restore my MBR and get Windows running again.

Here are the results from my boot repair attempt:

Boot successfully repaired.

Please write on a paper the following URL:
[http://paste.ubuntu.com/6203303/](http://paste.ubuntu.com/6203303/)

In case you still experience boot problem, indicate this URL to:
[email]boot.repair@gmail.com[/email] or to your favorite support forum.

You can now reboot your computer.
Please do not forget to make your BIOS boot on sda (750GB) disk!

The boot files of [The OS now in use - Ubuntu Saucy Salamander (development branch)] are far from the start of the disk. Your BIOS may not detect them. You may want to retry after creating a /boot partition (EXT4, >200MB, start of the disk). This can be performed via tools such as gParted. Then select this partition via the [Separate /boot partition:] option of [Boot Repair]. ([https://help.ubuntu.com/community/BootPartition](https://help.ubuntu.com/community/BootPartition))


Regards,
Joel

---

### Post by joeltrane on 2013-10-07
Hey,

I just thought of something, could marking the windows 8 partition to boot with priority have caused this? Before I would default to grub and as I have stated earlier, now I boot to windows bootloader.

I think I need to try booting into windows from disc and then trying to use Easy BCD one more time to make grub2 in ubunut my default bootloader.

What do you think?

- Joeltrane

---

### Post by oldfred on 2013-10-07
You have an UEFI system. You do not need EasyBCD.
You do show a bios_grub partition which is required to boot grub2 in BIOS mode. But it looks like Boot-Repair added a Windows boot loader to the MBR.
You have to consistently use UEFI or else you boot in BIOS and then have major issues dual booting. If one system is UEFI and the other BIOS, you have to go into UEFI menu and turn UEFI on or off or turn BIOS/CSM/Legacy boot mode on or off for whichever system you want to boot with.

So with secure boot off. Fast boot off in Windows to prevent its hibernation. What boots directly from UEFI menu. You should see Windows, ubuntu, and linuxmint as UEFI boot options.

It looks like you ran the rename function in Boot-Repair. It is not always required and if booting the Windows option in UEFI menu you will get grub as it renames files. If you can boot Ubuntu or Mint without rename then undo rename.
       Rename will occure if Boot-Repair sees Windows kernel issues, but may not always be required. 
buggy-kernel detected. Do you want to activate [Backup and rename Windows EFI files]?
Rename option now under advance choices - updated Boot-Repair so that by default it will put grub/shim in EFI/BOOT/bootx64.efi only
[http://ubuntuforums.org/showthread.php?t=1769482&p=12740984#post12740984](http://ubuntuforums.org/showthread.php?t=1769482&p=12740984#post12740984)
 available as a "Rename Windows EFI files" option in the Advanced Options for the few UEFI that are modified to only Boot Windows efi file.
To perform this, just run Boot-Repair --> Adv options --> tick "Backup and rename EFI files" --> Apply
Then reboot the PC to UEFI/BIOS and chose ubuntu,  and please tell us what you observe.
Please enable SecureBoot in your UEFI/BIOS, then run Boot-Repair --> Advanced Options --> "GRUB options" tab --> tick "SecureBoot" --> Apply.
Used Boot-Repair to rename files:
[http://ubuntuforums.org/showthread.php?t=2103778](http://ubuntuforums.org/showthread.php?t=2103778)
To perform this, just run Boot-Repair --> Adv options --> tick "Backup and rename EFI files" --> Apply
Then renamed /EFI/microsoft/boot/shimx64.efi to bootmgfw.efi
Actual Windows boot file, originally bootmgfw.efi.
/EFI/Microsoft/Boot/bkpbootmgfw.efi

   To undo & to rename files to their original names, you just need to tick the "Restore EFI backups" option of Boot-Repair. 

Boot-Repair also adds every efi file in efi folder as boot option. You may want to houseclean out some or most of those. Instructions in link in my signature.

---

### Post by joeltrane on 2013-10-07
Fred,

Thank you so much for your detailed response, I will try what you have recommended tonight and report my findings. :-)

Regards,
Joel

---

### Post by oldfred on 2013-10-07
If you left fast boot on, you may have to undo the rename, so you can directly boot Windows from UEFI menu. Then you need to test if you can boot the other systems without secure boot and fast boot in Windows on.
A few Windows only boot with secure boot or have hard coded UEFI (not standard) and only boot the Windows efi file. That is why the rename work around exists. But most vendors are changing UEFI to not require just a Windows boot.

---

### Post by joeltrane on 2013-10-07
Hi,

I was unable to boot ubuntu or mint with secure boot enabled in my BIOS menu.

> Rename option now under advance choices - updated Boot-Repair so that by  default it will put grub/shim in EFI/BOOT/bootx64.efi only

The above is confusing me.

As it stands, I can now default to grub but when I select WINDOWS UEFI in grub, I get the previous bootloader problem in windows. When I select other efi files in grub I either get a stop error or it reloads grub.

Here is what happened after my last attempts with boot repair: [http://paste.ubuntu.com/6207321/](http://paste.ubuntu.com/6207321/)

Thank you for your help!

Regards,
Joel

---

### Post by oldfred on 2013-10-07
You must have secure boot on. 
Ubuntu will boot with secure boot, but you have to have Installed in UEFI mode with secure boot on or run Boot-Repair with secure boot on. Then it installs the signed versions of the kernel & grub that include the Microsoft signing key. You do not have signed versions, so you only can boot with secure boot off.
Better to turn secure boot off, anyway.

This says you have run rename.
                        /EFI/Microsoft/Boot/bkpbootmgfw.efi 
                       /EFI/Microsoft/Boot/bootmgfw.efi 
The bootmgfw.efi is now grub2's shim file so your UEFI boots that when you choose Windows in UEFI menu. Shim has the Microsoft key so it will work. And then the bkpbootmgfw.efi is the original Microsoft file.

You may have to un-rename as posted above in post #3 to directly boot Windows if you cannot boot Windows from grub menu. It seems you may have left fast boot on also? That always causes problems dual booting.

---

### Post by joeltrane on 2013-10-08
Hello,

I do not see an option for fast boot in my bios menu. I also do not see any files named [B][COLOR=#000000]/EFI/microsoft/boot/shimx64.efi
[/COLOR][/B]
[COLOR=#000000]> Ubuntu will boot with secure boot, but you have to have Installed in UEFI mode with secure boot on or run Boot-Repair with secure boot on.[/COLOR][COLOR=#000000]
[/COLOR]
[COLOR=#000000]I do not believe that I installed ubuntu in uefi mode. When I installed UBUNTU I used the "something else" selection. Would choosing "install ubuntu along side windows 8" have installed ubuntu in uefi mode?[/COLOR]

[COLOR=#000000]Can I re-install Ubuntu in order to put it in UEFI mode? If so, How would I do configure it?[/COLOR]

[COLOR=#000000]> Then it installs the signed versions of the kernel & grub that include the Microsoft signing key. You do not have signed versions, so you only can boot with secure boot off.[/COLOR]
[COLOR=#000000]Better to turn secure boot off, anyway.[/COLOR][COLOR=#000000][/COLOR]

[COLOR=#000000]So by Installing Ubuntu in UEFI mode will allow me to access the Windows 8 partition?

[/COLOR]> [COLOR=#000000]You may have to un-rename as posted above in post #3 to directly boot Windows if you cannot boot Windows from grub menu. It seems you may have left fast boot on also? That always causes problems dual booting.[/COLOR]

What file do I need to un-rename, and what tool would I use to rename it? Should I edit the script manually? Can I do this with "Grub customizer"?

I do not think that I understand what to do, it seems like this is over my head at the moment. Do I need to change bootmgfw.efi to [COLOR=#000000]bkpbootmgfw.efi?[/COLOR]

This is what windows looks like when I try to boot to Windows: [Windows boot error]("https://www.google.com/url?sa=i&rct=j&q=&esrc=s&source=images&cd=&cad=rja&docid=1XwghJ3GxH-tQM&tbnid=exBruE_pc9YtlM:&ved=0CAUQjRw&url=http%3A%2F%2Fwww.prime-expert.com%2Farticles%2Fb18%2Ffix-0xC0000098-windows-bcd-does-not-contain-valid-os-entry.php&ei=qEFUUv3uFZSw4AOUuYDIAg&bvm=bv.53537100,d.dmg&psig=AFQjCNHETLxwdEYWs8LXFUNlKbS3H8_n6Q&ust=1381339940904638") <--- Would following these instructions allow me to rename the file?

I guess don't understand how to follow your instructions oldfred. Thanks for all of your help so far.

Best Regards,
Joel

---

### Post by westie457 on 2013-10-08
Hi oldfred's knowledge of boot issues is far superior to mine, so I am not going to interfere too much.

> [COLOR=#000000]I do not see an option for fast boot in my bios menu.[/COLOR]
Fastboot is hidden away in the power options found inside the Control Panel. I cannot remember exactly where in those options so I turned off all forms of hibernation and suspend. This was done to allow for the adding of files to a separate Data partition while using Ubuntu so Windows would be able to see them as well.

With Fastboot enabled Windows does not unmount the partitions (drives) and will not make the necessary adjustments to the Master File Table of any partitions that you write to.

Hope this is helpful to you.

---

### Post by joeltrane on 2013-10-08
Westie,

Thank you but I cannot boot windows in order to turn off fastboot. I read somewhere that it is possible to Enter bios and then hold down the power button for about 2 seconds until you hear 3 beeps and that should turn it off.

Can I correct this with a recovery disk? I suppose a live disc will allow me to do this but I do not know where to get a reliable ISO that isn't compromised by bundled malware.

When I did this, it did not seem to do anything:

> [COLOR=#000000]available as a "Rename Windows EFI files" option in the Advanced Options for the few UEFI that are modified to only Boot Windows efi file.[/COLOR]
[COLOR=#000000]To perform this, just run Boot-Repair --> Adv options --> tick "Backup and rename EFI files" --> Apply[/COLOR]
[COLOR=#000000]Then reboot the PC to UEFI/BIOS and chose ubuntu, and please tell us what you observe.[/COLOR]


I apologize for my ignorance on this issue and you all are wonderful human beings. Thank you for your continued assistance! I am sure that I am not interpreting the instructions very well. I am learning a whole lot about bootloaders and efi in the mean time though. I want to learn more about these issues so I can help people one day who share this very frustrating circumstance.

Regards,
Joel

---

### Post by oldfred on 2013-10-08
I was trying to explain what the rename does.

Run this:
To undo & to rename files to their original names, you just need to tick the "Restore EFI backups" option of Boot-Repair.

Then from UEFI menu in UEFI/BIOS you should be able to boot Windows directly. 
Turn off fast boot & turn off secure boot if it is on also. 
Confirm if you can boot Windows with secure boot off.
See it Ubuntu entry ubuntu in UEFI menu works.

---

### Post by joeltrane on 2013-10-08
Hello,

No wonder I didnt understand... My version of Boot repair seems to not have that option to Restore EFI Please see: [http://ubuntuone.com/1R5xB91RnPd8GadePNzGwR](http://ubuntuone.com/1R5xB91RnPd8GadePNzGwR)

I did a search and found this out by looking at this: 
[IMG]http://pix.toile-libre.org/upload/original/1346614300.png[/IMG]

I think I am getting somewhere I will try to boot to a live image of mint and run this in efi mode.

---

### Post by oldfred on 2013-10-08
It seems boot-repair cannot find its own backups? Your post showed this from Boot-Repair line 1572:
       Save and rename /mnt/boot-sav/sda4/EFI/Boot/bootx64.efi (/mnt/boot-sav/sda4/EFI/Boot/bkpbootx64.efi)
cp /boot/efi/EFI/ubuntu/grubx64.efi /mnt/boot-sav/sda4/EFI/Boot/bootx64.efi
LIne 1558
Adding custom /boot/efi/EFI/Microsoft/Boot/bootmgfw.efi
Adding custom /boot/efi/EFI/Boot/bkpbootx64.efi
sda1/bkpbootx64.efi already added
    
You can always manually rename files back.
 Then renamed /EFI/microsoft/boot/shimx64.efi to bootmgfw.efi
Actual Windows boot file, originally bootmgfw.efi.
/EFI/Microsoft/Boot/bkpbootmgfw.efi

So the bkp file is the original Windows file. Rename the shim that has the Windows name and rename the bkp file to bootmgfw.efi.

You also should have a copy of the original Windows file here:

 Windows UEFI install should  have backup of bootmgfw.efi here:
C:\Windows\Boot\EFI\bootmgfw.efi from a working Windows x86_64 installation.

---

