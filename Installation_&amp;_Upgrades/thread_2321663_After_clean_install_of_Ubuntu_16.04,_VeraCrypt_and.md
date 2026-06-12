---
title: "After clean install of Ubuntu 16.04, VeraCrypt and TrueCrypt are acting weird"
date: 2016-04-23
forum: Installation &amp; Upgrades
---

### Post by Gottier on 2016-04-23
I've been a long time TrueCrypt user, and I understand that VeraCrypt is the updated version. I clean installed Ubuntu 16.04 this morning, and both of these programs now require that I disable the kernel cryptographic services in order to open my containers. Should I be worried? Do I need to install something else too?

If I don't disable the kernel cryptographic services, it gives me an error when I try to open the container. Says:

> No such file or directory:
dmsetup

VeraCrypt::Process::Execute:88

---

### Post by BeMueller on 2016-04-23
sudo apt-get install dmsetup

will do it. dmsetup is now no standard application, so you must install it.

---

### Post by entropy1 on 2016-04-26
Thanks for the tip, BeMueller. Once I installed dmsetup, truecrypt started working again just like it used to.

---

### Post by entropy1 on 2016-04-26
Thank you, BeMueller. After installing dmsetup, truecrypt works like before.

Edit: Duplicate post when I didn't see my original one. I'd be happy to have it deleted.

---

### Post by fdmille on 2016-05-28
Thank you.  This got my Truecrypt working again.  It would not open a valid encrypted partition but now it does.

---

### Post by joberholzer on 2016-08-09
Hi guys, I'm really sorry to bump this old thread but I'm still having an issue with VeraCrypt and Ubuntu-Gnome 16.04.1. I did a fresh install on a Surface Pro 3, ran apt-get install dmsetup and installed veracrypt. When I try to mount an encrypted container in VeraCrypt, it just gets stuck on the "Please wait" screen. I can't seem to find any logs or information to tell me where it's stuck so I can start troubleshooting. Were there any other steps required to get VeraCrypt working or was it simply just "install dmsetup". Any help would be greatly appreciated :)

---

### Post by coolweather on 2016-11-20
Hey Thanks BeMueller. That worked. Thanks to other users here too who commented. Ubuntu community seems awesome. @BeMueller @entropy1

---

### Post by coolweather on 2017-04-22
> **BeMueller said:**
> sudo apt-get install dmsetup

will do it. dmsetup is now no standard application, so you must install it.

Wow! This is great. Thanks for the help. Ubuntu needs to a loooooooooooooot in intracting with user. VeraCrypt provided not clear help about if I needed this "dmsetup".

---

### Post by nastasja on 2017-12-31
Hi,
still in 2018 an useful hint to install this mysterious missing "dmsetup"!
Thanks.

---

