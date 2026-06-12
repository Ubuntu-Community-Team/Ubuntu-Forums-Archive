---
title: "Why do ALL the Ubuntu Family Alternative CDs have 7 &quot;Errors&quot;??"
date: 2007-09-02
forum: Installation &amp; Upgrades
---

### Post by OzzyFrank on 2007-09-02
OK, for the full story, check out: [http://ubuntuforums.org/showthread.php?p=3296314#post3296314](http://ubuntuforums.org/showthread.php?p=3296314#post3296314)

In short, while looking for an MD5sum checker for Linux, and one that can handle the finished CD not just the individual .iso files, I found a Windows freeware app called **[COLOR="Purple"]MD5summer[/COLOR]**. It checks all the individual hashes for all files contained in **md5sum.txt**, found on the Ubuntu CDs and other distros (another Windows app, **[COLOR="#800080"]FileCheckMD5[/COLOR]**, is my #1 choice but cannot handle the .txt extension, dammit).

Anyway, this MD5summer is fine with the Live CDs, but for all the Alternative CDs gives 7 errors each, without fail (in Windows... in Ubuntu the first error causes the app to crash). These are all tested OK the normal way, of course, and the "errors" in the app are always the same:

.\install\netboot\pxelinux.cfg\default ERROR: X:\.\install\netboot\pxelinux.cfg\default does not exists.
.\install\netboot\pxelinux.0 ERROR: Checksum did not match.
.\pool\main\l\linux-source-2.6.20\firewire-core-modules-2.6.20-15-generic-di_2.6.20-15.27_i386.udeb ERROR: X:\.\pool\main\l\linux-source-2.6.20\firewire-core-modules-2.6.20-15-generic-di_2.6.20-15.27_i386.udeb does not exists.
.\pool\main\l\linux-source-2.6.20\pcmcia-storage-modules-2.6.20-15-generic-di_2.6.20-15.27_i386.udeb ERROR: X:\.\pool\main\l\linux-source-2.6.20\pcmcia-storage-modules-2.6.20-15-generic-di_2.6.20-15.27_i386.udeb does not exists.
.\pool\restricted\l\linux-restricted-modules-2.6.20\nic-restricted-firmware-2.6.20-15-generic-di_2.6.20.5-15.20_i386.udeb ERROR: X:\.\pool\restricted\l\linux-restricted-modules-2.6.20\nic-restricted-firmware-2.6.20-15-generic-di_2.6.20.5-15.20_i386.udeb does not exists.
.\pool\restricted\l\linux-restricted-modules-2.6.20\nic-restricted-modules-2.6.20-15-generic-di_2.6.20.5-15.20_i386.udeb ERROR: X:\.\pool\restricted\l\linux-restricted-modules-2.6.20\nic-restricted-modules-2.6.20-15-generic-di_2.6.20.5-15.20_i386.udeb does not exists.
.\pool\restricted\l\linux-restricted-modules-2.6.20\linux-restricted-modules-2.6.20-15-generic_2.6.20.5-15.20_i386.deb ERROR: X:\.\pool\restricted\l\linux-restricted-modules-2.6.20\linux-restricted-modules-2.6.20-15-generic_2.6.20.5-15.20_i386.deb does not exists.

Is this normal? I mean, the self-test looks at the same md5 file and sees nothing wrong, so why do I always get these same errors in this app? Obviously, I just have to expect and ignore 7 errors for Alternative CDs, but am curious to see if any of you knows why this is happening at all.

So when is someone in the Ubuntu world going to make a simple md5 checker for ISOs and a more advanced one for all these Ubuntu CDs we burn?? C'mon guys, we have enough media players and network apps... how about making more useful apps like these to fill an obvious void, hehe??

---

### Post by mikewhatever on 2007-09-02
About the packages it says do not exist, I think they are really not there, well, at least the restricted ones.

---

