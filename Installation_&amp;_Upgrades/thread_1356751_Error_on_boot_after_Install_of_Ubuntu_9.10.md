---
title: "Error on boot after Install of Ubuntu 9.10"
date: 2009-12-16
forum: Installation &amp; Upgrades
---

### Post by idle1986 on 2009-12-16
New to Unix.
I just downloaded and attempted to install ver 9.10.  The install appeared to go fine but when I tried to boot I get the following message:

Error:  no such device d128b391-4d8d-4938-9412-d925edd98f62
failed to boot default entries
Press any key to continue

I told it to use the entire hard drive.
What did I do wrong?   What is the proceedure to correct?

---

### Post by pi4r0n on 2009-12-16
I would say that you have incorrectly configured grep while installing Ubuntu.

You can do 2 thinkgs to fix it

[LIST=1]
[*]Install Ubuntu once again and ensure that its configured the right way
[*]Open Boot CD and configur grub manualy
[/LIST]

---

### Post by idle1986 on 2009-12-16
I can reinstall the OS but could you be more specific on the settings?  Thanks

---

### Post by phillw on 2009-12-16
Hi,

Re-installing an unhappy Grub2 is covered here [https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD](https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD)

You need your LiveCD to carry it out - I know it works - Coz I borked my Grub a while back ;-)

Regards,

Phill.

---

