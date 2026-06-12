---
title: "Boot failure, Boot repair couldn't help"
date: 2015-08-03
forum: Installation &amp; Upgrades
---

### Post by paintsan on 2015-08-03
Hi
I have installed Ubuntu 15.04 on my Fujitsu Lifebook AH77/K, dual boot (win 8.1). I didn't get any error message during the ubuntu installation, but I can only boot windows. The boot sequence is correct and I've tried Boot Repair, but nothing changed. If I try to manually select ubuntu pressing f12, I get a "Warning: Boot Failure". Both safe boot and fastboot are disabled.

(log from boot repair: [http://paste.ubuntu.com/11994204/](http://paste.ubuntu.com/11994204/))

Can anyone help me? Let me know if you need some more information.

Thanks

---

### Post by oldfred on 2015-08-03
You may need other settings in UEFI to allow Ubuntu entry to work.

 Fujitsu lifebook ah512. Secure boot options blocked in bios - UEFI password required
[http://ubuntuforums.org/showthread.php?t=2171114](http://ubuntuforums.org/showthread.php?t=2171114)
 Fujitsu Lifebook A512 [SOLVED] Dualboot pre-installed win 8.1 and Ubuntu 14.04.1 
[http://ubuntuforums.org/showthread.php?t=2254442](http://ubuntuforums.org/showthread.php?t=2254442)

And some vendors modify UEFI to only boot Windows by description. That is not per UEFI spec. But we can copy grub or shim efi boot files into the default hard drive boot entry to make it work.
Boot-Repair also posted one of the other work arounds at the end of the report.

Details of work arounds if UEFI settings changes do not work are in link in my signature below. Or if you need detail post back.

---

### Post by paintsan on 2015-08-04
Thanks for your help, but it's not working yet. I tried these tutorial for lifebook you indicated me, but after running  the command "bcdedit /set "{bootmgr}" path \EFI\ubuntu\grubx64.efi" even windows won't start. Is there a way to undo that?
Thanks

---

### Post by oldfred on 2015-08-04
Another entry in BCD should not prevent Windows from booting.
Are you still booting in UEFI mode. Secure boot on or off should not matter.

And the only way to edit BCD is using Windows repair tools. Either f8 when you boot if that works, or your Windows repairCD or flash drive.
Most Windows repairs cannot be done from Linux. 
I do not think any Linux repairs can be done from Windows.

---

