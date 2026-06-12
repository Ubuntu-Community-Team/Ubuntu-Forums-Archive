---
title: "Problems installing Ubunut 12.04 and 14.04"
date: 2014-06-13
forum: Installation &amp; Upgrades
---

### Post by Tony_Brooks on 2014-06-13
I have Ubuntu 9.10 which was supplied with a "Introduction to Linux" magazine. I am using a Fujitsu laptop (Celeron 900 @2.2GHz)  and my access to www is via my Samsung (Galaxy Fame). I know that 9.10 is unsupported and so have been trying to download 14.04 to allow me to start from scratch. I am having problems. I consider myself reasonably cognisant with computers but am stymied at the mo. Don't know if the hardware is too old (it was cheap!) or whether there were problems with Karmic Koala. Can anybody help ? Possibly useful info : Kernel Linux 2.6.31-14-generic  GNOME 2.28.1

---

### Post by QIII on 2014-06-13
Hello!

What problems are you having, exactly?

---

### Post by Tony_Brooks on 2014-06-13
I have downloaded both 64 & 32 bit versions of 14.04 and then burnt them to DVD and then tried to RESTART with booting from the CD drive. The last trial was the 32 bit version and it looks at the CD then goes to the hard disk and loads 9.10 . Have tried 12.?? and 14.04 (64 bit) and my computer just hangs. I intend to try the latter again and then take more notice of messages. I do get (using Karmic Koala) "One or more of the mounts listed in /etc/fstab cannot yet be mounted"

---

### Post by Bashing-om on 2014-06-13
Tony_Brooks; Hello,

Sounds like the DVD ( must be burned to a DVD/USB as the image will not fit on a CD)is not "bootable".
Dot your i's and cross your t's:
verify the .iso file:
[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)
Burn as an image (not data !) S L O W L Y
[https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)
Check the disk integrity:
[https://help.ubuntu.com/community/Installation/CDIntegrityCheck](https://help.ubuntu.com/community/Installation/CDIntegrityCheck)

When all the above is done, and bios is set to boot from the CD drive -> should boot !

[INDENT][INDENT]my little bit to help
[/INDENT][/INDENT]

---

### Post by yancek on 2014-06-13
Compare your hardware to the minimum requirements at the Ubuntu site below:

[https://help.ubuntu.com/community/Installation/SystemRequirements](https://help.ubuntu.com/community/Installation/SystemRequirements)

Did you do an md5checksum on the downloaded iso file to verify it?
Did you burn it as an image?
The Ubuntu download is too large for a CD, you are using a DVD and have a DVD player, correct?

---

### Post by mörgæs on 2014-06-14
A Celeron 900 is not that old. You should get a decent performance out of it. X/Lubuntu are faster than Ubuntu but all three should work.

Only important step is to have wired internet access while installing because there will be hundreds of MB's to download. If you don't have at home it's worthwhile to bring the computer to a place where you get access.

Installing from USB is safer than from CD / DVD.

---

### Post by Bucky Ball on 2014-06-14
*Thread moved to **Installation & Upgrades**.*

To improve your chances of support I have moved your post and have changed the title of your thread. Please use descriptive thread titles rather than generic or ambiguous ones.

Welcome to the forums and good luck. ;)

---

