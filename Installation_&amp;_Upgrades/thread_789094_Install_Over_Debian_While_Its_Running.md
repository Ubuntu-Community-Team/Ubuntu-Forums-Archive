---
title: "Install Over Debian While Its Running"
date: 2008-05-10
forum: Installation &amp; Upgrades
---

### Post by Littlehawk on 2008-05-10
I am having a problem with installing. For some reason, I can't boot from a USB, even though the stick will boot on another machine. I can't install Ubuntu using PXE, because it hangs up due to a hardware error message. I have one hard drive and no other means to install.

However, I was able to install Debian using PXE. Now I want to replace it with Ubuntu. I can now read the USB, which has the Ubuntu LiveCD copied onto it. 

Is there a way to start the installation now from the USB once I have booted into Debian? I would prefer to either completely replace Debian or repartition without losing Debian (it uses the entire hard drive, after using the guided install). 

I have grub installed.

Thanks,
Jim

---

### Post by Pumalite on 2008-05-10
Have you consider:
[http://lubi.sourceforge.net/unetbootin.html](http://lubi.sourceforge.net/unetbootin.html)

---

### Post by Littlehawk on 2008-05-10
Unetbootin looks like just what I need, but it's not working. I'll continue give it, but any suggestions are appreciated. Here is the terminal output when I try to run it:

[B]me@debian:~/UnetBootin$ su -c ./unetbootin-linux-191
Password:
Qt: Session management error: Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed
./unetbootin-linux-191: symbol lookup error: ./unetbootin-linux-191: undefined symbol: _ZN9QListData7detach2Ev
[/B]
I installed all the packages beginning with libqt4... It's not clear what the dependencies are and which is on top.

---

### Post by Pumalite on 2008-05-10
Try this:
[https://help.ubuntu.com/community/Installation/Netboot](https://help.ubuntu.com/community/Installation/Netboot)
[https://help.ubuntu.com/community/Installation#head-ca8e337bdfab6bfa1d064371898775fe1e9e22fd](https://help.ubuntu.com/community/Installation#head-ca8e337bdfab6bfa1d064371898775fe1e9e22fd)

---

### Post by Littlehawk on 2008-05-10
Thanks, I'll try those.  In the mean time, I decoded what I needed to do for booting from USB and successfully installed from LiveCD running from the USB. 

I'm in business!!	\\:D/

---

### Post by Pumalite on 2008-05-10
Congrats!

---

