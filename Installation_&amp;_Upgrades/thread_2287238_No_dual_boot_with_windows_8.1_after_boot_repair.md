---
title: "No dual boot with windows 8.1 after boot repair"
date: 2015-07-17
forum: Installation &amp; Upgrades
---

### Post by Sandrag on 2015-07-17
Hi, I installed ubuntu 14.04.2 on my new acer with windows 8.1 following instructions found on forums but even after running the yannubuntu boot-repair tool the linux boot manager does not appear in the bios and the laptop boot directly to windows. I disabled boot secure and fast boot before insrallation
here is the boot-repair url
[http://paste.ubuntu.com/11896226/](http://paste.ubuntu.com/11896226/)
can anyone please help me?
thank you,

---

### Post by oldfred on 2015-07-17
Acer also requires you to set a password (never lose that) and then enable trust for any other system than Windows.
       Acer E3 requires UEFI password to allow added settings Post #8
[http://ubuntuforums.org/showthread.php?t=2253311](http://ubuntuforums.org/showthread.php?t=2253311)
Aspire E1-522 InsydeH20 Bios unlock -  7 min video
[https://www.youtube.com/watch?v=7SkBFkzOW0A](https://www.youtube.com/watch?v=7SkBFkzOW0A)

 Acer Aspire ES1-512-C39M Details on password and settings to enable trust on ubuntu entries Also R14 model same fix
[http://ubuntuforums.org/showthread.php?t=2256083&p=13203044#post13203044](http://ubuntuforums.org/showthread.php?t=2256083&p=13203044#post13203044)
[http://acer--uk.custhelp.com/app/answers/detail/a_id/27071/~/how-to-enable-or-disable-secure-boot](http://acer--uk.custhelp.com/app/answers/detail/a_id/27071/~/how-to-enable-or-disable-secure-boot)
      
 Acer Aspire ES1-512: ubuntu 14LTS USB install over Windows 8.1  Set shim as secure in UEFI
black list some drivers for shutdown issues - post #9 link to Mint
[http://ubuntuforums.org/showthread.php?t=2256083](http://ubuntuforums.org/showthread.php?t=2256083)

You also have a lot of duplicate UEFI entries. Best to houseclean some of those.
       
 sudo efibootmgr -v
The "-v" option displays all the entries so you can confirm you're deleting the right one, and then you use the combination of "-b ####" (to specify the entry) and "-B" (to delete it). Examples #5 is delete:, with Ubuntu you need sudo, others must be at root.
sudo efibootmgr -b XXXX -B
[http://linux.dell.com/cgi-bin/gitweb/gitweb.cgi?p=efibootmgr.git;a=blob_plain;f=README;hb=HEAD](http://linux.dell.com/cgi-bin/gitweb/gitweb.cgi?p=efibootmgr.git;a=blob_plain;f=README;hb=HEAD)

Be sure to always boot in UEFI boot mode. It looks like you previously booted in CSM/BIOS/Legacy mode as you have grub installed to MBR for BIOS boot. But install now is set for UEFI boot, either you fixed it or Boot-Repair's updates changed it to UEFI.

---

### Post by Sandrag on 2015-07-18
Hi, thak you for your answer. The dual boot worked following instructions of 
"Acer Aspire ES1-512-C39M Details on password and settings to enable trust on ubuntu entries Also R14 model same fix
http://ubuntuforums.org/showthread.p...4#post13203044".
At the end of installation after boot-repair I sent the "efi file boot 0: yes" to the top of the list in the bios boot priority instead of the HDD as suggested in other threads and dual boot finally works.

Which of the repeated uefi entries should I remove? Now that dual boot is working I am afraid o messing out everything.
Thank you for your help,
Sandra

---

### Post by oldfred on 2015-07-18
From your Summary report, may not be changed so rerun efibootmgr -v

```
 efibootmgr -v
BootCurrent: 0001
Timeout: 2 seconds
BootOrder: 2001,000B,2002,2003
Boot0000* ubuntu	HD(2,12c800,96000,40e12e5e-4191-43fd-8f4b-09c052eccf6b)File(EFIubuntushimx64.efi)
Boot0001* USB HDD: KingstonDataTraveler G3	ACPI(a0341d0,0)PCI(14,0)USB(0,0)HD(1,1f80,ee8080,00097af4)RC
Boot0002* Unknown Device: 	HD(2,12c800,96000,40e12e5e-4191-43fd-8f4b-09c052eccf6b)File(EFIubuntushimx64.efi)RC
Boot0004* Unknown Device: 	HD(2,12c800,96000,7ee1c0c5-cfa1-4488-b32d-7482fea5df6b)File(EFIubuntushimx64.efi)RC
Boot0005* Unknown Device: 	HD(2,12c800,96000,7ee1c0c5-cfa1-4488-b32d-7482fea5df6b)File(EFIubuntushimx64.efi)RC
Boot0006* Unknown Device: 	HD(2,12c800,96000,7ee1c0c5-cfa1-4488-b32d-7482fea5df6b)File(EFIubuntushimx64.efi)RC
Boot0007* Unknown Device: 	HD(2,12c800,96000,7ee1c0c5-cfa1-4488-b32d-7482fea5df6b)File(EFIubuntushimx64.efi)RC
Boot0008* Unknown Device: 	HD(2,12c800,96000,7ee1c0c5-cfa1-4488-b32d-7482fea5df6b)File(EFIubuntushimx64.efi)RC
Boot0009* Unknown Device: 	HD(2,12c800,96000,7ee1c0c5-cfa1-4488-b32d-7482fea5df6b)File(EFIubuntushimx64.efi)RC
Boot000A* Unknown Device: 	HD(2,12c800,96000,7ee1c0c5-cfa1-4488-b32d-7482fea5df6b)File(EFIubuntushimx64.efi)RC
Boot000B* Windows Boot Manager	HD(2,12c800,96000,40e12e5e-4191-43fd-8f4b-09c052eccf6b)File(EFIMicrosoftBootbootmgfw.efi)WINDOWS.........x...B.C.D.O.B.J.E.C.T.=.{.9.d.e.a.8.6.2.c.-.5.c.d.d.-.4.e.7.0.-.a.c.c.1.-.f.3.2.b.3.4.4.d.4.7.9.5.}...4................
Boot2001* EFI USB Device	RC
Boot2002* EFI DVD/CDROM	RC
Boot2003* EFI Network	RC


```

It looks like all the unknown device entries could be deleted as they also are just booting shim which is also your ubuntu entry.

---

### Post by Sandrag on 2015-07-18
Hi I tried 
Sudo efibootmgr -b Boot0002 -B and it erase a windows boot manager from the list of efibootmgr -v but nothing happens  the unknown are still in the list and the dual boot is working.
I'll leave the installation as it is because is working.
Thank you very much
Sandra

---

### Post by oldfred on 2015-07-18
If you erased Windows you should readd it.
But you have to list and erase each of the unknows one at a time.

       This should create a new entry:
sudo efibootmgr -c -L "Windows Boot Manager" -l "\EFI\Microsoft\Boot\bootmgfw.efi"

---

### Post by Sandrag on 2015-07-18
Boot002 was one of the unknown, even though the comnand erased the windows boot manager, but in the bios the windows boot manager is still there and the dual boot is working.
Thank you very much for your help,
Sandra

---

