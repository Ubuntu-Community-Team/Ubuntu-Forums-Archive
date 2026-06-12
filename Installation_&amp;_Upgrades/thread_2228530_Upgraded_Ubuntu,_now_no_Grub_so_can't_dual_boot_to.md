---
title: "Upgraded Ubuntu, now no Grub so can't dual boot to Kali (LVM)"
date: 2014-06-08
forum: Installation &amp; Upgrades
---

### Post by clay7 on 2014-06-08
Hello - I ugraded Ubuntu today and when I rebooted, I didn't get the usual GRUB menu to choose between Ubuntu and Kali. The computer boots straight to Ubuntu. Kali was an encrypted install LVM. How do I get GRUB to show again so I can choose which OS?

---

### Post by oldfred on 2014-06-08
The upgrade may not have reinstalled the LVM drivers.
check that you have lvm2.
sudo apt-get install lvm2

Then mount your LVM and run os-prober with this:
       sudo update-grub

---

### Post by clay7 on 2014-06-08
oldfred, you're awesome! Thank you very much...worked like a charm :)

---

