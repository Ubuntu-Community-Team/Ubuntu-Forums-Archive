---
title: "Updates, apt-get: security? How do we know we are downloading true  packages?"
date: 2006-10-27
forum: Installation &amp; Upgrades
---

### Post by joseph221b on 2006-10-27
Hi, everybody. I'm new to Ubuntu, but old with Gnu/Linux.

A question that is burning and important....

When we download CD iso, we use md5 hashes that are signed with Ubuntu's key to verify that a) our download was not messed up with errors and b) we are not downloading malicious software from a hacked mirror, for example. It's a great and important practice.


So, when we go to get additional packages, or just update the ones we have now, how do we handle the same issues? (I'm assuming Ubuntu uses apt-get mainly...).

How do we know that the updater is:
a) getting packages from the right source (i.e. which ftp site)
b) getting packages that have not been hacked to have Trojan Horses, etc.


If there are some people out there who are really familiar with apt-get who could elucidate this for me, I'd be thankful!


Thanks.

Joe

---

### Post by nino on 2006-10-27
See the Debian wiki page on secure apt for a description how it works:
[http://wiki.debian.org/SecureApt]("http://wiki.debian.org/SecureApt")

In short, the Release file is signed with GPG and contains the checksum of the Packages file, which contains checksums of each package.

---

### Post by joseph221b on 2006-10-27
Hey, Nino. Thanks for getting back to me so quickly. I appreciate it.

So, in short, the process is similar to downloading an iso, but it happens automatically?

1. download file
2. compute hash
3. verify hash against signed hash


Is this correct? 

And, do you know of a way to verify this? Does apt-get tell us that it's doing these things?

Thanks.

Joe

---

### Post by skymt on 2006-10-27
> **joseph221b said:**
> So, in short, the process is similar to downloading an iso, but it happens automatically?

1. download file
2. compute hash
3. verify hash against signed hash

Is this correct? 

And, do you know of a way to verify this? Does apt-get tell us that it's doing these things?

It's not a hash, it's a cryptographic signature. It not only makes sure that the download wasn't changed in transmission, it will also warn you if the package isn't from a trusted source. See [Wikipedia](http://en.wikipedia.org/wiki/Digital_signature) for details.

apt-get (and aptitude, and Synaptic) doesn't tell you about successful signature verification, but it will warn you very strongly if the package is unsigned or if the signature doesn't match the file.

---

### Post by joseph221b on 2006-10-27
1. download file
2. compute hash
3. verify hash against signed hash


Hi, Skymt. Thanks for the reply.


> It's not a hash, it's a cryptographic signature. 

According to the wikipedia article you pointed me to, a cryptographic signature is a hash. Are you saying something different here?


> apt-get (and aptitude, and Synaptic) doesn't tell you about successful signature verification, but it will warn you very strongly if the package is unsigned or if the signature doesn't match the file.

So, if the file has been altered, then its hash won't be correct, and hence won't match the signature, and then apt-get will tell me? Cool!


I found info on "apt-secure", included in apt 0.6. Do you know if Ubuntu uses apt of this version?


Thanks.

Joe

---

### Post by skymt on 2006-10-27
> **joseph221b said:**
> According to the wikipedia article you pointed me to, a cryptographic signature is a hash. Are you saying something different here?It's not a hash in the same way as the checksum for an ISO image, which was the comparison you made. I should have made that clear. My bad.> **joseph221b said:**
> So, if the file has been altered, then its hash won't be correct, and hence won't match the signature, and then apt-get will tell me? Cool!Yep!

EDIT: As I said, it will also tell you if the package isn't signed by someone you trust. It wouldn't be much good to only verify package integrity. Trust is a much more important part of the picture.> **joseph221b said:**
> I found info on "apt-secure", included in apt 0.6. Do you know if Ubuntu uses apt of this version?It looks like Ubuntu (as of Edgy, anyway) uses apt 0.6.45, so yes.

---

