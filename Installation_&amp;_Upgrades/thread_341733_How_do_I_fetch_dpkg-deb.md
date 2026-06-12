---
title: "How do I fetch dpkg-deb?"
date: 2007-01-19
forum: Installation &amp; Upgrades
---

### Post by GoUbuntu on 2007-01-19
I'm trying to install build essential via synaptic, and it downloads 12 of the 13 files, but then it says:

W: Failed to fetch [http://nz.archive.ubuntu.com/ubuntu/pool/main/d/dpkg/dpkg-dev_1.13.11ubuntu7_all.deb](http://nz.archive.ubuntu.com/ubuntu/pool/main/d/dpkg/dpkg-dev_1.13.11ubuntu7_all.deb)
  Could not connect to nz.archive.ubuntu.com:80 (202.7.6.10). - connect (111 Connection refused)

The same thing has been happening for a few days.  What can I do to get the package?  (I'm in New Zealand, BTW, hence the 'nz' in the URL)

Thanks in advance,
GoUbuntu

---

### Post by nsleiman on 2007-01-19
I think you can change the location from nz to us or something. It happened with me once but i downloaded the package from packages.ubuntu.com and: sudo dpkg -i pack.deb et voila :)

---

### Post by mcduck on 2007-01-19
if it's only one package you are missing you could just download it from [http://packages.ubuntu.com/]("http://packages.ubuntu.com/") and install it manually.

---

### Post by az on 2007-01-19
Taht package, along with all the other dependencies to build-essential are on the install cd.  Just boot into Ubuntu adn pop the cd into the drive.  The repository on the disk is apart from the live session.

sudo apt-cdrom add

---

### Post by GoUbuntu on 2007-01-20
Thanks for your help.

In the end I acutally didn't need any of these methods (after 4 or 5 days I was able to connect), but similar things have happened before so I'm glad to have gained the knowledge so that I can resolve the issue if it happens again.

---

