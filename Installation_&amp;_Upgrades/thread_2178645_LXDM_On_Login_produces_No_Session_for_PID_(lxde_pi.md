---
title: "LXDM: On Login produces No Session for PID (lxde pid) error"
date: 2013-10-04
forum: Installation &amp; Upgrades
---

### Post by Anaximander Thales on 2013-10-04
I have a fresh install of Lubuntu 13.10 Beta 2.

Leaving LightDM in place after the fresh installation, I installed LXDM.  This works fine except that when I login in, I am immediately presented with an Error -- No Session for PID (/usr/bin/lxsession -s Lubuntu -e LXDE).  If I logout, run dpkg-reconfigure lxdm, choose lightdm, service lxdm stop, service lightdm start and login, I do not receive this error.  If I enable lxdm and reboot, I receive the no session for pid error.  If I reconfigre lxdm and choose lxdm, I get the error.  Every iteration I have tried with lxdm, I receive this error.

I am not sure what I need to add or edit to make this work.  

I can go back to LightDM, but I would prefer to have things work the way I want them.  That's the beauty of linux, it's also the PITA of linux.

Thanks,
AT

---

### Post by Anaximander Thales on 2013-10-05
Just a bump ... hoping someone can clue me in.  

Not much shown in the dmesg or syslog -- I've tried grepping for the pid itself, dbus (found an item on it -- but, it is started), and just scanned for errors.  I don't see any messages in lxdm logs, syslog or dmesg.

Anyone?

---

### Post by Anaximander Thales on 2013-10-17
Solving this by going to mini-ubuntu

---

### Post by Interruptor on 2013-11-11
[https://bugs.launchpad.net/ubuntu/+source/lxsession/+bug/1249844](https://bugs.launchpad.net/ubuntu/+source/lxsession/+bug/1249844)

---

### Post by artsuaga on 2014-06-09
It worked for me editing file /etc/pam.d/lxdm.

After:

```
#%PAM-1.0
```

Insert:

```
session required pam_loginuid.so
session required pam_systemd.so
```

---

### Post by Juan_ngel_RG on 2014-06-30
Does not work with Lubuntu 14.04. How can you solve in Lubuntu 14.04?

Regards 
Thank you.

---

### Post by carlos102 on 2015-05-19
Hi,

i had the same error message with Lubuntu 14.04 x86 login in the Guest session.
The pam thing didnt work for me.

I found this solution : removing package apparmor and rebooting, because i saw somewhere some error log about apparmor.
```
apt-get remove apparmor -y
```

I know this solution might be very dirty because apparmor is about security but i dont care in my case.
I tested this solution on several Lubuntu 14.04  x86 fresh installations on several computers.

---

### Post by superseismic on 2015-09-05
[COLOR=#000000]This solution to edit /etc/pam.d/lxdm worked for me on Lubuntu / LXDM 14.04.3[/COLOR]

---

