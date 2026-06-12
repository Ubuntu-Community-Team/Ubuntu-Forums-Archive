---
title: "ubuntu will not start after install"
date: 2007-05-01
forum: Installation &amp; Upgrades
---

### Post by elendur45 on 2007-05-01
I have a compaq presasio 6370 which has been upgraded with a  wd 160 g hard drive running windows XP pro and an ATI radeon 9250 256 mb Video card.  I also have upgraded with a microsoft wireless mouse and keyboard. I partioned my hard drive using partion magic 8.0 leaving 30 g of free space then using the ubuntu alt cd i partioned the free space into 29 g of primary and 1 g of logical for my swap file. Everything installed ok, but when I rebooted the unbuntu screen comes up and the first three spaces in the logon change to orange and then the computer just stops. I have to power down to reboot. I can log into windows ok.  Am new to Linux and Ubuntu. Any help is appreciated. Thanks

---

### Post by rsambuca on 2007-05-01
At the grub screen where you select your OS, there is a key to press to edit the boot options (e - I think).  Move the selection to ubuntu, then press the key to enter the edit sequence.  Go to the line that starts root=... , and remove the "quiet splash" words at the end of the line.  Then boot from there.  You should see a list of commands running as it boots up.  When it hangs, write down what it says and post back here.  Either I or someone else will be able to help you out.

---

### Post by elendur45 on 2007-05-01
When it starts, gets to "Loading Hardware Drivers" I don't get the OK and then it starts scrolling so you can't read. After rebooting several times it finally stopped and the messages were error_code +0x7c/0x90, also page faults and apic faults among others repeating continuously

---

### Post by dlikhten on 2007-05-05
Interestingly enough... I had a similar issue. When booting my screen goes blank and caps and scroll lock lights flash. Strange I thought, so I thought of doing what you sugested and guess what... its the SPLASH option that was crashing my comp... HMMMM!!! Ive had some of this problem with the live cd (BTW ubuntu live-cd-installation is the best idea ever made!)

I want to thank you for the help. Maybe you can help me discover what is wrong so I can report it to development (sorry i cant even get the text caz my screen goes blank if i remove "quiet" after a few seconds of booting)

Where can I get the boot log dump?

--Dmitriy

---

