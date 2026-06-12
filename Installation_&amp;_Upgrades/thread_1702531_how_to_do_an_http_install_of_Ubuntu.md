---
title: "how to do an http install of Ubuntu"
date: 2011-03-07
forum: Installation &amp; Upgrades
---

### Post by tapas_mishra on 2011-03-07
Hi,
I am having a situation where I can not use a CD or PxE boot or wubi to install.I need to necessarily do an http install of Ubuntu.I am basically trying to create a guest OS in
a virtualization setup on Xen on a non VT hardware.In such a hardware  virt-manager(GUI to install guest) does not allow me to install the guest other than http install.

Here is what I did 
1) Download ubuntu 10.04 32 bit ISO
2) Kept it in /var/www (apache2 is running) 
3) renamed it to ubuntu.iso

and when I reached a stage where installation begins I gave path [http://localhost/ubuntu.iso](http://localhost/ubuntu.iso) 
but I got an error saying any installable distribution not found.

4) After this I did
```
mkdir /var/www/sk

mount -t iso9660 /var/www/ubuntu.iso /var/www/sk -o loop

```
and this time during the installation I gave path [http://localhost/sk](http://localhost/sk)
I was able to see the contents in browser [http://localhost/sk](http://localhost/sk) which you will see in a normal CD.
But beginning installation I got same error 
```
ValueError: Could not find an installable distribution at 'http://localhost/sk

```
So I want to just confirm if http install is done only this way or some other way.

---

