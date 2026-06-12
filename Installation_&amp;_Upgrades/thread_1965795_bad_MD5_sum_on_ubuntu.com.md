---
title: "bad MD5 sum on ubuntu.com"
date: 2012-04-26
forum: Installation &amp; Upgrades
---

### Post by tomhorsley on 2012-04-26
I downloaded the alternate CD iso images, and the amd64 version fails the checksum (I tried all 3 md5, sha1, and sha256). The i386 version passes. The gpg signature on the checksum file verifies correctly, so it really looks like something is wrong with the amd64 iso image. (I tried re-downloading it, but got the same failure on the 2nd try as well).

---

### Post by tomhorsley on 2012-04-26
Here's the details of what I downloaded and what I see:

```

tomh> wget http://releases.ubuntu.com/12.04/ubuntu-12.04-alternate-amd64.iso
tomh> ls -l ubuntu-12.04-alternate-amd64.iso 
-rw-rw-r-- 1 tweety tweety 729067520 Apr 25 08:51 ubuntu-12.04-alternate-amd64.iso
tomh> sha256sum ubuntu-12.04-alternate-amd64.iso 
fd58d2e7e6a2b7e3bc795bfe77f5b8eb23b5a5a19b3d32b017b11cabf7e73d32  ubuntu-12.04-alternate-amd64.iso
tomh> fgrep ubuntu-12.04-alternate-amd64.iso SHA256SUMS
f8d54df0afbab6a6248f6e2bcab3e68f01c04d52b0bb1f889d880ad3bc881ccb *ubuntu-12.04-alternate-amd64.iso

```

---

### Post by kolinab on 2012-04-26
I'm experiencing the same - the desktop-i386 checksum looks right, but the amd64 build doesn't match.

I synced these files from a recent daily version with zsync, trying a torrent right now to see if I get a different result. Interesting.

K

[edit] Confirmed - I triple checked the checksums on ubuntu-12.04-desktop-i386.iso. All three match:

```

kolin@insp:~/Downloads$ md5sum ubuntu-12.04-desktop-i386.iso 
d791352694374f1c478779f7f4447a3f  ubuntu-12.04-desktop-i386.iso
kolin@insp:~/Downloads$ sha1sum ubuntu-12.04-desktop-i386.iso 
94ca138ab6375cf7a72eb62325182beb9c44a997  ubuntu-12.04-desktop-i386.iso
kolin@insp:~/Downloads$ sha256sum ubuntu-12.04-desktop-i386.iso 
dc76b5ef8b242e2f4f05a0ca2265a1d5e7ace12da5d39c817ec251e0b2461d6f  ubuntu-12.04-desktop-i386.iso

```But no match on ubuntu-12.04-desktop-amd64.iso. This .iso was also 'finished' with zsync from a recent daily-live image:

```

kolin@insp:~/Downloads/doesn't md5$ md5sum ubuntu-12.04-desktop-amd64.iso 
57876b3740ee89e75c8fefc93a7ceee6  ubuntu-12.04-desktop-amd64.iso
kolin@insp:~/Downloads/doesn't md5$ sha1sum ubuntu-12.04-desktop-amd64.iso 
7a67974ca3fb92b39ea257fc463a76b85bc9be0e  ubuntu-12.04-desktop-amd64.iso
kolin@insp:~/Downloads/doesn't md5$ sha256sum ubuntu-12.04-desktop-amd64.iso 
2c32f3bbc7047a227d134d30cb2038b07c15a0a1bebbd253dbb7ead7dceaa21c  ubuntu-12.04-desktop-amd64.iso

```I've just downloaded the amd64 build from .torrent **and the checksums match this time**:

```

kolin@insp:~/Downloads/ubuntu$ md5sum ubuntu-12.04-desktop-amd64.iso 
128f0c16f4734c420b0185a492d92e52  ubuntu-12.04-desktop-amd64.iso
kolin@insp:~/Downloads/ubuntu$ sha1sum ubuntu-12.04-desktop-amd64.iso 
cb1afefcd9fb01d8bc02e53de63e70a2f6a6e7de  ubuntu-12.04-desktop-amd64.iso
kolin@insp:~/Downloads/ubuntu$ sha256sum ubuntu-12.04-desktop-amd64.iso 
eca367bb12f7bf197cfb2ab4835ac073b9ed902a8c37c075c28dd6b9f0e4bb55  ubuntu-12.04-desktop-amd64.iso

```So the zsync version doesn't match but the torrent version matches. Why?

---

### Post by richud on 2012-04-26
yeah failed for me too

MD5SUM file 9fcc322536575dda5879c279f0b142d7 *ubuntu-12.04-alternate-amd64.iso

MD5SUM of downloaded
$ md5sum ubuntu-12.04-alternate-amd64.iso
09cd432eec022881e9d5f58e6a32bab3  ubuntu-12.04-alternate-amd64.iso

---

