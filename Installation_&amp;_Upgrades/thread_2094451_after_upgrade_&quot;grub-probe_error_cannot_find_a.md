---
title: "after upgrade: &quot;grub-probe: error: cannot find a GRUB drive for .&quot;"
date: 2012-12-13
forum: Installation &amp; Upgrades
---

### Post by amp_man on 2012-12-13
I installed lubuntu 12.04 on this machine, an old Thinkpad T30, alongside Windows XP. Since I can't access Quickbooks through lubuntu, the machine being too slow to run a virtual machine reliably, I used grub-customizer to move XP to the top of the grub list, and set the save-default option. Now, any time update-grub runs, I get this error:

```
Installation finished. No error reported.
Generating grub.cfg ...
using custom appearance settings
Found linux image: /boot/vmlinuz-3.5.0-19-generic
Found initrd image: /boot/initrd.img-3.5.0-19-generic
Found linux image: /boot/vmlinuz-3.2.0-34-generic
Found initrd image: /boot/initrd.img-3.2.0-34-generic
Warning: Please don't use old title `Ubuntu, with Linux 3.2.0-34-generic' for GRUB_DEFAULT, use `Advanced options for Ubuntu>Ubuntu, with Linux 3.2.0-34-generic' (for versions before 2.00) or `gnulinux-advanced-159c7754-a054-4b6a-bfb3-55bf175abac7>gnulinux-3.2.0-34-generic-advanced-159c7754-a054-4b6a-bfb3-55bf175abac7' (for 2.00 or later)
Found linux image: /boot/vmlinuz-2.6.32-5-686
Found initrd image: /boot/initrd.img-2.6.32-5-686
cat: /video.lst: No such file or directory
/usr/sbin/grub-probe: error: failed to get canonical path of .
/usr/sbin/grub-probe: error: cannot find a GRUB drive for .  Check your device.map.
dpkg: error processing grub-pc (--configure):
 subprocess installed post-installation script returned error exit status 1
```

I've searched through the config files in /etc/grub.d/ and /etc/default/grub, and have been unable to find an erroneous "." anywhere, and these files were working fine before the upgrade. 

How can I just whipe out all the files in grub.d and replace them with the default versions?

---

### Post by oldfred on 2012-12-14
I think it was when I changed to grub 1.99 I found I had a missing } in my 40_custom. Before it worked, just left off that boot stanza. And since it was an old one I did not notice it missing before. Then with grub 1.99 it would not add any of my 40_custom. No typos allowed.

I would check to make sure your entries are all grub2 1.99 compatible. Perhaps update entries with the new version of Grub Customizer.

       New Grub Customizer works with 12.10
[http://www.webupd8.org/2012/09/grub-customizer-30-released.html](http://www.webupd8.org/2012/09/grub-customizer-30-released.html)
HOWTO: Grub Customizer Updated for grub 1.99
[http://ubuntuforums.org/showthread.php?t=1664134](http://ubuntuforums.org/showthread.php?t=1664134)
[http://www.ubuntugeek.com/grub-customizer-2-2-released-and-installation-instructions-included.html](http://www.ubuntugeek.com/grub-customizer-2-2-released-and-installation-instructions-included.html)

---

### Post by Joachim K on 2012-12-18
> **oldfred said:**
> I think it was when I changed to grub 1.99 I found I had a missing } in my 40_custom. Before it worked, just left off that boot stanza. And since it was an old one I did not notice it missing before. Then with grub 1.99 it would not add any of my 40_custom. No typos allowed.

I would check to make sure your entries are all grub2 1.99 compatible. Perhaps update entries with the new version of Grub Customizer.

       New Grub Customizer works with 12.10
[http://www.webupd8.org/2012/09/grub-customizer-30-released.html](http://www.webupd8.org/2012/09/grub-customizer-30-released.html)
HOWTO: Grub Customizer Updated for grub 1.99
[http://ubuntuforums.org/showthread.php?t=1664134](http://ubuntuforums.org/showthread.php?t=1664134)
[http://www.ubuntugeek.com/grub-customizer-2-2-released-and-installation-instructions-included.html](http://www.ubuntugeek.com/grub-customizer-2-2-released-and-installation-instructions-included.html)


I just updated to ubuntu 12.10 and I get the exact same error. I tried to use Grub Customizer, but get a similar error message when trying to open it (see screenshot).

I also noticed that the error says to check device.map, but I can't find that file. Any help will be much appreciated. Thanks, Joachim

---

### Post by oldfred on 2012-12-19
Device map is not used anymore. There is a note somewhere that it will use it if found but grub probes for all drives as it loads. That can lead to issues if it cannot probe all drives to partition table errors or a corrupt partition that it cannot see.

Run this to see lots of details.

       Post the link to the BootInfo report that this creates. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)
Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration and diagnose advanced problems.
Install in Ubuntu liveCD or USB or Full RepairCD with Boot-Repair (for newer computers) 
[http://sourceforge.net/p/boot-repair/home/Home/](http://sourceforge.net/p/boot-repair/home/Home/)
[https://help.ubuntu.com/community/UbuntuSecureRemic](https://help.ubuntu.com/community/UbuntuSecureRemic)

---

