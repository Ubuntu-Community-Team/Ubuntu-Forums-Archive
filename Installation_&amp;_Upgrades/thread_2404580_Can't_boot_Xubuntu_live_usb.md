---
title: "Can't boot Xubuntu live usb"
date: 2018-10-25
forum: Installation &amp; Upgrades
---

### Post by arpeasal on 2018-10-25
I tried installing Xubuntu from usb, but I can’t get my machine to boot from the usb.  I used Etcher to burn the Xubuntu 18.04.1 iso to a usb but when I reboot, Windows boots up.
 
 
 I bought this machine yesterday.  It is an Acer Aspire ES 15 with a 1TB HD.  I shrank this leaving about 250 GB for the Windows 10.
 
 
 Before I did anything, I made a Windows recovery usb.
 
 
 I then installed Antergos Linux (an Arch derivative).  I can’t access this yet (the machine just boots to Windows) and I’m trying to figure out how, but that’s a different issue.  (Actually, on my old machine I had a similar problem, but when I installed Xubuntu after the Antergos, the Xubuntu Grub showed the Antergos installation, so I didn’t need to do anything else.  I’m hoping that happens this time as well.)
 
 
 Anyway, I set the boot order, I moved the Windows boot manager to the bottom of the list.  When I reboot with either my live Antergos usb or my Windows Recovery usb, the machine will boot from the usb.  But when I try the Xubuntu live usb, it just boots to Windows.  I’ve tried burning the iso to different usbs, but that doesn’t help.
 
 
 What should I do?

---

### Post by kc1di on 2018-10-26
Hello arpeasal  and Welcome to ubuntu forums, 

Try turning off secure boot if it will let you and try again.

After doing some searching this Acer model has been a problem with Linux and Ubuntu for quite some time.  [This thread]("https://ubuntuforums.org/showthread.php?t=2381169") and the Post by Oldfred may be of help.

---

### Post by arpeasal on 2018-10-26
Thanks kc1di.
Both secure boot and fast start are disabled and they were disabled when I tried booting.

---

### Post by kc1di on 2018-10-26
update the bios if possible

---

### Post by SeijiSensei on 2018-10-26
Try using [Rufus]("https://rufus.ie/en_IE.html") in Windows to make a UEFI thumbdrive.  I'm having boot troubles on an ASUS machine.  It refuses to boot from a USB in legacy mode.  It boots properly if I give it a UEFI-formatted USB drive.

---

