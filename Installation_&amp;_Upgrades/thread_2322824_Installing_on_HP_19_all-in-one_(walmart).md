---
title: "Installing on HP 19 all-in-one (walmart)"
date: 2016-04-30
forum: Installation &amp; Upgrades
---

### Post by J_Templeton on 2016-04-30
I bought the above mentioned system about two years ago and was unable to install LinuxmintMATE.  Since I don't use computers much anymore I decided to live with it, but I am tired of MS Windows and want to install Ubuntu Mate.  I've got the DVD burned but am having trouble getting it to boot from the disk.  I don't normally buy PCs from Walmart but did so on a lark (wish I hadn't and never will again).  Is there something about this PC that prevents users from installing an alternative OS?  What might you recommend I try?  My first PCs were hand-built and it seems these newfangaled bobbers are a different beast altogether than they were even as little as six years ago.

Regards,
James

---

### Post by kansasnoob on 2016-04-30
If this documentation is right I think it's possible to run Ubuntu on that hardware:

[http://support.hp.com/us-en/document/c04094869](http://support.hp.com/us-en/document/c04094869)

[http://www.ubuntu.com/certification/catalog/component/dmi/4458/dmi%3AAMDE1-2500APUwithRadeon%28TM%29HDGraphics/](http://www.ubuntu.com/certification/catalog/component/dmi/4458/dmi%3AAMDE1-2500APUwithRadeon%28TM%29HDGraphics/)

[http://www.ubuntu.com/certification/hardware/201309-14204/](http://www.ubuntu.com/certification/hardware/201309-14204/)

What exactly happens when you try to boot the Live DVD?

---

### Post by J_Templeton on 2016-04-30
Thanks for the reply.  I changed the boot order but it seems to skip the DVD and boot the HD instead.  If memory serves, this might have something to do with the quick boot feature but I don't recall how to change that (couldn't find it BIOS).  I know the disc is good because I reviewed it from Windows.

---

### Post by yancek on 2016-04-30
Which windows version do you have installed?  If it is 8 or 10, it probably is UEFI.  Check the Ubuntu documentation on how to dual boot with windows using UEFI.

 [https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

Disable anything relating to fastboot or hibernation.  How did you burn the iso to the DVD?  You need to select the option to "burn as an image" to make it bootable.  Have you tested it in another computer to see if it boots to eliminate that as a problem?

---

### Post by J_Templeton on 2016-04-30
Yes, I believe it may have something to do with UEFI.  When purchased in 2014 I remember I did disable it but was having some other trouble at the time.

Running 10 presently and do not want to dual boot.  Thanks for the link--will check it out.

Definitely burned as image; double-checked after it was done to review the contents.

---

### Post by kansasnoob on 2016-04-30
> Running 10 presently and do not want to dual boot.

Assuming you have enough disc space I would just in case you encounter major problems with Ubuntu Mate so you'd still have an OS to fall back on :)

That aside, many of the newer puters I've messed with lately require selecting the proper key combo during boot to display the UEFI boot menu in order to boot from either DVD or USB. Most commonly pressing either Esc or F11 will display a menu with bootable devices. But the proper key(s) to press vary from computer to computer.

---

### Post by lisati on 2016-05-01
Whether you go dual-boot or Ubuntu only, I'd also recommend making sure you've got recovery disks available, just so you've got something to go back to should the need arise. If this is like other HP/Compaq products I've used, there's probably a tool preloaded within Windows to help with this.

---

### Post by RobGoss on 2016-05-01
Hello and welcome, The newer machines require UEFI and in most cases you're going to have to select the right mode ti install Ubuntu

The new machines have **UEFI or legacy.** In any case if you're trying to just install Ubuntu alone here is a simple tutorial that might help

[http://www.ubuntu.com/download/desktop/install-ubuntu-desktop](http://www.ubuntu.com/download/desktop/install-ubuntu-desktop)

As long as you're not trying to dual boot this method should be suffice

---

### Post by J_Templeton on 2016-05-01
I have successfully installed Ubuntu MATE but upon reboot it displays a no operating system message.  I did a basic install and let the installer choose the UEFI options.  Both secure boot and quick boot are disabled.  There is no option in BIOS for Intel Smart Response Technology so I assume it does not apply to my machine.  I reboot with disk and installed and run Boot Repair.  From the URL I get this link: [http://paste2.org/DYtJPd6M](http://paste2.org/DYtJPd6M)  Apparently no boot loader is installed and when booting from the live disc it says something about "no boot.efi" (I don't recall exactly what it read as).

From the UEFI link above, I am getting ready to try the steps listed under the heading Converrting Ubuntu into UEFI or Legacy mode.  Is that what I should try?  How might I install a boot loader?

---

### Post by J_Templeton on 2016-05-01
Poking around I realised that I have a fat32 partition; might that be the problem? EDIT: According to gparted I do have an EFI partition (the fat 32) but boot repair does not see it.  Maybe I need to convert to legacy?  Boot repair does not have an entry under the GRUB location tab.

---

### Post by kansasnoob on 2016-05-02
I don't know diddly about encrypted installs, which appears to be what you have, so I can't help but I'll give you a free bump.

IMHO you may want to open a new thread now because people will read your OP and assume you're still having trouble getting the live DVD to boot. Maybe a new thread titled "New 16.04 encrypted install fails to boot" :)

---

### Post by J_Templeton on 2016-05-02
Thank you all for the input.  I have solved the problem: I reinstalled without encryption and disabled the secure boot option in Boot Repair. Worked like a charm!  Apparently disabling secure boot in BIOS is not enough and the option was not available in Boot Repair with the encrypted install.  I am so happy to Linux back!  Two years I have suffered with Windows 8/10.  Prior to that I had been windows free since 2003, so you can imagine the frustration of MS hijacking the computer to update merely because it had been a few days since I last boot it up.  NEVER AGAIN!

---

