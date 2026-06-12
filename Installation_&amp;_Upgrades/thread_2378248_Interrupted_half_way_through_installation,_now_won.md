---
title: "Interrupted half way through installation, now won't boot into Windows either"
date: 2017-11-21
forum: Installation &amp; Upgrades
---

### Post by akino321 on 2017-11-21
I was installing Ubuntu on a Windows 10 laptop from a Live USB as dual boot but I lost power half way through the installation.

Now when I turn on the PC sometimes it goes into Grub but if I select Ubuntu it hangs on the start screen with the dots and loads forever.

Other times I just get a boot menu with the options of Ubuntu, Windows Boot Manager etc, but when I click on these nothing happens.

I can still go into the Live USB Ubuntu, but if I try to install Ubuntu again, the 'installation type' screen doesn't show any devices so I can't proceed.

When I try running 'Check disc for defects' it comes up with this error a lot:

COMRESET failed (errno=16)

Is there anything I can do?

---

### Post by yancek on 2017-11-21
If the installation of Ubuntu did not complete, I doubt very much you will boot it from the hard drive.

What did you do immediately after the power outage?  Re-boot the install usb?  Try to boot Ubuntu on the hard drive?  Try to boot windows?
Who is the manufacturer of the computer?  Do you know how to select boot options in the BIOS or access the BIOS to set boot priority?
Boot the Live USB and select the Try Ubuntu option and when you get to the Desktop, open a terminal and run this command, post the output here:

```
sudo gparted
```

---

### Post by oldfred on 2017-11-21
You may need BIOS/UEFI and/or SSD firmware updates.

[https://bugs.launchpad.net/ubuntu/+source/linux-meta/+bug/150259/comments/27](https://bugs.launchpad.net/ubuntu/+source/linux-meta/+bug/150259/comments/27)

---

