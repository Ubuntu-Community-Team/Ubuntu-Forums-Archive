---
title: "How do I mount fileshares in Ubuntu"
date: 2005-07-28
forum: Installation &amp; Upgrades
---

### Post by bobbygr on 2005-07-28
Is there a way to mount fileshares under ubuntu (I need to copy data from another computer to Ubuntu)?

Could someone tell me where I need to go to to this?

Thanks!

Bob

---

### Post by supanova on 2005-07-28
Do you want to copy from ubuntu to say windows?

if so create a mount point

say under /mnt

i.e. 

cd /mnt
mkdir mymount

then

smbmount //yourhost/share /mnt/mymount -o username=user/DOMAIN (or workgroup)

it'll ask you for your password

Ciao

---

### Post by bobbygr on 2005-07-28
I have samba installed.

I get command not found when I type smbmount....


Thanks,

Bob

---

### Post by supanova on 2005-07-28
Hi Bob

You need to make sure that you have ***smbfs *** installed

Fire up synaptic and install

Good Luck

---

