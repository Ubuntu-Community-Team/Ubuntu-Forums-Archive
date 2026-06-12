---
title: "When trying to upgrade lately...I can't"
date: 2008-04-24
forum: Installation &amp; Upgrades
---

### Post by TheGuyWhoGotOn on 2008-04-24
I get this when I try to download anything using a package manager:

> 
W: GPG error: [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) gutsy Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 58403026387EE263


It also downloads 0 bytes of most of the package files...I think this started when I tried to upgrade to Ubnutu 8.04 but I'm not sure.

---

### Post by TheGuyWhoGotOn on 2008-04-26
Sorry for the bump but I can't download any files and get them verified everything is buggy, please can somebody help me?

---

### Post by TheRingmaster on 2008-04-26
> **TheGuyWhoGotOn said:**
> Sorry for the bump but I can't download any files and get them verified everything is buggy, please can somebody help me?

try this from winehq guide to installing wine. you just need a key so that the computer knows that the software sources are safe.

> First, open a terminal window (Applications->Accessories->Terminal).  Then  add the repository's key to your system's list of trusted APT keys by copy and  pasting the following:
  *wget -q [http://wine.budgetdedicated.com/apt/387EE263.gpg](http://wine.budgetdedicated.com/apt/387EE263.gpg) -O- | sudo apt-key add -*


---

### Post by TheGuyWhoGotOn on 2008-04-26
> **TheRingmaster said:**
> try this from winehq guide to installing wine. you just need a key so that the computer knows that the software sources are safe.

But I've already done that and would this really affect everything? I'll try this...Again...

I praise you! It worked!!

---

### Post by TheGuyWhoGotOn on 2008-04-26
Sorry bump but I've gotten this when I try to upgrade to 8.04...I have an active 1mb/s with all ports that are needed open...

> 
Failed to fetch [http://ca.archive.ubuntu.com/ubuntu/dists/hardy/Release.gpg](http://ca.archive.ubuntu.com/ubuntu/dists/hardy/Release.gpg) Connection failed
Failed to fetch [http://ca.archive.ubuntu.com/ubuntu/dists/hardy/main/i18n/Translation-en_CA.bz2](http://ca.archive.ubuntu.com/ubuntu/dists/hardy/main/i18n/Translation-en_CA.bz2) Could not connect to ca.archive.ubuntu.com:80 (129.97.134.71), connection timed out
Failed to fetch [http://ca.archive.ubuntu.com/ubuntu/dists/hardy/restricted/i18n/Translation-en_CA.bz2](http://ca.archive.ubuntu.com/ubuntu/dists/hardy/restricted/i18n/Translation-en_CA.bz2) Connection failed
Failed to fetch [http://ca.archive.ubuntu.com/ubuntu/dists/hardy/universe/i18n/Translation-en_CA.bz2](http://ca.archive.ubuntu.com/ubuntu/dists/hardy/universe/i18n/Translation-en_CA.bz2) Connection failed
Failed to fetch [http://ca.archive.ubuntu.com/ubuntu/dists/hardy/multiverse/i18n/Translation-en_CA.bz2](http://ca.archive.ubuntu.com/ubuntu/dists/hardy/multiverse/i18n/Translation-en_CA.bz2) Connection failed
Failed to fetch [http://ca.archive.ubuntu.com/ubuntu/dists/hardy-updates/Release.gpg](http://ca.archive.ubuntu.com/ubuntu/dists/hardy-updates/Release.gpg) Could not connect to ca.archive.ubuntu.com:80 (129.97.134.71), connection timed out
Failed to fetch [http://ca.archive.ubuntu.com/ubuntu/dists/hardy-updates/main/i18n/Translation-en_CA.bz2](http://ca.archive.ubuntu.com/ubuntu/dists/hardy-updates/main/i18n/Translation-en_CA.bz2) Could not connect to ca.archive.ubuntu.com:80 (129.97.134.71), connection timed out
Failed to fetch [http://ca.archive.ubuntu.com/ubuntu/dists/hardy-updates/restricted/i18n/Translation-en_CA.bz2](http://ca.archive.ubuntu.com/ubuntu/dists/hardy-updates/restricted/i18n/Translation-en_CA.bz2) Connection failed


---

### Post by XVII on 2008-04-26
Download the alternate CD through one of the [torrents]("http://www.acc.umu.se/~mighty/ubuntu/").  Then you just pop it in and choose to upgrade.

---

### Post by TheRingmaster on 2008-04-27
> **TheGuyWhoGotOn said:**
> Sorry bump but I've gotten this when I try to upgrade to 8.04...I have an active 1mb/s with all ports that are needed open...

the server may still be under heavy load due to the recent release of hardy. Give it a day or two, if the issue doesn't clear up, we know there's a more pressing issue at hand.

---

### Post by TheGuyWhoGotOn on 2008-05-01
> **TheRingmaster said:**
> the server may still be under heavy load due to the recent release of hardy. Give it a day or two, if the issue doesn't clear up, we know there's a more pressing issue at hand.

I get "Could not download release notes please check your internet connection"...I assure you it's not my internet connection -.-...

@XVII:

The 8.04 one?

---

### Post by XVII on 2008-05-01
> **TheGuyWhoGotOn said:**
> 
The 8.04 one?

Yes, ubuntu-8.04-alternate.

---

### Post by TheGuyWhoGotOn on 2008-05-05
> **XVII said:**
> Yes, ubuntu-8.04-alternate.

Thanks but now I'm just pissed, I but in the disk and opened the updater click upgrade to 8.04 and then when it got the the END of the *installation* not the downloading part I got and error which I copied and it didn't go to my clipboard.

It was something about couldn't copy theme "Insert address here (On the CD)" because of a mismatch in the Md5 checksum or something.

wtf?

---

### Post by XVII on 2008-05-05
> **TheGuyWhoGotOn said:**
> Thanks but now I'm just pissed, I but in the disk and opened the updater click upgrade to 8.04 and then when it got the the END of the *installation* not the downloading part I got and error which I copied and it didn't go to my clipboard.

It was something about couldn't copy theme "Insert address here (On the CD)" because of a mismatch in the Md5 checksum or something.

wtf?

I don't know what the problem is, but the md5 checksums are [here]("http://www.mirrorservice.org/sites/releases.ubuntu.com/hardy/MD5SUMS").

---

