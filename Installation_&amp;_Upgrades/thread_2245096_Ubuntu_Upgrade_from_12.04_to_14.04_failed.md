---
title: "Ubuntu Upgrade from 12.04 to 14.04 failed"
date: 2014-09-21
forum: Installation &amp; Upgrades
---

### Post by alex262 on 2014-09-21
Hey,
so when I was updating my Ubuntu system from 12.04 LTS to 14.04 LTS it gave me an error and then a message saying "The system is now in an usable state" or something like that... I couldn't even shut down the system so I had to do it the "manual" way. After that I when I choose ubuntu (I have dual-boot system with ubuntu and windows 7) it gives me a black page like if it was the terminal but sometimes just a black page. What should I do?

Regards,
Alex

---

### Post by grahammechanical on 2014-09-21
You can try this.

At the Grub menu open the Advanced Options for Ubuntu sub-menu and select Recovery Mode. At the Recovery menu select Network. When that has finished getting an Internet connection select Root and type this

```
apt-get update
apt-get upgrade
```

and note down any error messages for us. You can also then run

```
apt-get dist-upgrade
```

to make sure that the OS upgrade is complete. To get back to the Recovery menu type

```
exit
```

Then select Resume. If gets to a working desktop Ubuntu will be using a fall back open source video driver. So, log out and in or reboot.

Regards.

---

### Post by alex262 on 2014-09-21
> **grahammechanical said:**
> You can try this.

At the Grub menu open the Advanced Options for Ubuntu sub-menu and select Recovery Mode. At the Recovery menu select Network. When that has finished getting an Internet connection select Root and type this

```
apt-get update
apt-get upgrade
```

and note down any error messages for us. You can also then run

```
apt-get dist-upgrade
```

to make sure that the OS upgrade is complete. To get back to the Recovery menu type

```
exit
```

Then select Resume. If gets to a working desktop Ubuntu will be using a fall back open source video driver. So, log out and in or reboot.

Regards.

Thanks for the fast answer :) When I went to network it did all that and then it stoped at loaded pluging linktop so I tought it would be over but it just stayed there so I did exit and it went back to recovery menu. When I went to root and typed "apt-get update" it gave the following errors:

W: Failed to fetch "Some website from ubuntu.com or something" (this error was repetead several times)
W: Some indez files failed to download. They have been ignored, or old ones used instead.
W: Not using locking for read only lock file /var/lib/dpkg/lock
E: dpkg was interrupted, you must manually run dpkg --configure -a to correct the problem. (i did that command and it gave me an erro saying that it wasn't a valid command :? )

Regards,
Alex

---