### Post by mineral4x on 2012-04-26
The MD5 found in [http://releases.ubuntu.com/precise/MD5SUMS](http://releases.ubuntu.com/precise/MD5SUMS) does not match the actual MD5 of the iso found at [http://releases.ubuntu.com/precise/ubuntu-12.04-desktop-amd64.iso](http://releases.ubuntu.com/precise/ubuntu-12.04-desktop-amd64.iso)

---

### Post by kernelles on 2012-04-26
Same problem here. What's going on? I've downloaded several times, both by torrent and directly, and used gisomount to calculate md5sum. Either I get the wrong sum, or a blank one.

---

### Post by kolinab on 2012-04-26
Wait, is this a matter of calculating a checksum on a 32 bit machine of a 64 bit image? Can't be . . . but that's my situation right now. . .

---

### Post by richud on 2012-04-26
just downloaded from different mirror ([http://nl.releases.ubuntu.com/precise/](http://nl.releases.ubuntu.com/precise/)) and its ok

$ md5sum "ubuntu-12.04-alternate-amd64 (1).iso"
9fcc322536575dda5879c279f0b142d7  ubuntu-12.04-alternate-amd64 (1).iso


using vbindiff between them - the (25th) release on releases.ubuntu.com/precise/ is in fact from 23rd and final (as far as MD5SUM says) is released on 25th

---

### Post by Ub28 on 2012-04-26
I'm having exactly the same problem.

Can someone please verify the sha1sums and md5sums on the download page: [http://releases.ubuntu.com/precise/]("http://releases.ubuntu.com/precise/")

---

### Post by kolinab on 2012-04-26
Hi! We're seeing the same here:

See thread [http://ubuntuforums.org/showthread.php?t=1965784](http://ubuntuforums.org/showthread.php?t=1965784)

---

### Post by jawilljr on 2012-04-26
Same thing here.

For ubuntu-12.04-desktop-amd64.iso I am getting this md5sum:

```
57876b3740ee89e75c8fefc93a7ceee6
```

On [This site](http://releases.ubuntu.com/12.04/MD5SUMS) it says:

```
128f0c16f4734c420b0185a492d92e52 *ubuntu-12.04-desktop-amd64.iso
```

Jerry

---

### Post by kolinab on 2012-04-26
> **jawilljr said:**
> Same thing here.

For ubuntu-12.04-desktop-amd64.iso I am getting this md5sum:

```
57876b3740ee89e75c8fefc93a7ceee6
```On [This site]("http://releases.ubuntu.com/12.04/MD5SUMS") it says:

```
128f0c16f4734c420b0185a492d92e52 *ubuntu-12.04-desktop-amd64.iso
```Jerry

That's exactly what I had.

[Edit] Now I think it was all my fault - I was checking the wrong files. Zsync seems to have done the job right but it put the new files right in /home, not in /home/Downloads where I expected them to be. Now my files match the server's list.

---

### Post by kernelles on 2012-04-26
Tried the mirror posted above, and had the same problem in gisomount, so I installed furiusisomount and checked it with that, and it worked.

---

### Post by CharlesA on 2012-04-26
Threads merged.

Has anyone checked the ISO from the torrents?

---

### Post by tomhorsley on 2012-04-26
I just got the torrent version downloaded, and the checksum matches on it. If I use cmp to see where they differ I get:

```

tomh> cmp *amd64*.iso
bad-ubuntu-12.04-alternate-amd64.iso ubuntu-12.04-alternate-amd64.iso differ: char 441, line 4

```

So the difference occurs pretty early, but isoinfo -d shows all the same header info. No idea what happened here.

---

### Post by Yellow Pasque on 2012-04-26
[https://bugs.launchpad.net/ubuntu-website-content/+bug/988994](https://bugs.launchpad.net/ubuntu-website-content/+bug/988994)

---

### Post by CharlesA on 2012-04-26
I'm curious if the sha1sum is correct, or if it has the same problem with a mismatched md5sum.

EDIT: Don't mind me, this was in response to:

> **mineral4x said:**
> The MD5 found in [http://releases.ubuntu.com/precise/MD5SUMS](http://releases.ubuntu.com/precise/MD5SUMS) does not match the actual MD5 of the iso found at [http://releases.ubuntu.com/precise/ubuntu-12.04-desktop-amd64.iso](http://releases.ubuntu.com/precise/ubuntu-12.04-desktop-amd64.iso)

---

### Post by schlameel on 2012-04-26
I'm getting an issue where the torrent for 64-bit desktop, when used in Transmission, causes all networking to virtually stop.  I ran Transmission with the Xubuntu 12.04 64-bit desktop .torrent and it works fine.  If I try to start up the one from Ubuntu it kills networking.

---

### Post by kolinab on 2012-04-27
Hi schlameel,

Sorry you're having trouble with it. I think that your question will be answered more quickly if you start a new thread though - it's just that not many people are likely to notice your (new) question at the bottom of this thread!

Regarding the funny checksums, I never did figure it out. Did anyone figure out why these didn't match in the beginning? Exciting times on official Precise Day One :)

I know many of you have been running it for months already, but I was pretty impressed with myself that I got it installed on four laptops yesterday! Only one of them is not 'happy' yet, and I have one more to do today.

K

---

