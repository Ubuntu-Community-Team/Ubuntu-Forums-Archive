---
title: "Live Session made Win7 unbootable"
date: 2012-08-03
forum: Installation &amp; Upgrades
---

### Post by norlandbuntu2 on 2012-08-03
I ran a live session of Ubuntu 12.04 on a Dell 745 desktop. I closed and exited properly.Afterwards the computer refused to boot returning a "This is not a bootable disk" error. Has anyone seen this before? This was NOT a failed installation attempt. Any ideas how this could happen?

---

### Post by drmrgd on 2012-08-03
Is your BIOS set to boot the Windows drive, or is it pointing to something else.  Try double checking the boot device order in BIOS just to confirm.

---

### Post by Frogs Hair on 2012-08-03
You may have to enter the Bios screen and change the boot options to include the hard drive as a bootable device . Sometimes the Bios needs to be set so the live cd will boot , but I have never heard of the Bios setting changing automatically to exclude the HDD. Methods to get in the Bios screen vary for different computer models.

---

### Post by norlandbuntu2 on 2012-08-03
The BIOS was not changed. Windows will not start even when I select hard drive from boot menu. I am concerned that something about the live session crippled Windows. The drive can still be accessed from a live Ubuntu session.

---

### Post by oldfred on 2012-08-04
Do not run any repairs, but post the link that running BootInfo creates.

Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration an diagnose advanced problems.

That will show entire boot configuration. So we can see if something is corrupted in Windows. If nothing is wrong with Windows boot files then It has to be BIOS.

---

