---
title: "Dual boot grub problems"
date: 2021-01-27
forum: Installation &amp; Upgrades
---

### Post by blacklotus767 on 2021-01-27
I have just installed a dual boot of Ubuntu 20.04.1 LTS alongside windows 10 on a Dell computer, and at first, I could only get back into windows. The Grub loader never materialized at startup. But then I used this code in a windows command prompt: bcdedit /set {bootmgr} path \EFI\ubuntu\grubx64.efi. This made it so the computer booted into Ubuntu, but no grub. Now I cannot log into Windows and there is no grub at startup. I can still see the partition in Ubuntu, can even access all the files. Is there a way for me to get grub to show up at startup without having to do this whole install all over? Thanks in advance for any help, I have very little experience with Linux.

---

### Post by yancek on 2021-01-27
After booting into Ubuntu, did you run:  sudo update-grub?  If not, do that and watch the output for a reference to windows.  You might post the output of that command here.
When you boot the computer, you should be able to enter the BIOS firmware and look at the boot options and see if there is an entry for windows which you can boot.
Did you read the Ubuntu documentation on dual booting Ubuntu with windows 10 at the link below?  If not, do that and compare the instructions there to what you actually did.

[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

If you don't get an entry for windows with the sudo update-grub command, I would suggest that you go to the site below and download boot repair using the 2nd option described on that page and run boot repair.  When you run boot repair, be sure to select the option to Create BootInfo Summary and do NOT try to make any repairs.  When it finishes you will be given a link which you can post here and hopefully get some assistance.   

[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

