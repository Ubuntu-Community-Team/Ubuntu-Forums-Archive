---
title: "Install To Disk Error"
date: 2006-06-28
forum: Installation &amp; Upgrades
---

### Post by Sethro on 2006-06-28
Hi guys,

Okay so I got a hold of Live CD... everything is beautiful right? I now try to install to disk. I get past the "Choose You Language" "User Name" and then I setup :

Windows XP : 40 GB
SWAP         : 15 GB
"/"              : 50 GB

* Everything goes great is starts to install but then suddenly stops!, like nothing happenened??

Help?

---

### Post by Drakkor on 2006-06-28
Did you verify the md5 hash, and when booting before installing verify the disk was not corrupted ? I had an install freeze up because of a bad burn. Hope this helps. Good Luck !

---

### Post by Sethro on 2006-06-28
wow thanx for getting back to me.. ur my hero

okay so how do I verify the md5 hash , and iam using a dvd instead of a cd, does this matter?

---

### Post by Drakkor on 2006-06-28
I verified on Windows with a program called DigestIt: [http://digestit.kennethballard.com/](http://digestit.kennethballard.com/)

Here are the sums for the different versions:
df03811bfc9f2a73672887a36d531965  ubuntu-6.06-alternate-amd64.iso
b2e9120f06d70cc076c1852c6c04654e  ubuntu-6.06-alternate-i386.iso
12bd53a48d7afbcfb0eae6794a1ac02f  ubuntu-6.06-alternate-powerpc.iso
722b8b4a75f977a76a722d4a2b071b19  ubuntu-6.06-desktop-amd64.iso
e2e5e0bfb2edffd2ce02dd77bda4558e  ubuntu-6.06-desktop-i386.iso
410d766d75a3afaa7f04c0c7dbdfd8da  ubuntu-6.06-desktop-powerpc.iso
02772b8b3461c246a2154aa6e699335b  ubuntu-6.06-server-amd64.iso
4c7c835d244453b9a29d397e5cd973fd  ubuntu-6.06-server-i386.iso
c1f9c3dc78572bc2ce76d44776949fcc  ubuntu-6.06-server-powerpc.iso
82da246064785adb7b87e5aa0cb5764c  ubuntu-6.06-server-sparc.iso
 
Also even if they are correct you should also verify the burned disk is ok,there should be a selection when you boot from the dvd below the start or install
option to check the disk. My md5 sums where ok,but when verifying the burned disk,I had one checksum error,so I just reburned the disk,then again checked it, and it was fine, and the installation went off without a hitch !
Good Luck ! :)

---

