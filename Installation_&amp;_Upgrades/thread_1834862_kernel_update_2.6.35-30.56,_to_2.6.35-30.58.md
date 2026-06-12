---
title: "kernel update: 2.6.35-30.56, to 2.6.35-30.58"
date: 2011-08-28
forum: Installation &amp; Upgrades
---

### Post by egrpioneer on 2011-08-28
Maverick 10.10 kernel update from 2.6.35-30.56, to 2.6.35-30.58 created the following output after every subsequent non-kernel update: 

<Failed to process /etc/kernel/postinst.d at /var/lib/dpkg/info/linux-image-2.6.35-30-generic.postinst line 1010.
dpkg: error processing linux-image-2.6.35-30-generic (--configure):
 subprocess installed post-installation script returned error exit status 2>  

Research led me to a solution posted on this forum by dino99. But, before I remove & reinstall grub-pc, as was suggested, please answer the following question: I have 2, hdds running Windows 7 Pro., and 10.10. Grub still works great and allows flawless dual boot! Will the "solution" create issues?

---

### Post by dino99 on 2011-08-28
is it a real installation ? or is Maverick installed inside virtualbox as a guest ? or is it installed via wubi ?

if grub works well, no need to reinstall it. Check that dkms is installed (synaptic)

---

### Post by egrpioneer on 2011-08-28
> **dino99 said:**
> is it a real installation ? or is Maverick installed inside virtualbox as a guest ? or is it installed via wubi ?

if grub works well, no need to reinstall it. Check that dkms is installed (synaptic)

Thanks for responding!! 2,hhds installed. Maverick 10.10 running ext4 sdb1. Windows 7, sda1. DKMS is installed!

---

