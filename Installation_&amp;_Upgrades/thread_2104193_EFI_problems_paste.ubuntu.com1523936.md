---
title: "EFI problems: paste.ubuntu.com/1523936"
date: 2013-01-12
forum: Installation &amp; Upgrades
---

### Post by dreycon on 2013-01-12
I bought a Portege Z935-P390

ran into the secure boot problem so I installed Ubuntu-Secure-Remix-64bit

never saw a grub menu on reboot, it just booted windows *unless* I had my installation USB inserted in which case it booted my Ubuntu install

Ran Boot-Repair

Then, I just get the nice Toshiba flash screen and the machine freezes  no OS

Insert my USB stick and now it boots from the stick instead of my Ubuntu installed on the hard drive

Ran Boot-Repair again:

paste.ubuntu.com/1523936

but same problem: frozen at splash screen, no grub menu, and no OS ever starts

note there was some crazy message about telling my BIOS to point to some file on sda2, but I don't have a BIOS that's my whole problem, right?

---

### Post by dorruk on 2013-01-12
Partition tables may be broken.. That would explain why your computer doesn't accept any OS on your HDD but only boot from USB.

Have you considered running testdisk from terminal?

Note: You do have a BIOS. If you didn't have one, then you couldn't boot anything at all. :D

---

### Post by oldfred on 2013-01-12
You need to go into  UEFI/BIOS (they are the same, just UEFI is new) and from UEFI menu choose to boot ubuntu entry. Then grub menu will have entry to chain load back to the Windows efi boot entry.

Every computer is different. Microsoft lists many ways to get into UEFI:
       UEFI/BIOS Boot keys - about halfway down on this Microsoft page
[http://social.technet.microsoft.com/wiki/contents/articles/12911.tips-for-configuring-your-bios-settings-to-work-with-windows-to-go.aspx](http://social.technet.microsoft.com/wiki/contents/articles/12911.tips-for-configuring-your-bios-settings-to-work-with-windows-to-go.aspx)

---

### Post by YannBuntu on 2013-01-12
> **dreycon said:**
> Ran Boot-Repair again:

[http://paste.ubuntu.com/1523936](http://paste.ubuntu.com/1523936)


You have SecureBoot enabled.
I would follow the 1st paragraph of [https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI) :
1) disable SecureBoot / FastBoot /QuickBoot in your BIOS
2) then run Boot-Repair, and tell us the new URL that will appear
3) reboot and tell us what you observe

---

### Post by dreycon on 2013-01-14
OK, problem is Windows doesn't always shut down when you tell it to shut down.  Now that I was reasonably sure it was F2 and not something else, repeated shutdowns and restarts with constant pressings of F2 eventually got me into the BIOS.  Yippee!!!

Have now turned off Secure Boot, Intel Rapid Start Technology, Anti Theft technology and left UEFI Boot on

Now Boot-Repair gave lots of commands to cut and paste into the terminal and ALL IS WELL! :)

Kudos!  Thanks!

---

