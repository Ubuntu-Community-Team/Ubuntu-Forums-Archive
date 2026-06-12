---
title: "How do you install Oracle Instant Client?"
date: 2011-04-03
forum: Installation &amp; Upgrades
---

### Post by bobt_1234 on 2011-04-03
Can someone tell me how you install Oracle Instant Client on Kubuntu.

I have Oracle XE and Lazarus installed on a KB machine, but Lazarus can't connect because it's missing the file "libociei.so".

I found that file in the Oracle Instant Client which I downloaded and unzipped from Oracle.com.  However, I have no idea how to install it.  Normally you issue a "sudo" command of some sort.  I can't just copy the files because I don't have privileges to copy to the system folders, and don't know where to copy them to anyway.  The only online help I've found is for installing PHP with it, which I'm not interested in.

I'm still very new to Linux and am not familiar with the Linux ways of doing things.  In Windows you just run a setup.exe program that takes care of all the gory details for you.

Any help will be appreciated.  Thanks in advance.

---

### Post by Karlchen on 2011-04-03
Hello, bobt_1234.

Oracle does not offer .DEB packages for Debian based Linux versions like Ubuntu. Instead you will have to download the appropriate .RPM packages for Redhat, convert them to .DEB packages and install them.

Please, see this Ubuntu documentation for the details: [**Oracle Instant Client**]("https://help.ubuntu.com/community/Oracle%20Instant%20Client").

HTH,
Karl

---

