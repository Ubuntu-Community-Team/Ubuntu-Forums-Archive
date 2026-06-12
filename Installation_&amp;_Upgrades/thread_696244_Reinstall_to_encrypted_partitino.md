---
title: "Reinstall to encrypted partitino"
date: 2008-02-13
forum: Installation &amp; Upgrades
---

### Post by ostehamster on 2008-02-13
Hi

When I installed Gutsy on my laptop, I choose to encrypt the hard drive.

For different reason the installation is messed up, and I want to make a clean installation. I would though really like to "reuse" the encrypted LVM partition, to keep my /home, is it possible?

I guess I should mount the LUKS partition somehow when the installation system boots up, but how?

Best regards
Christoffer Kjølbæk, DK

---

### Post by mrsteveman1 on 2008-02-13
Are you saying you have a separate encrypted luks partition that contains your home files?

Your best bet is to simply install ubuntu again in the free space and then setup the system to mount your luks partition on /home after you get it up and running. It's not terribly difficult to do, simple file editing etc.

Is that what you want to do?

---

### Post by ostehamster on 2008-02-15
No, I used the encrypted setup in the installation wizard. So I have one big encrypted partition with LVM, and of course a /boot.

---

### Post by mrsteveman1 on 2008-03-09
Found this page about recovering an encrypted system, you can probably tweak this a bit to reinstall onto the same system:
[URL="http://www.ubuntugeek.com/rescue-an-encrypted-luks-lvm-volume.html"]
http://www.ubuntugeek.com/rescue-an-encrypted-luks-lvm-volume.html[/URL]

---

