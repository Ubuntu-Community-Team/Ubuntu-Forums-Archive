---
title: "[HOWTO] Burning an uncorrupted installation media: do not use MD5 checks (use SHA256)"
date: 2011-12-04
forum: Installation &amp; Upgrades
---

### Post by mo.mashi on 2011-12-04
INTRO:

Yesterday, I downloaded and tried to install Ubuntu 11.10. I kept burning disk with errors despite the fact that my downloaded ISO's MD5 corresponded to the signature on Ubuntu's website. After a while of chasing after my own tail, it occurred that I could be dealing with a HASH collision. A collision is when two different files are similar enough that they produce the same HASH signatures. The longer the HASH key produced by an algorithm, the less a collision is likely. Length is measured in bits. MD5 is a 128bit algorithm which works well for distinguishing smaller files but at the size of DVD ISOs, it gives collisions. Meaning that it won't pick small levels of corruption in a DVD download. BAD! It gave a collision with me. When I ran SHA256 on my ISO, it didn't pass comparison with the SHA256 signatures posted by Ubuntu (whereas the MD5s were matching). So, having come across these issues, I decided make this make this HOWTO for other people that may have come across the problems of corrupted installation media. 

SOLUTION:

STEPS TO BURNING A GOOD INSTALLATION MEDIA AND VERIFYING IT:

[1] MAKE SURE YOUR ISO DOWNLOADED CORRECTLY

Don't verify the download with MD5! It's too weak: if a downloaded   DVD/CD image is only slightly corrupted, it may still give you a passing   MD5 (this happened to  me). Ubuntu also gives out the SHA256  signatures of their media. Much  less risk of a collision (that's when  two different files come out with  the same hash signature). I found the  SHA256 signatures here:

[http://sles-smt.uni-konstanz.de/linrz/linrz.hiwi.rz.uni-konstanz.de/images/ubuntu/checksums](http://sles-smt.uni-konstanz.de/linrz/linrz.hiwi.rz.uni-konstanz.de/images/ubuntu/checksums)


open the prompt, go to the  directory of your iso and type:

sha256sum <put the name of your ISO here>.iso

Eg:
sha256sum ubuntu-11.10-dvd-amd64.iso 

if sha256sum doesn't work, download and install the jacksum package and execute the following command:

jacksum -a SHA256 <name of your iso>.iso

)

Compare to results of the web.

[2] WHEN YOU BURN YOUR CD/DVD, use slowest speed your burner hardware  can  handle and check the verify CD/DVD option in your burning software.

[3] WHEN YOU BOOT YOUR CD/DVD: use the check CD/DVD option. 

It may be a bit more work then your used to  but trust me, the last   thing you want to be doing is running a corrupted installation. At the   best, the installer will quit on you, at the worst, you'll be running a   corrupted OS without realizing it....

---

### Post by drdos2006 on 2011-12-04
Nice pickup.

regards

---

