---
title: "GRUB2 boot-repair on multi-boot (RHEL &amp; Fedora)"
date: 2022-11-02
forum: Installation &amp; Upgrades
---

### Post by robuntu66 on 2022-11-02
Hi,

I am writing about a problem with booting from Grub on my system that has Ubuntu Desktop, Mint Desktop, Fedora Server, Debian Server and RHEL.  I have it set up like that so I can gradually progressively set up a system that is the same and work through the variations. It is working so far with all of them very well but Fedora and RHEL won't boot. They come up with the same message that says **boot: dracut-initqueue timeout. **They were all working prior to installing Ubuntu but then it lost access to those two. Its interesting how the installation sequence, graphics and everything about the install environment was almost exactly the same on Fedora and RHEL.

I downloaded the boot-repair and ran it to the point where it posts the report. Which I have included the link to on pastebin:
[https://pastebin.ubuntu.com/p/mPnbk7wvF2/](https://pastebin.ubuntu.com/p/mPnbk7wvF2/) 

Please can anyone help me correct it?  Any pointers and also any help understanding and seeing how to diagnose for myself, and pointers on sequence of appraisal.

Best wishes and thank you for your help.

Rob

---

### Post by yancek on 2022-11-02
>   Its interesting how the installation sequence, graphics and everything  about the install environment was almost exactly the same on Fedora and  RHEL.

Fedora was created by and is a test bed for Red Hat Linux.

Boot repair shows your drive is GPT and you have a bios_boot partition (sda9) which is needed for Grub.  You also have and EFI partition (sda6) and the only files there are for Ubuntu.  Have you tried running:  sudo update-grub from Ubuntu?  Do you have Legacy/CSM boot enabled in the BIOS firmware?

---

### Post by oldfred on 2022-11-02
You cannot easily mix UEFI & BIOS.
Only from UEFI can you boot different installs.
Grub can only boot other installs in same boot mode. The bios_grub partition can only have one grub in it for BIOS boot.

You booted Boot-Repair in BIOS/CSM/Legacy mode, but Ubuntu is in UEFI boot mode.
Best to all all installs in UEFI boot mode as ESP can have multiple boot loaders as long as different. But many based on Ubuntu all use same /EFI/ubuntu entry. And those that use grub have one entry for /EFI/grub.
But then from grub you can boot all other installs, if in same boot mode.

How to: Create a Customized GRUB2 Screen that is Maintenance Free.- Cavsfan
[https://help.ubuntu.com/community/MaintenanceFreeCustomGrub2Screen](https://help.ubuntu.com/community/MaintenanceFreeCustomGrub2Screen)
[https://www.gnu.org/software/grub/manual/grub/grub.html#Multi_002dboot-manual-config](https://www.gnu.org/software/grub/manual/grub/grub.html#Multi_002dboot-manual-config)
[https://help.ubuntu.com/community/Grub2/CustomMenus](https://help.ubuntu.com/community/Grub2/CustomMenus)
[http://ubuntuforums.org/showthread.php?t=2076205](http://ubuntuforums.org/showthread.php?t=2076205)
Configfile example to another grub.cfg
[https://ubuntuforums.org/showthread.php?t=2076205&p=13787835#post13787835](https://ubuntuforums.org/showthread.php?t=2076205&p=13787835#post13787835)

---

### Post by robuntu66 on 2022-11-02
Hello!

@yancek thank you for your suggestion.  Running [COLOR=#000000]sudo update-grub in Ubuntu went through all the partitions and found all the systems [/COLOR][COLOR=#000000]successfully. I went through them one by one and then just as I was thinking it was fixed RHEL got stuck at [OK] Reached Target Basic System, then after a while, started to come up with the same error over and over again.
Because Fedora worked I went back into Ubuntu and ran the same command, then after it found RHEL again tried to boot that immediately instead of going to any of the others first (It came last last time). It didn't matter, Fedora still worked but not RHEL.

[/COLOR]@yancek @oldfred[COLOR=#000000]
With the BIOS firmware it is an old[/COLOR] ASUS P7H55D-M LX BIOS[COLOR=#000000] so it doesn't have any options available in there to change. 

So anyway. I now have because of the positive things that happened as a result of running the command [/COLOR][COLOR=#000000]sudo update-grub run the [/COLOR][COLOR=#000000]boot-repair again and have a new file on Pastebin:
[/COLOR]https://pastebin.ubuntu.com/p/5P29Y4WPx3/[COLOR=#000000]
[/COLOR][COLOR=#000000]
PS: @oldfred [/COLOR][COLOR=#000000]How to: Create a Customized GRUB2 Screen looks cool
[/COLOR][COLOR=#000000]
Thanks for your help and best wishes,

Rob

[/COLOR]

---

### Post by oldfred on 2022-11-02
It looks like sda1 & sda2 have UEFI installs. You can see mount of ESP in fstab.
Mint uses Ubuntu so either could be the entry in UEFI. Last one installed or with major update will be that default.

You can easily convert both Mint & Ubuntu to BIOS boot using Boot-Repair's advanced mode.
You have to choose install & drive to install grub into. 
But with BIOS boot only one install can be in MBR, but its grub should boot all other BIOS installs.
But major grub update in any install, may reinstall to MBR, converting it to default.

With BIOS/MBR better to have different drives with different grub installs in each MBR.

You need to make sure UEFI/BIOS is set to boot in correct mode.
There must be a setting somewhere as you have both UEFI & BIOS installs. So Asus boots either way.
How you boot install media, UEFI or BIOS is then how it installs. UEFI is usually clear as UEFI:xxxx and BIOS is just xxxx where xxxx is name or label of flash drive. My systems often say PMAP.

---

### Post by robuntu66 on 2022-11-02
OK great I'll have a play around with it tomorrow.
Thanks for your feedback, will let you know.

---

