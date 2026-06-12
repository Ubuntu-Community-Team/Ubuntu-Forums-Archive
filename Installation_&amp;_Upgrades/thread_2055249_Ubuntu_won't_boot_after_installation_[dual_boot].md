---
title: "Ubuntu won't boot after installation [dual boot]"
date: 2012-09-08
forum: Installation &amp; Upgrades
---

### Post by anime4eva on 2012-09-08
Hi all,

I finish installed Ubuntu 12.04 into my IdeaPad Y480 via normal boot and not UEFI. However after installation, my BIOS auto boot to Windows 7 and there is no selection to Ubuntu 12.04

I wonder what else I am missing to enable my laptop to boot into Grub2 and select which OS i want to use.

In fact, it will be very much better if my laptop could auto boot into Linux in most of the time and only boot into Windows 7 by pressing some key [if that is possible]

Likewise, I will be very grateful if anyone could enlighten me on what else need to be done to ensure Grub2 to boot instead of BIOS.

Thanks in advance!

---

### Post by oldfred on 2012-09-09
This may fix it and if not run the BootInfo report and post the link it creates.

Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration an diagnose advanced problems.

---

### Post by anime4eva on 2012-09-10
Thanks now that I can boot Ubuntu. However, when I open ADDITIONAL DRIVER, it come out 'Downloading Package Indexes failed'

I have installed Patch, Fakeroot, DKMG and STA but still no driver is detected. I also put sudo b43 ssl wl.


Is there anything else missing? My ethernet is Atheros AR8131 too. Not sure how to make them appear.. Besides that, is there any drivers that I need to make them appear too?

---

### Post by oldfred on 2012-09-10
I do not know about added drivers. May be better to start a new thread with your exact issue in the title as your issue of booting seems to be solved. Be sure to include what device is not working and details.

---

### Post by anime4eva on 2012-09-10
Thanks! Will start a new thread then.

---

