---
title: "Grub repair failed. Report Attached"
date: 2014-05-28
forum: Installation &amp; Upgrades
---

### Post by amer-l on 2014-05-28
Hello guys,

I'm on HP 655.

I have pre-installed windows 8. I installed Ubuntu 14.04 after creating an empty partition in windows 8.

After successful installation, my grub failed to install because I couldn't see any menu while booting.

I tried ubuntu repair ISO boot disk but it failed and generated this report for me.
[http://paste.ubuntu.com/7538983/](http://paste.ubuntu.com/7538983/)

Can anyone please check and let me know how can I fix it?

Thanks

---

### Post by grahammechanical on 2014-05-28
Were you connected to the internet when you ran boot repair? I ask because the says that it could not access certain Ubuntu archives and that could be the reason why the repair failed.

Regards.

---

### Post by oldfred on 2014-05-28
You also have a HP which seems to have issues. 

Others have posted this:

 It seems hp firmware do not allow you to boot anything other than windows. Hence no ubuntu option in the UEFI. To work around it
1) press esc key while booting to access start up menu 2) press F9 for boot devices menu. 
[SOLVED] Trying to install Ubuntu as dual boot on Windows 8.1 desktop HP500
[http://ubuntuforums.org/showthread.php?t=2218154](http://ubuntuforums.org/showthread.php?t=2218154)
HP Envy 17  zero brightness, use f3 to change
acpi=off  worked for HP2000
HP Envy M6
[http://askubuntu.com/questions/346257/install-alongside-windows-8-is-not-working](http://askubuntu.com/questions/346257/install-alongside-windows-8-is-not-working)
HP Envy - Legacy boot seems to mean either UEFI or Legacy depending on which is found to boot from
[http://ubuntuforums.org/showthread.php?t=2167063](http://ubuntuforums.org/showthread.php?t=2167063)
Installing Ubuntu on HP Envy-6  Details of what worked post #11
[http://ubuntuforums.org/showthread.php?t=2123975](http://ubuntuforums.org/showthread.php?t=2123975)
HP 4545s Secure boot off, manually copy files.
[http://ubuntuforums.org/showthread.php?t=2133796](http://ubuntuforums.org/showthread.php?t=2133796)
HP Manually renamed files to make it work.
[http://ubuntuforums.org/showthread.php?t=2131886](http://ubuntuforums.org/showthread.php?t=2131886)

---

### Post by amer-l on 2014-05-29
Hello all,

Thanks for your help!

I have successfully managed to repair my GRUB.

The Issue:
My hard disk partition type was GPT and I was trying to repair GRUB for MBR.

The Solution:
I was selecting the legacy boot type from my SETUP (by pressing ESC key first and then F-10 key, on boot) that's why it was trying to repair for MBR type hard disk. I just turned on the secure boot option and disabled the legacy boot and booted with my GRUP Repair USB and then repaired the grub. It went smooth as silk!

---

