---
title: "Failure to install Ubuntu alongside Windows 10 - device boot failure"
date: 2016-02-28
forum: Installation &amp; Upgrades
---

### Post by jonathan108 on 2016-02-28
Hey all,

I'm trying to install Ubuntu alongside the Windows 10 OS on my laptop, but am running into trouble, and would like some help.

I've gotten to the point where the Ubuntu installation software says that Ubuntu is successfully installed, and asks me to restart. But upon restarting, the computer boots in to Windows with no sign of Ubuntu. If I restart and go into the computers boot options mode, then it sees the Ubuntu UEFI boot option. But if I choose that option, I get the error message "boot device failed - press any key to restart".

What should I do from here? What more information do you need me to provide about my installation/system?

My installation process:
My computer is a 64bit Windows 10 installation with UEFI
I make a bootable Ubuntu USB
I boot the computer from the USB in live only mode to make sure Ubuntu works - it does
I restart the computer, boot from the bootable USB and choose the "install Ubuntu" option.
I go through the installation process (using the default method for creating new hard drive partitions) and the installer finishes successfully and asks me to restart my computer.
I can't boot Ubuntu from the boot options menu after restart - I get a "selected device failed" error.

Thanks!

---

### Post by newbie-user on 2016-03-01
You may have to disable secure boot in the bios.

---

### Post by oldfred on 2016-03-02
What brand/model system?
Did you boot and install in UEFI mode?

        Post the link to the Create BootInfo summary report. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)

---

