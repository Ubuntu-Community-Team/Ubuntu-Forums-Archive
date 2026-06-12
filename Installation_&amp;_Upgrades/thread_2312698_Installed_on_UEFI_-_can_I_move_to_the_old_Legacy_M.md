---
title: "Installed on UEFI - can I move to the old Legacy MBR?"
date: 2016-02-06
forum: Installation &amp; Upgrades
---

### Post by helm10101 on 2016-02-06
Hello,

My BIOS has 2 options: to install an OS via UEFI or in Legacy mode.
What I did was to install Windows 10 and Ubuntu through the UEFI menu and not the Legacy menu (in the bios boot page).
Now, I wanted to try and install a 3rd OS, another Linux, but it doesn't support installation from UEFI.
What I did was to turn Legacy support on and install the OS from the Legacy mode, only to perform the installation.
That didn't work, because I now understood that you can either choose from UEFI or Legacy at a time. If I turn off Legacy - I can't boot to the 3rd OS, but if I turn on Legacy - I can't boot to GRUB and choose between Windows or Ubuntu.

What can I do to solve that?
Should I install all the 3 OS's in Legacy mode? And not use UEFI?
And if I choose to do that, I must reinstall Windows and Ubuntu under Legacy mode? Or I can somehow transfer those installations to the Legacy mode together with the 3rd OS?

Or there's something else?

Thanks!

---

### Post by ubfan1 on 2016-02-06
Maybe after the legacy install, switch back to UEFI, and run sudo update-grub.  Then you should be able to boot all three from UEFI.  The actual install has little difference, maybe an fstab entry for the EFI partition, but frankly, I don't think that is needed on a third OS which will never update grub for you.

---

### Post by Dennis N on 2016-02-06
The legacy (BIOS) install on a GPT disk is supposed to have bios boot partition. Create a 1-2 mB unformatted partition and set the "bios_grub" flag on that partition.

You cannot boot installs made in UEFI mode from grub on a BIOS system, and vice-versa. Maybe use the one-time boot menu.

I have also read that mixing legacy installs and UEFI installs on the same hard disk is not recommended, so I don't do it myself. At least put them on a different drive if not a separate computer.

---

### Post by grahammechanical on 2016-02-06
> What can I do to solve that?

> Having a PC with UEFI firmware does not mean that you need to install Ubuntu in UEFI mode. What is important is below:  


[LIST]
[*]if  the other systems (Windows Vista/7/8, GNU/Linux...) of your computer  are installed in UEFI mode, then you must install Ubuntu in UEFI mode  too. 
[*]if  the other systems (Windows, GNU/Linux...) of your computer are  installed in Legacy (not-UEFI) mode, then you must install Ubuntu in  Legacy mode too. Eg if your computer is old (<2010), is 32bits, or  was sold with a pre-installed Windows XP. 


[*]if  Ubuntu is the only operating system on your computer, then it does not  matter whether you install Ubuntu in UEFI mode or not.
[/LIST]


[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

> Should I install all the 3 OS's in Legacy mode? And not use UEFI?

You should be asking can I install Windows 10 in legacy mode?

[http://www.tenforums.com/general-discussion/2448-windows-10-mbr.html](http://www.tenforums.com/general-discussion/2448-windows-10-mbr.html)

Regards

---

### Post by helm10101 on 2016-02-06
Right now, I have a 3rd Linux install, but it's floating somewhere and I can't see it anywhere. I will try to update grub.
Btw, I did install Windows 10 in the past on the Legacy instead of the UEFI so I guess no problem.

* I dont think update-grub will change anything because as I can see in graham's post, you must have all of the OS the same way: UEFI or Legacy

---

### Post by oldos2er on 2016-02-06
Rhetorical question--will Windows 10 even install in legacy mode? I would guess "no" but I don't know for a certainty. That would be a question best asked in a Windows' support forum, or [here]("http://ubuntuforums.org/forumdisplay.php?f=170"). 

As was mentioned, you can't mix UEFI with BIOS/MBR installations, your system is either one or the other. 

Seems to me a virtual machine would be preferable to changing around your entire system. What is this other distro, btw?

---

### Post by helm10101 on 2016-02-06
Update:
1) ubfan, you were right, I just connected to Ubuntu, ran sudo update-grub, and it added the 3rd Linux to Grub2!
2) I already installed Windows 10 in Legacy mode in the past. (uninstalled after I installed ubuntu in UEFI and couldn't mix)
3) From some reason, I installed Ubuntu and Windows 10 in UEFI, and the 3rd Linux in Legacy mode, and I WAS able to mix between them, and it now appears in Grub2!

