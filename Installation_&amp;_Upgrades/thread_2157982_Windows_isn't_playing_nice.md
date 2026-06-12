---
title: "Windows isn't playing nice"
date: 2013-06-27
forum: Installation &amp; Upgrades
---

### Post by tommyss4l on 2013-06-27
I have two separate hard drives in my computer, one Ubuntu and one Windows 7. I just reinstalled Windows 7 and now on my Ubuntu drive I'm getting this message in the boot up screen:

Loading operating system... 
Error: file not found
Grub rescue>

Help? I have no idea what happened. Thank you in advance

---

### Post by kc1di on 2013-06-27
Hello,

It's likely the When you reinstalled win 7  it over wrote your MBR.  So grub can no longer find a boot file. 

you should be able to fix it by running boot-repair found [here:]("https://help.ubuntu.com/community/Boot-Repair")

just follow the instructions on the page. 
good luck

---

### Post by Mark Phelps on 2013-06-27
> **tommyss4l said:**
> I have two separate hard drives in my computer, one Ubuntu and one Windows 7. I just reinstalled Windows 7 ...

Advice -- whenever you have two different OSs on two different physical drive, the BEST approach, when you're updating or reinstalling one of the OSs, is to disconnect the OTHER drive.  That way, you don't run the risk of overwriting boot folders or files, or MBRs.

But, that said, the errors you're getting are confusing ...

You have two MBRs, one on each drive.  Typically, what you do is install each OS to its own drive, and each OS's boot loader to that same drive.  Thus, when you boot from the Win7 drive, you go straight into Win7; when from the Ubuntu drive, straight into Ubuntu.  IF you then do an "update-grub" on the Ubuntu drive, and boot from it in the future, you will get a GRUB menu with entries for Ubuntu and Windows.

This presumes the MBR on the Win7 drive still points directly to Win7, with no GRUB code in it.  Thus, if you simply overwrote the MBR on the Ubuntu drive from Win7, and you continued to boot from that drive, you would boot directly into Win7 -- and would literally have no way to boot into Ubuntu at all, as the Win7 drive MBR did not have GRUB code.

The error messages you're getting generally happen when GRUB code is in the MBR but when it tries to launch the GRUB modules in a Linux partition, it can't find them.  That's not an MBR problem per se; that's a problem with no GRUB modules.  This typically happens when you install Ubuntu to an external drive but install GRUB to an internal drive.  When you remove the external drive and boot, GRUB can't find it's modules because the external drive containing them is missing.

---

