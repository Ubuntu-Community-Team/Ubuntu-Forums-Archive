---
title: "UEFI not recognising Ubuntu"
date: 2012-11-14
forum: Installation &amp; Upgrades
---

### Post by r123 on 2012-11-14
I had never heard of UEFI before yesterday. So I carefully followed the guide here, using 64 bit Ubuntu: [https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

It just boots straight into Windows as if Ubuntu doesn't exist.

When I enter my BIOS settings, there is no way to turn UEFI off. The PC came with Windows 8, but no reinstall CD, and as it's a work computer my boss wouldn't be too pleased if I ruined Windows.

[http://paste.ubuntu.com/1355707/](http://paste.ubuntu.com/1355707/)

I tried the Boot-Repair option, it ran successfully. However the last screen that mentions something about an EFI file and reminds us not to forget to do something about the file (but never really specifies what). I looked in the BIOS and there are no options that touch the file.

What should I do?

Thank you

---

### Post by oldfred on 2012-11-14
You do not want to turn UEFI off as then you break Windows. It is installed in UEFI mode probably with secure bit turned on. 

Ubuntu 12.10 with grub2 2.00 should install to a Windows 8 computer with UEFI secure bit on or off. Several have reported it just works either way when correctly installed in UEFI mode.

Have you gone into UEFI and chosen the ubuntu entry from the UEFI menu?

It looks like Boot-Repair added the correct efi chain entry to Windows from the grub menu, so if you boot Ubuntu by default it should work and give you a choice to boot Ubuntu or Windows.

Best not to install to a work computer unless you have specific permission. You can install to a separate USB drive if you can access BIOS to change boot order, but many computers are locked down by administrators so users cannot do anything.

---

### Post by r123 on 2012-11-14
Thank you for your response.

The difficult part is this: "Have you gone into UEFI and chosen the ubuntu entry from the UEFI menu?"

Where do I find the UEFI menu. When I enter the BIOS settings there are no options to change the UEFI. It's as if it's designed only to boot Micro$oft.

Rest assured, I'm developing software, so we can do whatever we like within reason. Removing Windows 8, although perfectly reasonable in Jesus' eyes, would not be in my boss' ;-)

---

### Post by oldfred on 2012-11-14
There should be a place. Not sure if you then do have to turn secure boot off to get the choice.

One user posted this (but was older version) and every vendor's UEFI is a bit different.

> Enter your UEFI menu, select "Boot maintenance manager", then "Boot options", then "Add boot option", then "NO VOLUME LABEL,....Primary,Slave...1, GPT,..", then browse the /EFI/ubuntu/ folder via the UEFI boot menu, and select the grubx64.efi . Give it the name you want (eg "Precise"), then "Commit Changes and exit", then Enter. 


---

### Post by r123 on 2012-11-14
Thank you again. After enabling the boot menu, I can see ubuntu as an entry when I hit F12 (upon turning on the computer), and it works!

However after restarting, that option disappears from the menu until I re-run Boot-Repair. Any idea why?

---

### Post by oldfred on 2012-11-14
I have BIOS, but f12 is a one time boot key to let me leave one Hard drive as boot drive, but for just one boot choose the CD, USB, or other hard drive. It does not change BIOS order. I think UEFI is the same. You have to change the default boot from Windows to Ubuntu.

---

### Post by r123 on 2012-11-14
Thank you again for your help!

There are no UEFI options. I tried this: [https://help.ubuntu.com/community/UEFIBooting#Make_the_firmware_launch_GRUB2_.28U.29EFI_as_default](https://help.ubuntu.com/community/UEFIBooting#Make_the_firmware_launch_GRUB2_.28U.29EFI_as_default)

It worked. However, it appears to automatically get deleted the next time I restart. UEFI security is disabled.

What would happen if I erase the EFI partition and let Ubuntu make a new one. Would beloved windows be gone forever or would GRUB pick it up?

---

### Post by oldfred on 2012-11-14
Do not erase efi partition. Each system writes its boot files into the efi partition. Boot_Repair may copy or add some but you need the Windows files.

Post a new link to BootInfo report so we can see where you are at.

---

### Post by r123 on 2012-11-15
This one is before I did a repair: [http://paste.ubuntu.com/1360363/](http://paste.ubuntu.com/1360363/)

EDIT: My boss has instructed me not to waste time on it and given me another PC. Just as a last word, this thread: [http://forum-en.msi.com/index.php?topic=153411.0](http://forum-en.msi.com/index.php?topic=153411.0) - the symptoms are exactly the same as I was experiencing. I am not sure if it was an MSI motherboard I had, but this is certainly concerning.

---