*Not sure what exactly I did, but on the 3rd Linux installation, it asked me if I want to overwrite the existing Ubuntu's Grub, I said 'NO', so it asked me to manually put the bootloader somewhere.
I put it, without really knowing where it is, on /dev/sda2 (which I later saw that it's for Windows boot manager).
Can you explain me, how can it be that both Windows boot loader and the other Linux boot loader are on the same folder /dev/sda2 (it is a folder in Ubuntu, right? or partition, but still)

Thank you!

---

### Post by oldfred on 2016-02-06
If you did not install grub to MBR, you corrupted the NTFS partition. That becomes another repair.

You can boot one system in UEFI mode and one in BIOS mode, just not recommended. And you cannot use grub to boot. You have to use UEFI boot menu or one time boot key. Some UEFI may require you to turn on/off UEFI or BIOS/CSM/Legacy boot settings, but most newer will let you choose & know which way to boot, either from MBR or from ESP - efi system partition.

But once you start booting in one mode you cannot switch to other mode. Or you can only use grub to boot systems installed in same boot mode.
Some can work around it as UEFI has a one time reboot, so you reboot into the other install. Do not think grub can do that.

NTFS/FAT32 saves a backup partition boot sector. If you wrote grub into the partition you need to use testdisks to restore from backup. What exactly is sda2, that often is the FAT32 ESP - efi system partition.

Both Windows and Linux install in UEFI or BIOS boot mode totally based on how you boot install media. So you can boot Windows in BIOS mode and install in BIOS mode. But Windows will convert drive back to MBR(msdos) in effect erasing drive. 
Windows only boots in UEFI mode from gpt partitioned drives.
Windows only boots in BIOS mode from MBR partitioned drives.

---

### Post by ubfan1 on 2016-02-06
If /dev/sda2 is your EFI partition, it normally gets mounted at /boot/efi, so the filesystem on the partition appears from that point -- /boot/efi/EFI/...  Now the ubuntu bootloaders get installed to /boot/efi/EFI/ubuntu, so they do not overwrite the Windows bootloaders, which are in /boot/efi/EFI/Microsoft/Boot.  Which bootloader to use is picked out of non-volatile ram, so there is no conflict with having multiple bootloaders.

---

### Post by helm10101 on 2016-02-06
> **ubfan1 said:**
> If /dev/sda2 is your EFI partition, it normally gets mounted at /boot/efi, so the filesystem on the partition appears from that point -- /boot/efi/EFI/...  Now the ubuntu bootloaders get installed to /boot/efi/EFI/ubuntu, so they do not overwrite the Windows bootloaders, which are in /boot/efi/EFI/Microsoft/Boot.  Which bootloader to use is picked out of non-volatile ram, so there is no conflict with having multiple bootloaders.

Thank you ubfan!
Yes, sda2 is my EFI partition created by Windows installation. but if I installed the boot loader of the second Linux inside sda2, wasn't it supposed to cause problems? maybe when I choose Windows at grub2 menu it would not let it mount because it recognizes 2 boot loaders in the sda2 partition? Or what I'm saying does not make sense (I don't know what's happening inside, but it just what I think is happening, I am no software expert)

Is there a way to check that there is really something like a bootloader inside the /dev/sda2?
I was sure that it would really slow down my start up as there are too many files in the EFI partition (although I don't know what it is used for, just trying to learn and understand new things)

---

### Post by oldfred on 2016-02-06
Post the link to the Create BootInfo summary report. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)

---

### Post by Dennis N on 2016-02-06
> Is there a way to check that there is really something like a bootloader inside the /dev/sda2?

Since sda2 is the EFI system partion, you can post the results of the command below to see inside. You should have more folders than I do here. You may have to install the small utility **tree** first.

```
dmn@Sydney:~$ tree /boot/efi -pu
boot/efi
&#9492;&#9472;&#9472; [drwxr-xr-x root    ]  EFI
    &#9492;&#9472;&#9472; [drwxr-xr-x root    ]  ubuntu
        &#9500;&#9472;&#9472; [-rwxr-xr-x root    ]  grub.cfg
        &#9500;&#9472;&#9472; [-rwxr-xr-x root    ]  grubx64.efi
        &#9500;&#9472;&#9472; [-rwxr-xr-x root    ]  MokManager.efi
        &#9492;&#9472;&#9472; [-rwxr-xr-x root    ]  shimx64.efi

2 directories, 4 files

```

Also, please post the link to your boot info summary as oldfred asked to get a true picture of the situation. Thanks.

---

