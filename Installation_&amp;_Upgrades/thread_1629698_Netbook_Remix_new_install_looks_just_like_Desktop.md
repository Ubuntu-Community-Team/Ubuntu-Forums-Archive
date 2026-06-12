---
title: "Netbook Remix new install looks just like Desktop"
date: 2010-11-24
forum: Installation &amp; Upgrades
---

### Post by weliwarmer on 2010-11-24
Hi Ubuntu Experts,

My first Netbook Remix installation (though not my first Ubuntu by far) and it seems to have installed the Desktop version.

I downloaded the Netbook Remix 10.10 iso and installed via usb onto an emachines atom netbook.

Did I miss a step?  Is there a hidden option to select UNE instead of Desktop?

Thanks for your help,
Tim

---

### Post by sikander3786 on 2010-11-24
Logout and from login screen, click your name. A sessions menu should appear near the bottom of screen. Does it contain Ubuntu Netbook session? If yes select and login.

If doesn't, I think you have not install Netbook Edition.

You can add ubuntu-netbook to a standard Ubuntu desktop by

```
sudo apt-get install ubuntu-netbook
```

And then switch between them at login screen.

Good Luck!

---

### Post by kerry_s on 2010-11-24
> **weliwarmer said:**
> Hi Ubuntu Experts,

My first Netbook Remix installation (though not my first Ubuntu by far) and it seems to have installed the Desktop version.

I downloaded the Netbook Remix 10.10 iso and installed via usb onto an emachines atom netbook.

Did I miss a step?  Is there a hidden option to select UNE instead of Desktop?

Thanks for your help,
Tim


unity is 3d accelerated, if your card does not support that out of the box, you get the normal desktop so you can install your vid drivers, then log out & select netbook in the session menu.

---

### Post by weliwarmer on 2010-11-24
Thanks for the quick replies.  I'll try the session switch this evening and post the result.  Thanks again.

---

### Post by weliwarmer on 2010-11-25
sikander3786: Your suggestion worked.  After installing ubuntu-netbook packages and a logout/login, it all works fine.

I'm surprised that the installation from the netbook remix iso did not install these packages by default.  I've treble checked that this is the iso used!

Thanks again to you both.

Tim

---

