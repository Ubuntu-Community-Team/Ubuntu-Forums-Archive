---
title: "Software Index Broken"
date: 2012-02-06
forum: Installation &amp; Upgrades
---

### Post by rduffee on 2012-02-06
I find myself in somewhat of a bind after an interrupted update. The software index is broken, and numerous features (mousepad, wireless) are not functional. When I try to update, it advises me that the Software index is broken. When I try apt-get install -f I get this error:

E: dpkg was interrupted, you must manually run 'sudo dpkg--configure -a' to correct the problem.

So upon running dpkg configure, I get this output:

Setting up linux-image-3.0.0-15-pae (3.0.0-15.26) ...
Running depmod.
update-initramfs: deferring update (hook will be called later)
Examining /etc/kernel/postinst.d.
run-parts: executing /etc/kernel/postinst.d/dkms 3.0.0-15-generic-pae /boot/vmlinuz-3.0.0-15-generic-pae
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 3.0.0-15-generic-pae /boot/vmlinuz-3.0.0-15-generic pae
update-initramfs: Generating /boot/initrd.img-3.0.0-15-generic-pae
run-parts: executing /etc/kernel/postinst.d/pm-utils 3.0.0-15-generic-pae /boot/vmlinuz-3.0.0-15-generic-pae
run-parts: executing /etc/kernel/postinst.d/update-notifier 3.0.0-15-generic-pae /boot/vmlinuz-3.0.0-15-generic-pae
run-parts: executing /etc/kernel/postinst.d/zz-update-grub 3.0.0-15-generic-pae /boot/vmlinuz-3.0.0-15-generic-pae



At that point, there is no more output, and it never progresses past that point. Any ideas? I'd like to avoid a full reinstallation if possible. Thanks!

---

### Post by drs305 on 2012-02-06
Just confirm the command you ran was:
```
sudo dpkg --configure -a
```

Looking at the /etc/kernel folder, the zz-update-grub file is the last in the folder, so it is either completing this set of tasks or that particular script is failing. The former is more likely since you receive no error message from the zz-update-grub script. Why it then stops I don't know, but I thought I'd add this bit rather than just post the above command.

---

### Post by rduffee on 2012-02-06
Thanks for the reply. Yes, that was the exact command I used (I should have been clearer, sorry). I initially let the zz-update-grub run for over an hour, and it never returned any kind of error message.

---

### Post by rduffee on 2012-02-06
I found this on another site, but I'd like a second opinion before I try it out. Would this solve my problem?

sudo dpkg-reconfigure -phigh -a

---

### Post by rduffee on 2012-02-06
Alright, I solved it myself. I went in with a Live USB, changed the root directory to the hard disk (I don't know if that helped or not) and ran 'sudo dpkg --configure -a' from there. Although there were a bunch of errors (due to permissions), I restarted and everything was back to normal. :-)

---

