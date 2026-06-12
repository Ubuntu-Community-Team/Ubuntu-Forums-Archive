---
title: "Problem with installing ubuntu 9.10 on an iMac G5"
date: 2010-04-16
forum: Installation &amp; Upgrades
---

### Post by egalois on 2010-04-16
Hey guys!

I want to install ubuntu 9.10 on my iMac G5 ppc. I downloaded it under: [http://cdimage.ubuntu.com/ports/releases/9.10/release/]("http://cdimage.ubuntu.com/ports/releases/9.10/release/") and wrote it onto a DVD.
It was possible to boot from the DVD but after a while my iMac hang up at the point:

returning from prom_init

I also tried the alternate version and different options like 'install video=ofonly' and 'nosplash-powerpc-64' without success.
It would be great if someone could help me! Thx

e.galois

---

### Post by zvacet on 2010-04-16
Did you check [md5sum]("https://help.ubuntu.com/community/HowToMD5SUM")? If you have miss-match download same iso with torrent and point download to the folder where your existing iso is.Torrent will just check iso for bad files and replace them with good ones.After that burn iso on lower possible speed.On first boot check disc integrity.If everything is good go for install.

---

### Post by egalois on 2010-04-17
Thank you for your help!

My hash number of md5sum is:

fa2c5eb18dfb2e82fffa661fac75a240

for the ubuntu-9.10-desktop-powerpc.iso and for ubuntu-9.10-alternate-powerpc.iso it is:

1433302714a234d72626aeef6d534308

Unfortunately on [https://help.ubuntu.com/community/UbuntuHashes]("https://help.ubuntu.com/community/UbuntuHashes") exists no hash number for ppc and I didn't found it on the Web. 
I also tried to burn the DVD with lower speed but my iMac is hanging up again. What else could I do?

---

### Post by zvacet on 2010-04-17
[Md5sums]("http://cdimage.ubuntu.com/ports/releases/9.10/release/MD5SUMS")

You can also look [here]("http://ubuntuforums.org/showthread.php?t=427714") an d see if you can find any useful info.

---

### Post by veonline on 2010-04-19
I'm trying to install on a powermac G5 but i found the exact same problem. 
I've tried other distros and i found similar issues but usually selecting the 64bit kernel at yaboot menu was sufficient to go on and install.
But with Ubuntu there is no way...
I'm sad because i'm trying to find a human distro to raise from the dusty corner my glorious powermac, thought ubuntu was the right choise.
I want to try again, help me please :(

---

