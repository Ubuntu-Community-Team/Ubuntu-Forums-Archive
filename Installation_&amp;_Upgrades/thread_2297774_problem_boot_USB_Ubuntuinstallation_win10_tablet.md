---
title: "problem_boot_USB_Ubuntuinstallation_win10_tablet"
date: 2015-10-06
forum: Installation &amp; Upgrades
---

### Post by PhilippL90 on 2015-10-06
Hey guys,

I got a new Tablet-PC (Xcellent 10.1 Pro XL from One.de).

I wanted to install Ubuntu 14.04.3 LTS instead of the extraordinary Win10 home. -.-
So I made a bootable USB-Stick with the Universal-USB-Installer-1.9.6.1 from Ubuntu.com.

First I tried to use the new (since win8) function to restart and start from another device. (options-restore).
But the tablet just startet the windows again.
Then I looked into the UEFI/BIOS. I made the USB-Stick (wich already was discovered) to the one and only bootdevice (set all the others to "Disable").
But again it started this wonderful Windows....

Could anybody help me with that?

Thanks, Philipp...

---

### Post by ubfan1 on 2015-10-06
Have you tried the USB you made in another computer to see if it works?

Did you md5sum check the downloaded iso?
  See [https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)
  Check the number against the listing in the link for your release listed at
  [http://releases.ubuntu.com](http://releases.ubuntu.com) under the MD5SUMS link.

---

### Post by PhilippL90 on 2015-10-07
Good afternoon ubfan1 and thanks for your reply,

Yes I tried to boot from my Laptop where already Ubuntu is installed and it worked.
So I think the iso was correctly and completely downloaded.
Of course I will test it with md5sum in a couple of minutes.

A friend of me told me to root the tablet. I searched for a toolkit or a manual but could only find tutorials for android and apple-devices.
So I now, realy don't have a clue what to do next.

kind regards,
P.Lempfer

---

### Post by ubfan1 on 2015-10-07
Some things to try:
1) Make sure the machine is 64 bit -- 32bit is a separate problem.
2) Make sure the Windows is not hibernated, asleep -- power option fast boot must be off.  (Although in Win 10, even a shutdown seems to just be a sleep, since the function keys don't work to get to UEFI settings, and you need the shift-restart from Windows to get there.)
3)Secure boot should not be a factor, but in practice, it frequently is, so turn it off.
4)Make sure your boot order has USB first.  The USB may have to be present when the order is set, and the order may reset if the USB is removed, on some machines.
5)Try the EFI menu to boot the USB (I think you've already tried this, but try again after the above).
6)If you can get to the grub menu, and then turn black, it's a video problem, try options like "nomodeset" (from a function key) to get a successful boot and then install a proprietary video driver.

---

### Post by Null_Sieben on 2016-06-18
@Phillip: Did you get Ubuntu running on the tablet?

---

