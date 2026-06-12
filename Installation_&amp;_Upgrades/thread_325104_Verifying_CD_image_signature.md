---
title: "Verifying CD image signature"
date: 2006-12-25
forum: Installation &amp; Upgrades
---

### Post by ultranet on 2006-12-25
This is what i did, but i'm getting an error. Any thoughts?

$apt-get source ubuntu-keyring
$cd ubuntu-keyring-2005.01.12.1/keyrings/
$gpg --import ubuntu-archive-keyring.gpg 
$gpg --verify MD5SUMS.gpg ubuntu-6.10-desktop-i386.iso 
gpg: Signature made Thu 26 Oct 2006 04:36:44 AM CDT using DSA key ID FBB75451
gpg: BAD signature from "Ubuntu CD Image Automatic Signing Key <cdimage@ubuntu.com>"

$gpg -v --list-keys FBB75451
gpg: using PGP trust model
pub   1024D/FBB75451 2004-12-30
uid                  Ubuntu CD Image Automatic Signing Key <cdimage@ubuntu.com>

---

### Post by NeoLithium on 2006-12-25
Here's a nice walkthrough for verifying MD5Sums
[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

---

### Post by ultranet on 2006-12-25
I was verify&#305;ng the signature on the wrong file:

$gpg --verify MD5SUMS.gpg MD5SUMS
gpg: Signature made Thu 26 Oct 2006 04:36:44 AM CDT using DSA key ID FBB75451
gpg: Good signature from "Ubuntu CD Image Automatic Signing Key <cdimage@ubuntu.com>"
gpg: WARNING: This key is not certified with a trusted signature!
gpg:          There is no indication that the signature belongs to the owner.
Primary key fingerprint: C598 6B4F 1257 FFA8 6632  CBA7 4618 1433 FBB7 5451

---

