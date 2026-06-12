---
title: "Another 12.04 to 14.04 problem"
date: 2014-08-23
forum: Installation &amp; Upgrades
---

### Post by burro on 2014-08-23
Hello,

My Ubuntu installation is broken after attempting to upgrade from 12.04 to 14.04. At one stage I managed to boot the system after switching from lightdm to gdm (lightdm wouldn`t start the x server), however, when the system advised me that my system wasn`t upgraded correctly and suggested I follow the following steps (another partial upgrade, I think) the system no longer works. Presently the following happens when I attempt to boot - 

Grub loads ok - i choose the latest entry
Purple screen with ubuntu logo says that it is 'waiting for network configuration...`
It stalls here for a while and then
'waiting for up to 60 more seconds for network configuration...'
after this the gvd screen finally loads however the mouse and keyboard are frozen and I can`t preceed.

Another thing I tried was ubuntu's Boot-Repair. This reported no errors and didn`t help - however the printout from the process is available here

paste.ubuntu.com/8121112

My guess is that I should attempt to reinstate lightdm. However as nothing has worked too well so far, I`m writing to this forum (via a Live USB) for advice on the safest way forward.

Hope someone can help

thanks

---

### Post by grahammechanical on 2014-08-23
> [COLOR=#000000]Grub loads ok - i choose the latest entry[/COLOR]

So, you do not have a boot problem that Boot Repair can fix. Here is what you can try

1) at the Grub boot menu select Advanced Options for Ubuntu and in the sub-menu select Recovery Mode.
2) at the recovery menu select Network. That will set up a network (internet) connection.
3) when back at the recovery menu select Root. That will put you at a root shell prompt.
4) run

```
apt-get update
apt-get upgrade
apt-get dist-upgrade
```

See what happens and post and error messages. Just the error messages.

5) to get back to the recovery menu type exit
6) at the recovery menu select Resume. That will attempt to load to a desktop using a fall back open source video driver.

See how that goes. If you get to a working desktop think about changing the video driver.

Regards.

---

### Post by burro on 2014-08-23
Thanks very much for the reply. In the grub menu I don`t see any advanced options, however there is the recovery mode of the latest installed kernel and this leads to a list of options, one of which is 'network'. Unfortunately, and I forgot to mention this, the keyboard freezes at this step and nothing can be selected. Back at the grub menu, the keyboard works and I can enter the command line via 'c' and edit boot commands with 'e'. From memory I think I can mount and boot my HD partition from the live USB (with chroot?). Should I try something like this to run the update/upgrade commands you suggested?

---

### Post by kansasnoob on 2014-08-23
> **burro said:**
> Thanks very much for the reply. In the grub menu I don`t see any advanced options, however there is the recovery mode of the latest installed kernel and this leads to a list of options, one of which is 'network'. Unfortunately, and I forgot to mention this, the keyboard freezes at this step and nothing can be selected. Back at the grub menu, the keyboard works and I can enter the command line via 'c' and edit boot commands with 'e'. From memory I think I can mount and boot my HD partition from the live USB (with chroot?). Should I try something like this to run the update/upgrade commands you suggested?

It's possible. Here's a chroot procedure that assumes you have no separate /boot:

[http://www.webupd8.org/2014/01/how-to-fix-non-bootable-ubuntu-system.html](http://www.webupd8.org/2014/01/how-to-fix-non-bootable-ubuntu-system.html)

And here are some common commands to help recover from a borked release upgrade:

[http://ubuntuforums.org/showthread.php?t=2240033&page=2&p=13103395#post13103395](http://ubuntuforums.org/showthread.php?t=2240033&page=2&p=13103395#post13103395)

The order in which to run commands varies from borkage to borkage and the actual output of the commands quite often provides info that tells you what to try next.

---

### Post by burro on 2014-08-23
Thanks for your help grahammechanical and kansasnoob. Did the chroot then apt-get update, apt-get upgrade and  apt-get dist-upgrade. Also purged and reinstalled/reinstated lightdm. Booted fine - probably some things to fix yet, but looking good.

---

