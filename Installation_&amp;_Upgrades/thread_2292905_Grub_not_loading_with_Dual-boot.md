---
title: "Grub not loading with Dual-boot"
date: 2015-08-31
forum: Installation &amp; Upgrades
---

### Post by nathan85 on 2015-08-31
So, I have an HP machine that has been upgraded to Windows 10. After the Windows 10 upgrade I decided to dual boot Ubuntu 15.04. I was able to get this all working and Grub2 would work. Today, I needed more space on the Ubuntu partition so I shrunk my Windows 10 partition and filled the space with the Ubuntu partition. I knew that this would likely break the boot but was going to use boot repair to fix it. I have run boot repair several times now but Grub will not load, instead the machine boots directly into Windows 10. I have confirmed that I can still boot into my Ubuntu partition by bringing up the UEFI boot menu and selecting the first (of many) ubuntu items listed. I ran the additional command on my windows machine to change the bootmgr to grubx64.efi but that has not seemed to help. I have tried to research this but am not finding a solution so I am not sure what else to do to get this working again. Please help.

My boot repair link is [http://paste.ubuntu.com/12242897/](http://paste.ubuntu.com/12242897/)

and my windows 10 bcdedit list is as follows:

Windows Boot Manager
--------------------
identifier              {bootmgr}
device                  boot
path                    \EFI\ubuntu\grubx64.efi
description             Windows Boot Manager
locale                  en-US
inherit                 {globalsettings}
resumeobject            {1f8184a2-14de-11df-9734-f08c6d8c50b0}
displayorder            {current}
toolsdisplayorder       {memdiag}
timeout                 10


Windows Boot Loader
-------------------
identifier              {current}
device                  partition=C:
path                    \Windows\system32\winload.efi
description             Windows 10 Pro
locale                  en-US
osdevice                partition=C:
systemroot              \Windows
resumeobject            {f2880ab4-5077-11e5-82fc-806e6f6e6963}
bootmenupolicy          Standard

---

### Post by ubfan1 on 2015-09-01
Take a look at the UUID used in the grub.cfg stub file, that's the one in the EFI partition /EFI/ubuntu/grub.cfg  (mounted at /boot/efi/EFI/ubuntu/grub.cfg in the running system).  You might have an old one in use and need to use the current one 
d20d3c58-2837-4020-8c72-e824ca1f91fc
The /boot/grub/grub.cfg seems to have the right one.

---

### Post by nathan85 on 2015-09-01
I checked this file and the uuid is what you said it should be.

---

### Post by oldfred on 2015-09-01
Most with HP have needed to copy all the ubuntu efi files into /EFI/Boot and rename either grub or shim to bootx64.efi. Then boot hard drive entry in UEFI.

       [http://ubuntuforums.org/showthread.php?t=2234019](http://ubuntuforums.org/showthread.php?t=2234019)

Also more details on cp commands in link in my signature.

---

### Post by nathan85 on 2015-09-01
Thanks so much for the help. That has solved my problem. Writing this down so I can remember for the future.

---

