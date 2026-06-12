---
title: "Unable to repair boot"
date: 2015-08-01
forum: Installation &amp; Upgrades
---

### Post by blong-fiction on 2015-08-01
I was attempting to create a live usb, and picked the wrong drive, it looks like I picked my "D" drive, which was some small partition on the end of my Win7 box.

Now, my Win7 box boots to grub which is an ubuntu server install menu, and Win7 isn't listed.

I tried to use the boot repair disk, and although it says it repaired it, nothing changed.  The two previous partitions appear to be there and can be mounted.  I've tried using Windows bootrec off of a Win8 install DVD I have, still no luck.

How do I remove grub and revert this box to just Win7?

First boot repair info:
[http://paste.ubuntu.com/11978047/](http://paste.ubuntu.com/11978047/)

Current boot repair info:
[http://paste.ubuntu.com/11978258/](http://paste.ubuntu.com/11978258/)

Thanks

---

### Post by vidtek on 2015-08-01
> **blong-fiction said:**
> I was attempting to create a live usb, and picked the wrong drive, it looks like I picked my "D" drive, which was some small partition on the end of my Win7 box.

Now, my Win7 box boots to grub which is an ubuntu server install menu, and Win7 isn't listed.

I tried to use the boot repair disk, and although it says it repaired it, nothing changed.  The two previous partitions appear to be there and can be mounted.  I've tried using Windows bootrec off of a Win8 install DVD I have, still no luck.

How do I remove grub and revert this box to just Win7?

First boot repair info:
[http://paste.ubuntu.com/11978047/](http://paste.ubuntu.com/11978047/)

Current boot repair info:
[http://paste.ubuntu.com/11978258/](http://paste.ubuntu.com/11978258/)

Thanks

To repair this you will need to do a windows only fix.

With the bootrec solution, you need to do each step carefully and reboot to the dvd ***after doing each and every step***

These are the bootrec commands you need./FixMbr, /FixBoot, /ScanOs and /RebuildBcd

do them in this order.

This will take you the best part half a day, sorry, the only other way is a full windaz re-install.

best of luck, Tony.

---

### Post by blong-fiction on 2015-08-01
So, I was able to "fix" this...

It looks like it installed grub in uefi, but booting via legacy worked to boot the Windows box.  I disabled uefi boot in the bios, and it now boots to windows fine.

I did try your suggestion, though it failed with the /RebuiltBcd command with not being able to find the system or some such error message.

Not sure if any of the other things I tried to fix it were necessary or not, it's possible they fixed the bios/legacy booting, allowing the bios change to work around the uefi issue.

Thanks for the help.

---

### Post by oldfred on 2015-08-01
From Boot-Repair's report, it looks normal.

You have a Windows boot loader in MBR, you have boot flag on sda1, you have Windows boot files bootmgr & /boot/BCD in sda1 and winload.exe in sda2.  It shows Boot Sector as NTFS.

vidtek's suggestions should refresh everything, but you may also need chkdsk, which you may have to run several times or until no errors.
       Repair often does not work, some say run 3 times others recommend the command line bootrec.exe
Always run chkdsk and run again until there are no errors, that may be all that is required
chkdsk c: /b
/b includes /r
[http://technet.microsoft.com/en-us/library/cc730714%28v=ws.10%29.aspx](http://technet.microsoft.com/en-us/library/cc730714%28v=ws.10%29.aspx)

---

### Post by vidtek on 2015-08-01
> **blong-fiction said:**
> So, I was able to "fix" this...

It looks like it installed grub in uefi, but booting via legacy worked to boot the Windows box.  I disabled uefi boot in the bios, and it now boots to windows fine.

I did try your suggestion, though it failed with the /RebuiltBcd command with not being able to find the system or some such error message.

Not sure if any of the other things I tried to fix it were necessary or not, it's possible they fixed the bios/legacy booting, allowing the bios change to work around the uefi issue.

Thanks for the help.

Glad it got fixed, don't forget to mark this thread as solved

Cheers, Tony.

---

