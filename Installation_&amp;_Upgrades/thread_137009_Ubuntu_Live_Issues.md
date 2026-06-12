---
title: "Ubuntu Live Issues"
date: 2006-02-27
forum: Installation &amp; Upgrades
---

### Post by bipinbabu on 2006-02-27
Hi All,

I am very very new to Ubuntu, I have been using SUSE 10.0 for almost good 5 months now, am quite happy with it. I heard that Ubuntu is also a good distro. So here I am trying the LIVE version. 

I downloaded ubuntu-5.10-live-i386.iso from this site which was listed in the official Ubuntu website [http://ftp.ecc.u-tokyo.ac.jp/UBUNTU-CDS/5.10/ubuntu-5.10-live-i386.iso](http://ftp.ecc.u-tokyo.ac.jp/UBUNTU-CDS/5.10/ubuntu-5.10-live-i386.iso)

I tried to boot from the CD and it give me an error about the file or the CD being corrupt. I run a disk intergrity check and I get the message that the MD5sum does not match. So I checked my MD5sum on google and it does confirm that I have the right one...

This is the MD5 I have

**49f36f8aef009d6403360de23b5a47d4  ubuntu-5.10-live-i386.iso**

What could be wrong??? I have also tried burning the image again on a different disk this time through XP (man I was back on windows after a long time ;)  ). Still the same problem. Can somebody help?

Thanks

BB

---

### Post by newuser111 on 2006-02-27
that is the correct md5 sum for the live cd, it could be that it burned onto bad media

try burning slower, or try booting with acpi=off option

---

### Post by bipinbabu on 2006-02-27
Thanks dude, giving it another shot....running out to buy a new CD....will try and post it here give me half an hour

Thanks

BB

---

### Post by bipinbabu on 2006-02-27
No luck still the same....it says that the .install/vmlinuz md5 checksum failed. I checked the MD5 Checksum for this file..here it is

**AD1972F13ABF36D6CF8573DF17CB37D8**

Can someone verify this?

Dammn! I am liking the way Ubuntu is working for me....this definetely would endup with me being totally crazy about ubuntu.

Cheers,

BB

---

### Post by Bartender on 2006-02-27
Burn the CD at 1X or 2X, also don't waste yur time with cheap media.  Folks have reported success with quality discs (Memorex, Verbatim, etc.) when cheesy generic blanks were failing.
BTW, can you please tell me how you checked the burned CD's md5?  I've been trying to figure out a good way for Windows users to check the CD after burning it.  Even if you did it in Linux can you repeat the command for me please?

---

### Post by bipinbabu on 2006-02-28
Hey Bartender,

Great I am not sure if I am using a cheap sleezy media, unfortunately the brands you mentioned are a rarity here in India. The media I tried was a SONY and a Moserbaer. Anyway, will try it again..it was after a long time into windows....so I guess it would have been the windows also. 

Checking the MD5Checksum on windows, I downloaded a MD5Checksum calculator (i dont have the link now, back in Linux). I am not sure if this is what you wanted to know.

---

