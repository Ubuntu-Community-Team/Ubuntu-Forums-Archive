---
title: "Upgrade, Encryption, Backup Data"
date: 2007-10-11
forum: Installation &amp; Upgrades
---

### Post by weller on 2007-10-11
Hi
I'm currently using Feisty on my Notebook. Now Gutsy offers HD encryption on installation. This is a nice feature for the "stolen laptop case" :-)

Now I would like to change from Feisty to Gutsy but there are several question:
As the encryption is only possible on installation I can't run an online update.

1.) is it sufficient to backup my home directory. What data will be lost if I backup home and copy it to Gutsy?

2.) I installed several packets. Can I do the following:
dpkg --get-selections "*" > packetlist - under Feisty
dpkg --set-selections < packetlist followed by dselect install  - under Gutsy

3.) Which options uses DM-Crypt by default after installing gutsy?
AFAIK "ESSIV" should be used instead of "plain" as IV mode. I also read that DM crypt uses no salt by default for increasing the password's entropy

Thank you!


Regards,
  Andreas Weller

---

### Post by zvacet on 2007-10-11
If you upgrade via net you will have same version as you download  and install it.So,you will get HD encryption both ways.Let somebody correct me if I´m wrong.

---

