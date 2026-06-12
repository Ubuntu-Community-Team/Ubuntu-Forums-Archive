---
title: "Installing Ubuntu on a Dell Poweredge 1550"
date: 2010-07-28
forum: Installation &amp; Upgrades
---

### Post by Madgemade on 2010-07-28
Hi I'm new here and need some help installing ubuntu 10.04 server on a Dell Poweredge 1550 rack mount server.

At first I tried to install it from a CD burned by Brasro But it only got to 17% 'loading installer components' then hung for a bit them displayed the message that the CD may be defected and to check it for integrity

After a bit of searching I found that Brasro may have been causing these errors so I removed it and replaced it with K3b I re-burned the disk and tried again same error at 17%.

It turns out my CD-ROM drive is old, tired and doesn't work properly so I am now trying to PXE boot it over my network using this tutorial [https://help.ubuntu.com/community/Installation/WindowsServerNetboot](https://help.ubuntu.com/community/Installation/WindowsServerNetboot) it all works good up if very slowly up to the installer but when it gets to the selecting of the mirror it cannot connect to any of them and gets stuck there it seems its not Evan trying to connect to the Internet.However the first time I used the PXE boot it worked great until I tried to get the ISO of a CD that caused my original error but a=every time I have tried after it Fails?

Thanks in Advance for any help!

---

### Post by Madgemade on 2011-11-30
I managed to fix this by using PXE boot with remote download and install and it is working fine.

---

