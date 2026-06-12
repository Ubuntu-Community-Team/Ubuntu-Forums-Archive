---
title: "Boot-repair-disk Clean Install won't reboot even after fixing"
date: 2015-03-17
forum: Installation &amp; Upgrades
---

### Post by Bo_Jangles on 2015-03-17
Hi everyone, I'm new to linux, and the forums. I installed ubuntu, and it went swimmingly up until restarting the computer, and then it gave me the error message, "Reboot and select proper boot device or insert media in selected boot device and press a key." I created and ran Boot-Install-Repair disk, and it said it fixed the problem and gave me this url in case it didn't work, which it didn't:

[http://paste.ubuntu.com/10612776/](http://paste.ubuntu.com/10612776/)

It indicated I shoud post it in a forum for someone more intelligent than I. Thanks in advance for your help!

---

### Post by oldfred on 2015-03-17
You used the full drive LVM with encryption install. Is that what you intended?
Did you give pass phrase to Boot-Repair when it tried to mount the encrypted / (root) partition inside the LVM.

I do not know LVM nor encryption.
But some systems only boot Windows in default UEFI mode. Some require you to separately autorize/enable booting of something other than Windows. Some of those require a separate UEFI password to allow you to enable just about anything (never ever lose that password if required).
And some only boot Windows and we have to make it think it is booting Windows when it really is just booting grub/ubuntu.

If you cannot otherwise enable ubuntu entry in UEFI, you can do this since you do not have Windows. You must boot live installer in UEFI mode and use efibootmgr. If 
 
 sudo efibootmgr -c -L "Windows Boot Manager" -l "\EFI\ubuntu\shimx64.efi"

The internal checks that some vendors have done to UEFI (against UEFI standard) to only boot Windows then work but it really loads shim version of grub to boot.

You have secure boot on. Ubuntu should work if using the version of grub that is shim as above. If you turn secure boot off, either shimx64.efi or grubx64.efi should work.

---

### Post by Bo_Jangles on 2015-03-17
Thank you oldfred! I ran the script you mentioned in the terminal in boot-repair, then rebooted the computer and it booted in my ubuntu install! From what you described, it seems like for this particuar problem I could have ran the script in any terminal, so no need to have used Boot-repair (i.e. the "try without installing ubuntu" option on the ubuntu installation startup disk. For the next person with this issue, this was the script I ran:

 sudo efibootmgr -c -L "Windows Boot Manager" -l "\EFI\ubuntu\shimx64.efi"

Thanks again oldfred!

---

### Post by oldfred on 2015-03-17
Glad that worked for you.

Yes, it should work in any terminal if booted in UEFI mode.

---

