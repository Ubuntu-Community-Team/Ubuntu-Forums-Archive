---
title: "Trouble uninstalling UNR 9.10 from native XP system"
date: 2009-11-19
forum: Installation &amp; Upgrades
---

### Post by hydrurga on 2009-11-19
Hi there,

I run an XP system normally on my Samsung N140 but thought I would give Ubuntu Karmic a shot. I downloaded UNR and installed it under Windows, no problem. After testing it, I then decided to uninstall UNR (I'm going to go down the virtualisation route instead) - I used the Windows Add/Remove Programs functionality to do this. One small problem - the boot loader screen giving me the choice between XP and Ubuntu still shows on netbook startup (although obviously selecting Ubuntu causes it to complain and do nothing) - not a very good state of affairs. How do I get rid of this dual loader? I don't mind reinstalling UNR and re-uninstalling it again in a different manner if that's what it takes.

Thanks guys.

---

### Post by cariboo on 2009-11-19
Use your windows install disk to go to the Windows Recovery Console and run FIXBOOT and FIXMBR. If you don't have an install CD you can use [SuperGrub Disk]("http://www.supergrubdisk.org/") to restore the mbr.

---

### Post by hydrurga on 2009-11-19
> **cariboo907 said:**
> Use your windows install disk to go to the Windows Recovery Console and run FIXBOOT and FIXMBR. If you don't have an install CD you can use [SuperGrub Disk]("http://www.supergrubdisk.org/") to restore the mbr.

Thanks Cariboo. My machine's a netbook, so lacking in CD drive. So, given that I can't use an install disk, are you saying that I have to reinstall UNR under windows and then run SuperGrub Disk under it to restore the XP-only boot. Then reboot and uninstall UNR using Add/Remove Programs in XP?

---

### Post by hydrurga on 2009-11-20
Right, problem solved. First of all, if you want to uninstall UNR (and I imagine any other type of Ubuntu) that has been installed under Windows XP, you do it by running the Uninstall program in the Ubuntu folder on XP, NOT by using the Add/Remove Programs in the XP Control Panel.

If this is too late, and you used the latter method, I imagine that reinstalling Ubuntu and uninstalling it correctly will solve the problem. A quicker solution (if you're comfortable with it) is simply to remove the Ubuntu line from the list of the Operating Systems in XP's boot.ini (see [http://support.microsoft.com/kb/289022](http://support.microsoft.com/kb/289022) for how to do this).

---

