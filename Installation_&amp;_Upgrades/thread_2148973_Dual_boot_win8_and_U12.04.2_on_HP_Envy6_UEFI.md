---
title: "Dual boot win8 and U12.04.2 on HP Envy6 UEFI"
date: 2013-05-27
forum: Installation &amp; Upgrades
---

### Post by pberden on 2013-05-27
Hi, I'm trying to install Ubunut 12.04.2 on a HP Envy 6 1208ed. I followed these instructions: [https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

Regarding step 2; "In your BIOS, [disable QuickBoot/FastBoot]("http://ubuntuforums.org/showpost.php?p=12397979&postcount=9") and [Intel Smart Response Technology]("http://ubuntuforums.org/showpost.php?p=12460938&postcount=6") (SRT). If you have Windows8, also [disable FastStartup]("http://www.eightforums.com/tutorials/6320-fast-startup-turn-off-windows-8-a.html")."
I don't see any of these options in my BIOS. I do have Intel Rapid Start Technology, not sure whether this should be disabled or not.
And I forgot to disable FastStartup in Win8. :icon_frown:

The output of Boot-Repair is here: [http://paste.ubuntu.com/5706452/](http://paste.ubuntu.com/5706452/)

GRUB is loaded on boot, but Ubuntu does nothing. When i choose the recovery mode, it displays Loading Linux 3.5.0-31-generic... and that's it.
Choosing Windows 8 returns errors:
Secure Boot forbids loading module from (hd0,gpt7).boot/grub/ntfs.mod
...
...invalid EFI file path

Any help is appreciated!

---

### Post by pberden on 2013-05-27
Oh forgot to mention that Boot-Repair gave this message:

Please do not forget to make your BIOS boot on sda2/EFI/ubuntu/grubx64.efi file

I have no clue on how to this. In the BIOS I can choose between legacy and UEFI boot, and set the order but I don't seen an option to add a boot file or whatsoever.

---

### Post by fantab on 2013-05-28
In you UEFI/BIOS you will see an option to boot Windows and Ubuntu You have to choose and set it boot Ubuntu.

---

### Post by ubfan1 on 2013-05-28
My understanding is 1) you are doing UEFI boot (no MBR set in sda), and 2) you are doing secure boot (used the signed kernels in grub).
Notice in your grub you have two types of Windows boot menu items -- the ones that have UEFI in them are the ones to use, the others  with the chainloader +1 are for any potential legacy boot -- not for you.  If those don't boot Windows for you, try Windows directly from the efi menu -- early in the boot sequence, type the function key (varies by machine) which gives you the choice to select a boot device, select the hard disk in UEFI mode, or just the hard disk if that is the only choice, then maybe a windows will pop up allowing you to select the operating system on the hard disk, you should see Windows or Ubuntu. Both should work.  ubuntu should bring up grub.
  When running Ubuntu, package/program efibootmgr will allow you to examine the details of the efi boot.  run  sudo efibootmgr -v  and you should see the two choices, with their paths:  That is the path the boot-repair was referring to .  The ubuntu choice path should NOT be /EFI/ubuntu/grubx64.efi for a secure boot, but instead should be /EFI/ubuntu/shimx64.efi.  The correct entry should be made by grub-install --uefi-secure-boot.  efibootmgr offers many capabilities, but I have used it only for listing things.

---

### Post by fantab on 2013-05-28
OP has ran 'Boot-Repair' and it probably fixed the boot issue for him/her.

[QUOTE=Boot Info Summary @ paste.ubuntu.com/5706452/]
Boot successfully repaired.  You can now reboot your computer. 
Please do not forget to **make your BIOS boot on sda2/EFI/ubuntu/grubx64.efi file**![/QUOTE]

OP has to set it in BIOS/UEFI to boot Ubuntu/Grub entry.

---

### Post by pberden on 2013-05-30
Hi ubfan and fantab, thanks for your responses!

Here's what I see when I boot to the boot manager: [http://imageshack.us/photo/my-images/27/imag0595m.jpg/](http://imageshack.us/photo/my-images/27/imag0595m.jpg/)

