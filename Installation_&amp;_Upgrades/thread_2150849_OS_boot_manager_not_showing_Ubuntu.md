---
title: "OS boot manager not showing Ubuntu"
date: 2013-06-02
forum: Installation &amp; Upgrades
---

### Post by brfc1 on 2013-06-02
I just got a brand new hp pavilion g6 and i want to run win 8 and ubuntu side by side. I booted ubuntu from a cd and installed it all right. Then i tampered with a partition that was supposedly ubuntu's(the partition was empty when i looked at it in win 8). So i booted again and now in the boot options there are two ubuntu entries and one works. But the thing is the pc doesn't ask me which os to go for. I am having to go to the boot manager every time my pc starts to get to ubuntu. Is there a work around this? I tried enabling/disabling legacy and the safe mode alternatively and it didn't work. I also need to get rid of the dummy ubuntu entry in the boot menu from my previously failed installation.

So please help me out here. I am at a loss. Shall be thankful.

Best regards

---

### Post by ohnonot on 2013-06-04
welcome to the forums brfc1!

don't you have to go to the boot manager (grub) anyway to start ubuntu?
where exactly do you dis/enable legacy and safe mode?
what exactly was that "tampering"?
is there anything actually broken, or does grub just have an extra dummy entry?

also i think windows still doesn't recognize linux file systems.

---

### Post by Mark Phelps on 2013-06-05
The new default for Ubuntu is if it is the ONLY OS on the drive, it does NOT put up a menu anymore. Since, as you said, there are no options in the menu for Windows, it does not know that Windows is on the drive. 

Also, your PC, being new, most likely uses UEFI BIOS -- and installing in that is a LOT more complicated than just sticking in Ubuntu media and running the installer.

Not a UEFI expert, so you will need to wait until one comes along to find out how to fix this.  Most likely, you will need to remove the Ubuntu install, make some configuration changes to your boot setup, and reinstall it -- properly this time.

---

### Post by brfc1 on 2013-06-09
Hey,  Thanks for the replies. Yes, my pc does infact run the UEFI setup and i read that it can be a real pain. In regards, to your question, i change the legacy/safe mode in the main bios setup. I can see that i screwed up the installation somehow. So, can someone please tell me how do i go about installing it cleanly in UEFI systems?  Shall be thankful

---

### Post by oldfred on 2013-06-10
See my signature, but procedure is primarily this and Boot-Repair to make fixes:
 Shows install with screen shots.
[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

If you have an install already, Boot-Repair may be able to fix it up. It will convert a BIOS Ubuntu install to UEFI by uninstalling grub-pc and installing grub-efi or the signed version if you need that.

Does your Windows boot with secure boot off? Some do and some do not. And some only boot the Windows efi file which is not per UEFI standard, but Boot-Repair can rename grub's secure boot shim file to be the Windows file so you can dual boot.

---

