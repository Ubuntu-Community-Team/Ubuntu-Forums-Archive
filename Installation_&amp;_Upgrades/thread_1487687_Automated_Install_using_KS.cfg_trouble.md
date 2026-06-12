---
title: "Automated Install using KS.cfg trouble"
date: 2010-05-19
forum: Installation &amp; Upgrades
---

### Post by smacneill on 2010-05-19
Hi Gang,  First off i'm very new to this so i may have missed the obvious.   I'm following the whitepaper on the ubuntu site to build a server to auto deploy clients using PXE boot.   I've modified the whitepaper a bit to match lucid instead of hardy in which it was written for.  

So far i've built my 10.04 server, installed DHCP / Apache / TFTP / DNS.
I've built a second server now that is my mirror, i built this mirror using apt-mirror and this server also runs Apache.

In my TFTPBoot directory i'm using the netboot.tar.gz from the lucid archive.

When i PXE boot my client i get an IP, it downloads pxelinux.0 without problems,  and it's going to my mirror for the files which i want.

Now the trouble:

My install fails pretty quickly saying it cannot find the files.  I hooked up a laptop and snooped and find that it's trying to download the files in a directory i dont have:

[http://192.168.1.10/ubuntu/dists/lucid/main/](http://192.168.1.10/ubuntu/dists/lucid/main/)**debian-installer**/binary-i386/Packages.gz

My mirror does **not **have that debian-installer directory by default...   So, my first instinct was to just create that directory, then move my binary-i386 (and contents) into it.   perfect.  Now when i boot it can find Packages.gz without problems, downloads and extracts.  

The real problem now is that the MD5 checksum for Packages.gz does not match what it expects.  

My gut is telling me i my PXE client is trying to go for a distribution that is not LUCID.   I have no idea what i need to correct to get around this.     Any help would be greatly appreciated.

-S

---

### Post by vikjon0 on 2010-10-21
On e.g. the lucid server CD you will find
dists/lucid/main/debian-installer

This is what you need, not the .gz from the the other dir.

---

