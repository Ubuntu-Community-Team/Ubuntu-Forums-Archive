---
title: "&quot;No bootable device&quot; - Ubuntu Studio"
date: 2019-03-22
forum: Installation &amp; Upgrades
---

### Post by emians on 2019-03-22
Hi all,

I installed Ubuntu Studio from a bootable USB drive.

On the first reboot I got this message stuck on screen: "No bootable device".

If I reboot from the USB drive containing the OS I get this on boot screen:

"
Failed to open \EFI\BOOT\mmx64.efi - Not Found
Failed to load image \EFI\BOOT\mmx64.efi: Not Found
Failed to start MokManager: Not Found
Something has gone seriously wrong: import_mok_state() failed
: Not Found
"

after the computer just shuts.

I can access to BIOS.

I used balenaEtcher to prepare the bootable USB drive.

I'm trying to remake the bootable USB drive with Ubuntu Studio on my Mac but doesn't allow me to erase the key...

Any suggestions?

Thanks in advance.

---

### Post by oldfred on 2019-03-22
If you have mmx64.efi, copy it into /EFI/Boot.
A full install will have it both in /EFI/Boot and /EFI/ubuntu.
If not just copy shimx64.efi to /EFI/Boot and rename to mmx64.efi.

       System fails to boot with \EFI\BOOT\mmx64.efi - Not Found
[URL="https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1798171"]https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1798171

      [/URL]
 Ubuntu recently renamed MokManager.efi to mmx64.efi, and added fbx64.efi (which just launches GRUB through a new path). 
You used to not be able to install proprietary drivers with UEFI Secure Boot on as Canonical could not sign files from other vendors. But a user can if the user thinks it is trusted. So they now have mmx64.efi so you can create a key to sign your own install of proprietary driver. 

    [URL="https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1798171"]
[/URL]

---

### Post by emians on 2019-03-22
I do not have those files. And in shortage of USB sticks. 

Any other way to start a fresh installation of the OS?

If any more information needed just ask.

I got UEFI and secure boot enabled. Switch to legacy and disable secure boot output the very same issues.

---

### Post by emians on 2019-03-22
Installatio of Ubuntu Studio went smooth and clean. Problem occurred at the reboot.

---

### Post by emians on 2019-03-22
I also tried installing Ubunt Desktop natural. Same issue. 

Any idea on how to cut the chase and put a serious installation on my hardware from a bootable USB drive seen the situation?

---

### Post by oldfred on 2019-03-22
What brand, model hardware? What video card/chip?
Some need boot parameters to work or work well.

If installed this will give a lot of info on the install.
       May be best to see details, use ppa version with your live installer or any working install,  not older Boot-Repair ISO:
Please copy & paste link to the Boot-info summary report ( do not post report), the auto fix sometimes can create more issues.
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

### Post by VMC on 2019-03-23
> **oldfred said:**
> If you have mmx64.efi, copy it into /EFI/Boot.
A full install will have it both in /EFI/Boot and /EFI/ubuntu.
If not just copy shimx64.efi to /EFI/Boot and rename to mmx64.efi.

       System fails to boot with \EFI\BOOT\mmx64.efi - Not Found
[URL="https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1798171"]https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1798171
[/URL]
 Ubuntu recently renamed MokManager.efi to mmx64.efi, and added fbx64.efi (which just launches GRUB through a new path). 
You used to not be able to install proprietary drivers with UEFI Secure Boot on as Canonical could not sign files from other vendors. But a user can if the user thinks it is trusted. So they now have mmx64.efi so you can create a key to sign your own install of proprietary driver. 
[URL="https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1798171"]
[/URL]
Thanks Fred. I just read about this today:
[https://blog.ubuntu.com/2017/08/11/how-to-sign-things-for-secure-boot](https://blog.ubuntu.com/2017/08/11/how-to-sign-things-for-secure-boot)
That bug link is informative.

---

### Post by emians on 2019-03-23
I put Boot-Repair-Disk on USB with balenaEtcher. 
Once loading does not recognize the stick at all and I got the "No bootable device" screen.

I'll give a work on this later, sounds promising:

[COLOR=#000000]System fails to boot with \EFI\BOOT\mmx64.efi - Not Found[/COLOR]
[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1798171](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1798171)

And look further into Boot Repair.

Some infos on the system am working on:

CPU Type: Intel Pentium quadcore CPU N3540 @ 2.16Ghz
System BIOS Version: v1.10
Laptop: ACER Aspire ES1-512 (E15)
No idea about video card. Intel HD graphics?

I'll keep posted progress. Thanks for the infos provided to the now oldfred.

---

### Post by emians on 2019-03-23
2 VMC:

Just saw urs. Cheers. ;)

---

### Post by oldfred on 2019-03-23
All Acer requires you to set "trust" on the ubuntu/grub .efi files from within UEFI.

All similar, but some explain better or differently:
       Acer Trust Settings - details, some now report that then secure boot has to be on to set trust:
[https://ubuntuforums.org/showthread.php?t=2297947&p=13369742#post13369742](https://ubuntuforums.org/showthread.php?t=2297947&p=13369742#post13369742)
[https://ubuntuforums.org/showthread.php?t=2297947](https://ubuntuforums.org/showthread.php?t=2297947) & 
[https://ubuntuforums.org/showthread.php?t=2358003](https://ubuntuforums.org/showthread.php?t=2358003)
[https://ubuntuforums.org/showthread.php?t=2291335&p=13341757#post13341757](https://ubuntuforums.org/showthread.php?t=2291335&p=13341757#post13341757)
[https://ubuntuforums.org/showthread.php?t=2342323](https://ubuntuforums.org/showthread.php?t=2342323)
Acer Cloudbook shows screen for selecting trust, shows typical screens for all Acer
[http://bernaerts.dyndns.org/linux/74-ubuntu/340-ubuntu-install-acer-aspire-cloudbook-431](http://bernaerts.dyndns.org/linux/74-ubuntu/340-ubuntu-install-acer-aspire-cloudbook-431)
[https://community.acer.com/en/categories/predator](https://community.acer.com/en/categories/predator)

---

### Post by VMC on 2019-03-23
I have a Acer-TC desktop and I don't have to bother with Trust-Settings. I've never activated the password. Maybe just Acer laptops, but I would think all Acer's share same or similar bios firmware.
I did upgrade my bios firmware straight away. I've seen several Acer related post's and Trust Settings come up. It makes me ponder why mine is different.

---

### Post by emians on 2019-03-25
Also:
[https://ubuntuforums.org/showthread.php?t=2391280](https://ubuntuforums.org/showthread.php?t=2391280)

---

### Post by emians on 2019-03-25
Any repository for the mmx64.efi to download or fetch?

---

### Post by oldfred on 2019-03-25
the mmx64.efi will be in both /EFI/Boot and /EFI/ubuntu folders in your ESP once installed.

Some have just copied & renamed grubx64.efi to mmx64.efi in /EFI/Boot to make the installer work.
Since key manager only really required for proprietary drivers and adding your own key.

---

### Post by emians on 2019-03-26
OK. Solved.

It was easier than I thought.

So...

Go to bios press F2 while loading and access bios;

Go to "Boot" menu and enable "Secure Boot";

Go to "Security" menu and under the voice "Select an UEFI file as trusted for executing:" press enter;

Press enter @ HDD0;

you'll find <EFI> dir, press enter;

Select <BOOT> dir and press enter; 

Select mmx64.efi and press enter;

F10 to save and exit in reboot.

Now I got Ubuntu Studio running.

Thanks all for support.

---

