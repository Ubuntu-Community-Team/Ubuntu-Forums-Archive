---
title: "Ubuntu 18.04 LTS stuck on tty1 after upgrade from 17.10"
date: 2018-04-27
forum: Installation &amp; Upgrades
---

### Post by Rvdpeet on 2018-04-27
Hi everyone,

Today, I decided to install the long-expected Ubuntu 18.04.
First, I installed it on my old PC, which worked fine.

Later, I installed it on my (relatively) new laptop, and the installation process went well.
However, when rebooting, it hangs on

"Ubuntu 18.04 LTS [computer name] tty1
[computer name] login:"

Does anyone know how to fix this?

Thanks in advance!

Regards,
Rutger

---

### Post by memberstorm on 2018-04-27
Hi Rvdpeet,

Log in on the tty1 shell with your account username and password. Once there run this to revive gnome desktop:

sudo systemctl restart gdm3

Once performed, the error didn't happen to me again (so far)

---

### Post by Rvdpeet on 2018-04-28
Hi memberstorm,

Thanks for your quick response!

I tried your solution and it does start the gnome desktop. However, the next time I start my laptop, I have to do it again. I already tried turning on automatic login upon startup, but that didn't fix the problem.

Do you, or anyone else, know someting else I can try?

Regards,
Rutger

---

### Post by rollermy on 2018-04-28
Hey, I had the same problem. I followed advice on this page and it worked: [https://bbs.archlinux.org/viewtopic.php?id=165941](https://bbs.archlinux.org/viewtopic.php?id=165941)
In /etc/systemd/system display-manager.service was symlinked to lightdm
I removed that symlink and created a new one pointing to gdm instead
ln -sf /lib/systemd/system/gdm.service  display-manager.service
Rebooted and no problems.

you can run systemctl status gdm.service to get the location of the gdm service

---

### Post by Rvdpeet on 2018-04-28
> **rollermy said:**
> Hey, I had the same problem. I followed advice on this page and it worked: [https://bbs.archlinux.org/viewtopic.php?id=165941](https://bbs.archlinux.org/viewtopic.php?id=165941)
In /etc/systemd/system display-manager.service was symlinked to lightdm
I removed that symlink and created a new one pointing to gdm instead
ln -sf /lib/systemd/system/gdm.service  display-manager.service
Rebooted and no problems.

you can run systemctl status gdm.service to get the location of the gdm service


First of all, thanks for your quick response!


Since I'm not really familiar with these system links and I've had some bad experiences with computers with faulty boot systems (that I don't want to experience again :P), I'd like to verify a few things.

First: when I try to open the display-manager.service file, it says it's broken, and the link cannot be used because its target "lib/systemd/system/lightdm.service" doesn't exist. Is this normal? 

Furthermore, how do I remove this symlink? Do I delete the file in the folder in nautilus? Or can I do it with some command in the terminal? (again, I'm quite a noob with system links :P)

And after removing it, I should just run the "ln -sf /lib/systemd/system/gdm.service display-manager.service" command to fix it right?

Thanks a bunch!

*edit: I tried running the ln-line without actively removing the first link. Can anyone tell me how to delete the old symlink?

---

### Post by rollermy on 2018-04-28
Hey,

I know that lightdm user to be used, but that 18.04 now uses gdm. Lightdm was uninstalled during the upgrade but the display manager service still points to it. So the file "lib/systemd/system/lightdm.service" does not exist because it has been removed.
Open up a terminal and run "ls -la /etc/systemd/system". This will give more information about the files in the folder.  Check where display-manager.service is pointing to. ex "display-manager.service -> lib/systemd/system/lightdm.service"
If it still is pointing to lightdm: Remove the bad link with "sudo rm /etc/systemd/system/display-manager.service"
And then create the right one with "sudo ln -sf /lib/systemd/system/gdm.service /etc/systemd/system/display-manager.service"

---

### Post by Rvdpeet on 2018-04-28
Hey, this solved my problem!

Thanks for replying so quickly and helping me by explaining the steps i needed to take!

---

### Post by 2dmartin on 2018-05-22
And thank you also, it solved my 18.04 problem too !!

---

### Post by marc47474 on 2018-09-03
I had a similar issue, not even the console login would show up. After wasting quite some time it was again an old issue where graphical consoles prevent startup of Xorg.

A detailed solution can be found over here: [https://faqs.leponceau.org/2018/09/after-ubuntu-upgrade-to-1804-lts-xorg.html](https://faqs.leponceau.org/2018/09/after-ubuntu-upgrade-to-1804-lts-xorg.html)

---

### Post by lombardoalex on 2018-10-05
Hi,
I have tried this but I'm still having the same issue. if I type startx it will get to the GUI but it won't do it automatically. Thanks

---

