---
title: "ubuntu not booting after installation on pc!"
date: 2023-04-09
forum: Installation &amp; Upgrades
---

### Post by kelvinakom on 2023-04-09
Hello, My Ubuntu is not booting after installation. The boot repair send me this: [https://paste.ubuntu.com/p/4ZJgrKctp7/](https://paste.ubuntu.com/p/4ZJgrKctp7/)
to send to expats to help me.
please some one help me.

---

### Post by tea for one on 2023-04-09
[COLOR="#0000FF"]Line 68[/COLOR] - OS#1:   Ubuntu 22.04.2 LTS on sda3
[COLOR="#0000FF"]Line 69[/COLOR] - OS#2:   Ubuntu 22.04.2 LTS on sda4

[COLOR="#0000FF"]Line 80[/COLOR] - The firmware seems EFI-compatible, but this live-session is in Legacy/BIOS/CSM mode (not in EFI mode).
You have installed Ubuntu 22.04 twice in Legacy mode yet your PC is compatible with UEFI.

I would back up my data and start over with a fresh install of Ubuntu 22.04 in UEFI mode with GPT.

Are you familiar with the advantages of UEFI OS installations?

---

### Post by kelvinakom on 2023-04-09
No i'm not, can you please direct me on how to do it?

---

### Post by tea for one on 2023-04-10
_GPT_
Allows more than 4 primary partitions
Easier to manipulate partitions
More robust
Essential for new installations of Windows 10/11
Required for larger disks i.e. 2TB and above
[U]
UEFI mode[/U]
Improved boot speed
More security options available
Boot OS from one-time boot menus (rather than just boot a particular disk)
Other boot utilities available I.e. rEFInd
Generally able to (emergency) boot via EFI shell
Essential for new installations of Windows 10/11

If you are going to re-install, then can you confirm:-
You have backed up your data
You are able to access UEFI settings and disable Legacy boot
You can boot the Ubuntu 22.04 installer in UEFI mode (i.e. UEFI followed by colon followed by disk description)

According to the boot-repair report, your disk is already GPT (see line 94)

---

### Post by yancek on 2023-04-10
What does "not booting" mean in your case?  What exactly happens when you try to boot, warning or error messages?

As pointed out, you have a GPT drive and you have both a BIOS Boot partition(sda1) which is needed to do a Legacy install on a GPT disk.  You also have an EFI partition (sda2) which is used for an EFI install on a GPT disk which is the preferred method.

Line 162 shows the UUID for sda4 which if you set the computer to boot UEFI (disable Legacy/CSM) it should boot Ubuntu on sda4 as that is the UUID for sda4 (see line 145).  You have the standard EFI files for Ubuntu showing on sda2 beginning at line 28 - 36.

Have you tried to boot with Legacy/CSM on?  Have you tried with it disabled?  What are the results of each?

If you have disabled Legacy/CSM and tried to boot and failed then I would agree with the post above to boot in UEFI mode and install that way.  Make sure the BIOS boot partition is deleted.

---

### Post by kelvinakom on 2023-04-10
Thanks very much let me try and get back to you.
I'm new in this but let me try.

---

### Post by kelvinakom on 2023-04-10
when i turn the pc on, it will just show a blank screen which try to light up and die down again and again.

---

