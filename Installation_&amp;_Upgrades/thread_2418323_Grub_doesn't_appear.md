---
title: "Grub doesn't appear"
date: 2019-05-05
forum: Installation &amp; Upgrades
---

### Post by mati220 on 2019-05-05
Hi. I have a problem with grub. Today, when I upgrade ubuntu to version 19.04 I lost the list of systems in grub. Ubuntu was automatically loaded without any choice. I use boot-repair and I get error message. I fixed this error. Actually I have a black screen but I can choose Ubuntu or Windows (I remember what I must clicked and in what order to turn on the system). I think the grub works but it doesn't appear. What's the problem? 

After the latest repairing boot-repair app I get this logs:
[http://paste.ubuntu.com/p/5ZTCG74H3g/](http://paste.ubuntu.com/p/5ZTCG74H3g/)

---

### Post by oldfred on 2019-05-05
Remove boot flag from sda2. That looks like it should be the Windows System Reserved which must be unformatted. Parted tools may show as an error as unformatted, but it should have the GUID for Microsoft's System reserved.

Your /etc/default/grub looks normal for 19.04.

Boot-Repair does add extra grub boot entries into 25_custom. Most are not required. You can edit out ones you do not want or turn off execute bit on 25_custom so grub does not run it on grub-update.
You also should houseclean out the old Boot-Repair logs in your ESP, sda1.

---

