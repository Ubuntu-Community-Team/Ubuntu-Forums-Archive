---
title: "Ubuntu CD won't boot for reinstall"
date: 2005-05-11
forum: Installation &amp; Upgrades
---

### Post by snackzilla on 2005-05-11
Hi--

I just got Ubuntu installed but I got an error message when I first logged in saying Ubuntu is configured incorrectly. Now I can't access certain areas of GNOME like User Groups, Login Setup, Synaptic, Root Terminal, etc.. 

Now I think it's best to just reinstall Ubuntu, but it won't boot from the CD-ROM. I configured my BIOS to boot form CD-ROM first and it still didn't make any difference. Now I think this may be a GRUB issue. Is there any way to solve this? Thanks.

---

### Post by James Wilford on 2005-05-11
[QUOTE=snackzilla]Hi--

I just got Ubuntu installed but I got an error message when I first logged in saying Ubuntu is configured incorrectly. Now I can't access certain areas of GNOME like User Groups, Login Setup, Synaptic, Root Terminal, etc.. 

Now I think it's best to just reinstall Ubuntu, but it won't boot from the CD-ROM. I configured my BIOS to boot form CD-ROM first and it still didn't make any difference. Now I think this may be a GRUB issue. Is there any way to solve this? Thanks.[/QUOTE]
 What happens exactly when you try to boot from CD? Does the system ignore the CD entirely, or does it attempt to boot from it and fail? You could try the live CD as a test (or any other bootable CD) to see if its your CD or your system that has a problem.

If you get as far as the boot prompt on the CD, try pressing F1 for some advanced boot options. I had to use "linux noapic nolapic" on my machine otherwise it would hang after "uncompressing linux".

James

---

### Post by snackzilla on 2005-05-11
First of all, thanks for the reply.

> What happens exactly when you try to boot from CD? Does the system ignore the CD entirely, or does it attempt to boot from it and fail? 

The Ubuntu CD is ignored completely at boot time. I'm using just the Ubuntu install CD, not the live CD. I'll try using Knoppix and see if it will work, and if it does, I'll wipe out my Ubuntu partition and start over agian.

---

