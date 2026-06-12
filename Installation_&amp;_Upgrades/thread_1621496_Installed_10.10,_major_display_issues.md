---
title: "Installed 10.10, major display issues?"
date: 2010-11-14
forum: Installation &amp; Upgrades
---

### Post by andrewarthurwilson on 2010-11-14
I am new to ubuntu and windows. 
 
I installed ubuntu 10.10 using wubi on an HP Pavilion dv6605us notebook (1.8 GHz AMD Athlon 64 X2 TK-55; 1 Gb RAM, NVIDIA GeForce Go 7150M graphics card) running Vista Home Premium, and while I can get it to start up in ubuntu, the screen display is bizarre-it's three vertical "partitions" showing the same thing, giant magnified windows and no menu bars. I can move the cursor and drag windows around but they disappear when moved to the edge of the "partition," and it's basically impossible to do anything like change display options since there's no menu bar. 
 
I had started ubuntu from a cd prior to installing with wubi, and somehow figured out that setting the "nomodeset" option on the startup menu resulted in a normal usable appearance. Now I don't even know how to get that startup menu to appear. 
 
Also, to tack one more question on, when I tried to log on to a wireless network I got the message "lacks firmware" or something like that-how can I go about getting the necessary firmware update when I can't get online on this machine? I assume burning a cd from another computer, but I don't know where to go to get the firmware. 
 
Thanks so much in advance, 
 
Andrew

---

### Post by bradbury on 2010-11-14
Try using Ctrl-Alt-F1 thru F4 (VT1-VT4) to get a basic login prompt.  Then login as a normal user.  "sudo bash" with the "primary" user's password will get you a "root" shell.  From they one can do "apt-get install -package-" or "apt-cache search string" to install packages or search for packages respectively (do web searches from Windows or "man apt-get" or "man apt-cache" from linux if unfamiliar).  Note -- this is NOT a graphical (Gnome) user interface -- its the basic old-fashioned UNIX/Linux "shell" interface (which fortunately should not require fancy graphics).  However I've seen cases where 10.10 "loses" the ability to shift to these alternate/simpler interfaces (if so back off to an older Ubuntu version -- 10.10 is problematic to to buggy versions of the X program and several gnome utilities).  Normal graphical interfaces are found on VT7 and up (ctrl-alt-F7).

As far as the firmware goes there may be a separate directory (/lib/firmware???) which may be required.  I don't know if it is required on your root partition or the temporary root (initrd) which is loaded at boot time however.  Firmware for a variety of cards is typically found in this directory.

---

