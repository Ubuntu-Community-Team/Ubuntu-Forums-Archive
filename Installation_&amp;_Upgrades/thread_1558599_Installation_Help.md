---
title: "Installation Help"
date: 2010-08-22
forum: Installation &amp; Upgrades
---

### Post by Tarmon.Gaidon on 2010-08-22
Hey Everyone,

I am trying to install the latest Ubuntu on a IBM Thinkpad lenovvo T60. Right after the installation starts I am given this message:

Edit: This is given under a Busybox header. 

"(intitramfs) mount: mounting /dev/loop0 on //filesystem.squashfs failed: Input/output error

Can not mount /dev/loop0 (/cdrom/casper/filesysytem.squashfs) on //filesystem.squashfs"

Any help you would be appreciated! 

Thanks,
Rob

---

### Post by Rubi1200 on 2010-08-22
Hi,
did you check the MD5SUM?
[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

what graphics card do you have installed and how much RAM do you have?

Thanks.

---

### Post by EckyThunp on 2010-08-25
I'm getting the same error trying to install off a burned CD. I ran the MD5 check as instructed (the Windows version) and it matches.

If it provides any clues, I tried "mount /dev/loop0" after getting the error, and got the message "cannot read /etc/fstab - no such file"

Thanks for any help.

---

