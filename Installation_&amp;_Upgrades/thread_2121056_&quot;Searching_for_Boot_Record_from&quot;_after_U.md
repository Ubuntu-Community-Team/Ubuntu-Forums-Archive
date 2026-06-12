---
title: "&quot;Searching for Boot Record from&quot; after Ubuntu 12.10 install from USB"
date: 2013-02-28
forum: Installation &amp; Upgrades
---

### Post by svilenn on 2013-02-28
Hi, I have the following problem:

I had Windows, then I got sick of it breaking down. A friend showed me Ubuntu and after using it off a live usb for a few days, I made the decision to install it to the hdd and to just replace Windows altogether.

So from that Ubuntu 12.10 USB, I clicked Install and went through the whole process with the exception that it seemed to have frozen after sending me back to the home screen, but with the cursor still rolling. So I rebooted and tried again. And again. Still the same. I figured maybe that's its way of saying it's done, so after the third try, I booted without the USB just to see if my harddrive install had worked. After the boot table I get this message:

"Searching for Boot Record from IDE-0..OK" and then it just hangs.

So now the only way I can use Ubuntu is if I load the live usb. If it's not in, I get stuck at the error above.

Any help as to how to repair this, will be much appreciated!

---

### Post by oldfred on 2013-03-01
If it just did not complete the install of grub this may help. But if not a full install it will not. Even though it worked as live install, did you verify download with md5sum? How much RAM does you system have?

       Post the link to the BootInfo report that this creates. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)
Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration and diagnose advanced problems.
Install in Ubuntu liveCD or USB or Full RepairCD with Boot-Repair (for newer computers) 
[http://sourceforge.net/p/boot-repair/home/Home/](http://sourceforge.net/p/boot-repair/home/Home/)
[https://help.ubuntu.com/community/UbuntuSecureRemix](https://help.ubuntu.com/community/UbuntuSecureRemix)

---