The first two options give me: [http://imageshack.us/photo/my-images/580/imag0596b.jpg/](http://imageshack.us/photo/my-images/580/imag0596b.jpg/) (1)

The third option (ubuntu (MTFDDAT128MAM-1J2) boots to the GRUB menu: [http://imageshack.us/photo/my-images/196/imag0598nn.jpg/](http://imageshack.us/photo/my-images/196/imag0598nn.jpg/) (2)

When I choose Ubuntu (1st option), I get a purple screen but nothing happens. When I choose the recovery mode (2nd option) I see: [http://imageshack.us/photo/my-images/835/imag0599burst002.jpg/](http://imageshack.us/photo/my-images/835/imag0599burst002.jpg/)

The last option in the boot manager let me see the [COLOR=#000000]/EFI/ubuntu/[/COLOR][COLOR=#000000]grubx64.efi and [/COLOR][COLOR=#000000]/EFI/ubuntu/shimx64.efi, but give the same results as above, 1 and 2 respectively.



My BIOS boot options are: [/COLOR]http://imageshack.us/photo/my-images/826/20130530100924.jpg/

Hope you can help me further on this issue. What will happen when I boot in the live CD and wipe the Ubuntu partition? Will Windows boot normally? Or in other words is GRUB on the ubuntu partition or on a higher level? :confused:

Regards,

Paul

---

### Post by ubfan1 on 2013-05-30
Oh, I see you have the wrong grub, should be 2.0 something instead of 1.99.  To reinstall grub
sudo grub-install --uefi-secure-boot 
(I think it defaults to sda, so that's all that's needed)
Everything else looks reasonable.  the EFI menu Ubuntu is grubx64, the lower case ubuntu is shimx64, and they do just what you'd expect for secure boot. You might want to increase the 0 time to 5 seconds to give yourself a little more time to hit function keys for boot options.

---

### Post by fantab on 2013-05-30
AFAIK 12.04 uses Grub 1.99. I could be wrong.

---

### Post by ubfan1 on 2013-05-30
Oops, you're right. Somehow got the idea 12.04.2 had switched over along with the kernel.

---

### Post by ubfan1 on 2013-05-30
The loading kernel message does not list the name with a ".signed" at the end -- not sure if that really means you're booting an unsigned kernel.  Maybe check from the live media the two grub.cfg files, the one listed from /boot/grub and the one in /EFI/ubuntu.  Should be the same but..  When you are at grub, type "e" and look at the linux line.  Does it have a name like "vmlinuz-3.5.0-31-generic.signed" (looking for the .signed).  If not, type it in and boot control-X or F10.

---

### Post by pberden on 2013-05-31
See grub line here: [http://imageshack.us/photo/my-images/541/20130531165132.jpg/](http://imageshack.us/photo/my-images/541/20130531165132.jpg/)

it has .signed...

Next week I'll try:
-wiping the ubuntu partition.
-boot Win 8
-[COLOR=#000000]disable FastStartup in Win8
-reinstall ubuntu

Thanks for all your help so far![/COLOR]

---

### Post by fantab on 2013-05-31
'Fast Startup' in Win8 is 'Hibernate'. It has to be disabled to affect a proper shutdown, without which it is not possible to boot any other OS.
I just re-read your First post... You should've disabled it in the first place. That is the issue.

---

### Post by pberden on 2013-06-03
I've wiped the Ubuntu partition
Did a system restore for Win 8
Disabled Fast Startup
Installed Ubuntu
Ran Boor Repair

Now Ubuntu boots, yeah!

But Windows does not. I'm ok for now because Ubuntu will be the main OS, Windows is a nice to have.

Here is the new log from Boot Repair: [http://paste.ubuntu.com/5728756/](http://paste.ubuntu.com/5728756/)

---

### Post by fantab on 2013-06-03
This is known bug: [https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1024383](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1024383)

Boot-Repair should fix it.

---

### Post by pberden on 2013-06-05
I've got the Envy working with dual boot! After the ubuntu install I had to run Boot Repair via the live CD to be able to boot to Ubuntu. Then I needed to run Boot Repair again from the installed Ubuntu OS in order to be able to boot in Win8.

Thanks for your help!

---

### Post by YannBuntu on 2013-06-05
hello
> **pberden said:**
> http://paste.ubuntu.com/5706452/

Please disable SecureBoot in your BIOS, then run the Recommended Repair again, and indicate the new URL that will appear.
Then reboot and indicate what you observe.

---

