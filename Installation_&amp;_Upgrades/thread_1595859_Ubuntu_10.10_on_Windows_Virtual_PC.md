---
title: "Ubuntu 10.10 on Windows Virtual PC"
date: 2010-10-13
forum: Installation &amp; Upgrades
---

### Post by vicky_buddie on 2010-10-13
I've downloaded the Ubuntu 10.10 desktop 64bit iso and was trying to install it under Windows Virtual PC. This is what I did so far - 


[LIST=1]
[*]Created a new Virtual Machine.
[*]In the 'DVD drive' configuration, I selected the downloaded Ubuntu iso.

[IMG]http://i145.photobucket.com/albums/r211/vicky_dear1/Gizmo/Clipboard03.jpg[/IMG]
[*]

Started the new 'Ubuntu' virtual machine.
[*]Got the following boot screen -

[IMG]http://i145.photobucket.com/albums/r211/vicky_dear1/Gizmo/Clipboard01.jpg[/IMG]
[*]But immediately after this, I got the following error screen -


[IMG]http://i145.photobucket.com/albums/r211/vicky_dear1/Gizmo/Clipboard02.jpg[/IMG]
[/LIST]
FYI, this is my original physical PC [Acer Aspire 5745G] configuration - 


[LIST]
[*]Intel core i5 2.27 GHz
[*]Windows 7 Ultimate 64bit
[*]4 GB RAM
[*]1 GB nVidia Graphics card
[*]500 GB Sata HDD
[/LIST]
Could anyone please let me know what the above error means and how to avoid it? How do I install Ubuntu 10.10 desktop 64bit on Windows Virtual PC?

Note: I'm trying to avoid VitualBox and other 3rd Party softwares here.

---

### Post by Mark Phelps on 2010-10-13
> **vicky_buddie said:**
> Note: I'm trying to avoid VitualBox and other 3rd Party softwares here.

We're NOT a Windows support forum; we're an Ubuntu support forum.

Those "3rd party softwares" that you're trying to avoid is what we DO here.

---

### Post by gkey on 2010-10-15
Virtual PC and the 64-bit edition of ubuntu don't go well together. 
Try the i386 version. It works for me. Make sure to press F6 at boottime and add the following to the string

> vga=791 noreplace-paravirt

I used the instructions from Scott with some imagination here and there:

[URL="http://www.hanselman.com/blog/InstallingUbuntu104LTSOnWindowsVirtualPCOnWindows7.aspx"]
http://www.hanselman.com/blog/InstallingUbuntu104LTSOnWindowsVirtualPCOnWindows7.aspx[/URL]

---

### Post by chrisgabriel on 2010-11-13
Windows Virtual PC emulates a 32bit environment. You'd need to use the i386. iso for it.

---

### Post by gkey on 2010-11-13
> You'd need to use the i386. iso for it

Exactly my point.... thats why I mentioned it first in my reply

> Try the i386 version. It works for me. 

---

### Post by Dr. C on 2010-11-13
Virtualbox supports a 64bit GNU / Linux guest on a 64bit Microsoft Windows host. The PUEL edition for Microsoft Windows is available from [here]("http://www.virtualbox.org/wiki/Downloads"). Or one can download Open Source Edition of Virtualbox and compile it on Microsoft Windows.

---

