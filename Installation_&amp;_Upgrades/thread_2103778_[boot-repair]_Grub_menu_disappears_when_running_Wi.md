---
title: "[boot-repair] Grub menu disappears when running Windows 8"
date: 2013-01-11
forum: Installation &amp; Upgrades
---

### Post by sephiao on 2013-01-11
Hi!

I'm trying to get dual boot on my laptop for Windows 8 (which was pre-installed) and Ubuntu 12.10.

I have gone through quite a lot of struggling already:
1. It seems there was some Ubuntu installation bug related to Windows UEFI boot.
2. After running boot-repair, I still wasn't able to enter Windows, as I had to disable secure boot (and I think I had to go into Windows to get access to BIOS)

This post helped me a lot through the process:
> [http://ubuntuforums.org/showthread.php?t=2087991](http://ubuntuforums.org/showthread.php?t=2087991)


Anyway, I think I ended up reinstalling Windows once (some recovery/restore option they have, as they don't give you the phisical DVD's when you buy the computer)(*1) and I can't remember how many times I have reinstalled Ubuntu.

The thing now is: no matter how many times I run boot-repair, it works perfectly as long as I only go into Ubuntu. **First time I run Windows, my PC stops showing me the grub menu** and I cannot run Ubuntu anymore (until I run boot-repair again from live CD).

This is URL boot-repair generates: > [http://paste.ubuntu.com/1516559/](http://paste.ubuntu.com/1516559/)

I think it's needless to say that there're a lot of partitions of recovery stuff and some other crap which I don't really understand.

Thanks a lot for your time and your help! :)

(*1) If possible, I wouldn't like to repeat that ever again ](*,)

---

### Post by oldfred on 2013-01-11
It looks like you are booting into the Sony recovery by default.

Boot-Repair normally finds the Windows bootmgfw.efi in the efi partition. But your Sony has that file in sda1 and is labeled SONYSYS not efi so that looks like a recovery partition boot file. But since the first partition it is the first one Boot-Repair found.

Try booting from the one labelled like this as that is the real Windows efi entry that you want to chain to:
Windows UEFI bootmgfw.efi sda3

If that works ok we can figure out how to adjust menu and file a bug on Boot-Repair.

---

### Post by sephiao on 2013-01-11
Thanks a lot for your response.

I run the live CD, then boot repair, and then on restart I tried to use the entry:
> Windows UEFI bootmgfw.efi sda3
But the behaviour was the same. It's like if Windows would be erasing the grub every time I run it, or hiding the menu somehow...

Now when I restart/shut down-start it goes directly into Windows.

Just in case you need it, this is the new URL boot repair generated:
> [http://paste.ubuntu.com/1520742/](http://paste.ubuntu.com/1520742/)

Thanks again, I can't express how much I appreciate the help given :)

---

### Post by oldfred on 2013-01-11
I know Yann has been changing Boot-Repair a bit. Windows 8 with secure boot and  each vendor seems to have implemented UEFI a bit different. Some work without issue, some have issues & others just about do not work at all.

I think boot repair now has it as an advanced option. It used to always rename the Windows boot files and then rename grub or shim(grub secure boot) to have the Windows name. Then the UEFI booted grub (not Windows) and grub would add a chain load entry to the backup file of Windows. But some systems that added issues.

I think yours must need the file renaming. Some have done it manually and I think you can use Boot Repair. But back up the entire efi partition first. 

       How Boot-Repair fixes a Ubuntu with grub-pc with efi Windows
[http://ubuntuforums.org/showpost.php?p=12205679&postcount=516](http://ubuntuforums.org/showpost.php?p=12205679&postcount=516)
Boot-Repair - Updated Jan 1, 2013 to not rename first time, but rename if first time Windows does not boot. Post 706
[http://ubuntuforums.org/showthread.php?t=1769482&page=71](http://ubuntuforums.org/showthread.php?t=1769482&page=71)
 Boot-Repair copied /EFI/ubuntu/grubx64.efi to /EFI/Boot/bootx64.efi (in case the BIOS is hard-coded to boot into /EFI/Boot/bootx64.efi or secure boot
signed GRUB file shimx64.efi.

    
       sony vaio laptop error: symbol not found: `grub_efi_secure_boot'.
[http://ubuntuforums.org/showthread.php?t=2102083](http://ubuntuforums.org/showthread.php?t=2102083)> 
So this time I installed 12.10, then I booted again from liveCD, made backup of (efi part)/EFI/microsoft/boot and copied all files from /EFI/ubuntu into it. Then renamed /EFI/microsoft/boot/shimx64.efi to bootmgfw.efi. And it works

    

---

### Post by YannBuntu on 2013-01-11
Hi
> **oldfred said:**
> I think yours must need the file renaming.

To perform this, just run Boot-Repair --> Adv options --> tick "Backup and rename EFI files" --> Apply
Then reboot the PC and please tell us what you observe.

> **oldfred said:**
> to not rename first time, but rename if first time Windows does not boot. Post 706
[http://ubuntuforums.org/showthread.php?t=1769482&page=71](http://ubuntuforums.org/showthread.php?t=1769482&page=71)

@Fred: this is obsolete ([current behavior]("http://ubuntuforums.org/showpost.php?p=12440592&postcount=720")), better giving this link [http://ubuntuforums.org/showpost.php?p=12435040&postcount=711](http://ubuntuforums.org/showpost.php?p=12435040&postcount=711)

---

### Post by sephiao on 2013-01-15
> **YannBuntu said:**
> 
To perform this, just run Boot-Repair --> Adv options --> tick "Backup and rename EFI files" --> Apply
Then reboot the PC and please tell us what you observe.


That made it. Now it works properly!

Just in case you need it for something, this is the generated URL:
> [http://paste.ubuntu.com/1533872/](http://paste.ubuntu.com/1533872/)

I still have one more question. Now I'm going into Windows through the entry called:
> Windows boot UEFI loader sda3

Are the rest of them useful for something? can I tidy up the grub menu with one of the tools available in ubuntu?


Thanks a lot for the support!

---

### Post by oldfred on 2013-01-15
I think you might want to keep entries in 25_custom. Since grub2 os-prober is not currently working you can turn it off and remove those incorrect entries. 

       In /etc/default/grub I added this:
gksudo gedit /etc/default/grub
GRUB_DISABLE_OS_PROBER=true
or turn off executeable bit
sudo chmod a-x /etc/grub.d/30_os-prober

    
When they eventually fix the os-prober then you can turn it back on and house clean 25_custom.

---

### Post by sephiao on 2013-01-15
Thanks for your help!

I got to know a little bit more how it all works. I manually commented some lines on 25_custom and disabled 30_os-prober following your suggestion.

Now my grub menu looks smart and compact, and more important.. it works!

---

### Post by YannBuntu on 2013-01-15
> **sephiao said:**
> That made it. Now it works properly!

Great! \\:D/

IMHO your case shows that each time you use Windows8, Windows8 modifies the BIOS making it boot on /EFI/Boot/bootx64.efi  (or /EFI/Microsoft/Boot/bootmgfw.efi ).
This is another evil strategy of Microsoft to prevent people from using Linux. :twisted:

To workaround this issue, I will enable by default the "Backup and rename EFI files" option of Boot-Repair, as soon as Windows8 is detected.

---

