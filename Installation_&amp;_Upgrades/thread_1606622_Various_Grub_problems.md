---
title: "Various Grub problems"
date: 2010-10-26
forum: Installation &amp; Upgrades
---

### Post by footclan on 2010-10-26
Hi, I'm using Ubuntu 10.10 64 bit (32bit i386 or alternate wouldn't work) and have been having dual boot issues.

I had Ubuntu installed first and I decided to install Xp. After installation it would boot straight into windows with no bootloader. I put in a livecd and followed a tutorial and grub came back, but there was no option for windows. 

As of now grub doesn't show at all and I'm put straight into Ubuntu. While I've been using Ubuntu for awhile I'm still a noob.

Any suggestions?

thanks

---

### Post by Seq on 2010-10-26
> **footclan said:**
> Hi, I'm using Ubuntu 10.10 64 bit (32bit i386 or alternate wouldn't work) and have been having dual boot issues.

I had Ubuntu installed first and I decided to install Xp. After installation it would boot straight into windows with no bootloader. I put in a livecd and followed a tutorial and grub came back, but there was no option for windows. 

As of now grub doesn't show at all and I'm put straight into Ubuntu. While I've been using Ubuntu for awhile I'm still a noob.

Any suggestions?

thanks

You can adjust the GRUB_TIMEOUT in the file /etc/default/grub. The value is in seconds.
```
gksu gedit /etc/default/grub
```

Afterwards, run `sudo update-grub`. It should enumerate all operating systems found on your system, including Windows. It updates grub with said OS list, as well as the updated timeout you changed above.

---

### Post by footclan on 2010-10-26
Awesome. It worked without any problems. 

Thanks a lot.

---

