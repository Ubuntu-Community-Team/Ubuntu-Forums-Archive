---
title: "MD5SUM mismatch"
date: 2006-10-26
forum: Installation &amp; Upgrades
---

### Post by bugnotme on 2006-10-26
I get the following error:

Failed to fetch cdrom:[Ubuntu 6.10 _Edgy Eft_ - Release i386 (20061025.1)]/pool/main/s/synaptic/synaptic_0.57.11ubuntu12_i386.deb MD5Sum mismatch

when using the alternate CD  to do 'sudo apt-get update && sudo apt-get dist-upgrade'.

Is the MD5 stored on the CD or retrieved from a Server? Is my CD bad? apt-get suggests using fix-missing but I'm afraid to do something like that on an upgrade. 

What should I do?

---

### Post by magicfab on 2006-10-26
Check the MD5 Sum of the .ISO you used to burn the CD, that will let you know for sure if the CD is ok - which doesn't seem to be the case.

---

### Post by bugnotme on 2006-10-27
ISO is fine, the only thing I'm concerned about is the CD is bad.

Assuming the CD is corrupted for only that one file, how can I fix this by fetching this one file from the repos?

---

### Post by magicfab on 2006-10-27
Did you try checking for CD integrity from the initial menu at boot ?

---

### Post by bugnotme on 2006-10-27
I didn't boot from the CD, I did apt-cdrom add and then update, dist-upgrade.

I will check the integrity of the CD itself using MD5 in a few hours (I needed the ISO size to do that).

It doesn't matter though. Unless I was receiving a bad MD5 from a server, I will still have to work around the problem by either installing the package from an Internet repository or hold it back (I don't feel like wasting another CD). 

I'll try to manually add the .deb to the cache and see if that works out.

---

### Post by yage on 2006-10-27
argh! I'm having a serious problem now. I have downloaded the iso image several times and finaly i got the MD5 checksums to match. But i'm still having problem installing. After partitioning and all that the files are being copied to the HD but when the progressbar says its only i few minutes left it just hangs there.... what to do? install dapper and upgrad to edgy? suggestions?

---

