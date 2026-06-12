---
title: "Choosing OS loaded on next bootup"
date: 2011-08-15
forum: Installation &amp; Upgrades
---

### Post by aldaeron on 2011-08-15
I have searched around a little, but am not having a lot of luck.

I have a dual boot Win7 and Ubuntu system that is great!  I have the Windows bootloader and it works fine.  By default the bootloader chooses Win 7 and I choose Linux within 9 seconds if I want.

I am wondering if there is a way in Linux or Win 7 to set the default OS in the bootloader.  Specifically my problem relates to the fact that I want to control my PC remotely using my phone.  I sometimes leave the PC booted into one OS and want the other but since Windows is the default, I can't boot into Ubuntu remotely no matter what I do.  I have a CUDA/MPI app on Ubuntu that I like to run when I am not using my computer in person.  I have heard terrible things about MPI on Windows systems so moving my app to Windows is not something I am interested in.  Plus I am trying to get better using Ubuntu.

I am willing to change to a different bootloader if needed, but am quite new and any links to existing resources are appreciated.

Thanks!

Matt

---

### Post by Mark Phelps on 2011-08-15
Did you install using Wubi? Or did you install Ubuntu to its own partitions?

Asking because I believe the default is to boot into Ubuntu; thus, if you're booting into Win7 by default, that's likely to be a Wubi installation.

---

### Post by aldaeron on 2011-08-17
Yes I did install using Wubi.  At the time it seemed like a quick and reliable way to install.  I now have a c:\ubuntu folder I can see in Win 7 with a disks folder including root.disk (which I believe is the ubuntu file system) swap.disk (which i believe is the ubuntu swap file) and a boot folder.  It loads pretty slow and my guess is that this is because I didn't use a separate partition.

The Win 7 installer loads first.  If I choose the Ubuntu option from the Windows Bootloader Options it loads grub and I can choose to boot Ubuntu from there.

Some questions:

1) Can I get rid of the Windows Bootloader and use grub?

2) I have found how to change the default OS in the Windows Bootloader while in Windows.  Is there a way to edit the Windows bootloader in Ubuntu?

3) Can I create a partition now and move my installation over?  Will it decrease my boot time?  I have an SSD and feel like it takes forever to load Ubuntu and X.

Thanks!

-matto-

---

