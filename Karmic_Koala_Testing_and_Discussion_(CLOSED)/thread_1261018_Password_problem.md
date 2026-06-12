---
title: "Password problem"
date: 2009-09-08
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by henwyn on 2009-09-08
I have been having problems getting Karmic installed and running. Alpha 5 seems to have installed okay but my password did not get recorded correctly somehow. I tried re-installing and same problem. Since grub 2 did not install links to the other os's on this computer, I'm stuck booting off of the cd. If anyone else has had this password problem, I'd like to know what route works best to fix it. Barring that, is it possible to edit the grub 2 files on this installation from the installation disk so that I can boot into another os?

Thanks in advance for any pointers.

---

### Post by sisco311 on 2009-09-08
Try to boot in recovery mode and reset your password.
[http://psychocats.net/ubuntu/resetpassword]("http://psychocats.net/ubuntu/resetpassword")

or try to boot your main os. when the grub menu shows up press c and type:
```
set root=(hd0,1)
linux /boot/vmlinuz<hit tab for auto-complete> root=/dev/sda1
initrd /boot/initrd<hit tab>
boot
```

replace (hd0,1) and /dev/sda1 with the actual partition.

---

### Post by henwyn on 2009-09-08
Thanks for the reply. Looking into this further, it looks like my installation is borked. Specifically, there is no /boot/grub/grub.cfg file and it looks like the script that probes for other os's on the computer is incomplete. This makes me distrust the whole installation. I'll have to try to get back into jaunty and then try this again from scratch.

Thanks again.

---

