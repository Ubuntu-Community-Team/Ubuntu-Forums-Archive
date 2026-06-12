---
title: "I was downgraded from 14.04 to 13.10"
date: 2014-05-21
forum: Installation &amp; Upgrades
---

### Post by tayx on 2014-05-21
Hello,

Recently I logged into my computer to find the Gnome theme instead of Unity. This was a bit strange, so I went to check the 'Details' page in my system settings, and I found that I was now using 13.10 instead of 14.04. I originally upgraded to 14.04 when it was released, but now it seems to be gone. Has anyone else run into this issue and if so, was there a way to return to 14.04 without re-upgrading??

Thanks!

---

### Post by LastDino on 2014-05-21
:-o

I don't know, but I think people would be more interested in knowing how you achieved this ''problem'' of downgrading.

---

### Post by tayx on 2014-05-21
Okay now I'm more confused. When I check 'Details' in Settings, it lists that I have ubuntu 13.10. HOWEVER, when I check in terminal through 'lsb_release -a', it shows that I have Ubuntu 14.04 LTS. Additionally, if I reload unity, it stays for the current session, however I am kicked back to Gnome upon restarting my machine.

Honestly though if I could go back to Unity permanently with my previous settings, I wouldn't mind the mismatch between 13.10 and 14.04 depending on how I check my current version. :)

---

### Post by grahammechanical on 2014-05-21
Are you using Ubuntu Gnome? If so then what you are seeing is a known bug. Look for the heading Known Issues. Perhaps you have installed Gnome 3 shell and may be that has the same bug.

[https://wiki.ubuntu.com/TrustyTahr/ReleaseNotes/UbuntuGNOME](https://wiki.ubuntu.com/TrustyTahr/ReleaseNotes/UbuntuGNOME)

[https://bugs.launchpad.net/ubuntu/+source/gnome-control-center/+bug/1299912](https://bugs.launchpad.net/ubuntu/+source/gnome-control-center/+bug/1299912)

You are on 14.04. The Details page is lying to you. As to why this is happening, it might be due to the fact that Ubuntu 14.04 does not use gnome-control-center any more but a Ubuntu fork of it called unity-control-center.

Regards.

---

### Post by kansasnoob on 2014-05-22
> if I reload unity, it stays for the current session, however I am kicked back to Gnome upon restarting my machine

What "gnome" packages have you added? It would be cool to see your /var/log/apt/history.log :)

---

