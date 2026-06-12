---
title: "Xubuntu alternate install CD errors"
date: 2007-02-12
forum: Installation &amp; Upgrades
---

### Post by CalcProgrammer1 on 2007-02-12
I downloaded the Xubuntu Alternate CD ISO because the PC I'm installing Xubuntu on only has 64MB RAM.  I started the base install and it errored out.  I then ran a test on the CD, and got the error:

[quote="xubuntu CD-ROM Integrity test error"]
Integrity Test Failed
The ./pool/main/w/w3m/w3m_0.5.1-4ubuntu2_i386.deb file failed the MD5 checksum verification.  Your CD-ROM or this file may have been corrupted.
[/quote]

The machine is a Pentium 133/64MB RAM, CD-ROM drive (24X).  The HDD is 40GB, but it was pulled from a dead laptop.  I had used the HDD in my good desktop with Ubuntu, but when I switched from 6.06 over to 6.10, it wouldn't boot, then I tried reinstalling and it couldn't complete a format on the drive.  I then moved the drive to the old Pentium desktop, trying to make an FTP server out of it.  Is there a way to test the image before I waste another CD on a possibly corrupted image, or should I test the CD in another PC?

---

### Post by LotsOfPhil on 2007-02-12
I got these from [http://ubuntu-cdimage.datahop.it/xubuntu/releases/6.06.1/release.1/MD5SUMS](http://ubuntu-cdimage.datahop.it/xubuntu/releases/6.06.1/release.1/MD5SUMS)
```
c837e79aa08a1bf78e609bf97dae1f00  xubuntu-6.06.1-alternate-amd64.iso
c0b54deca75e8e3a87988846c9ae1e44  xubuntu-6.06.1-alternate-i386.iso
d9629470753132c9379562ae327e7839  xubuntu-6.06.1-alternate-powerpc.iso
ab3acc3ca2a4830b3b9e9f2b73bd3076  xubuntu-6.06.1-desktop-amd64.iso
20d5b0e83e4a701d76739347520b133e  xubuntu-6.06.1-desktop-i386.iso
ac07d20b3190e7370e3fe4307df548bf  xubuntu-6.06.1-desktop-powerpc.iso

```

I assume they are the same for any mirror. Just type md5sum IMAGE

---

### Post by LotsOfPhil on 2007-02-12
Here are the 6.10 ones:
```

30b2e4211c8cab3328f8bba4a9758715  xubuntu-6.10-alternate-amd64.iso
fd706420fb2c1529707658ba43e9554a  xubuntu-6.10-alternate-i386.iso
eefea0c37b7b9a59e8e34f3a87d80d5e  xubuntu-6.10-alternate-powerpc.iso
38d6f02de8acc7838abaf2a5ddbc1d4d  xubuntu-6.10-desktop-amd64.iso
22dbcd0958d5f19be4ae4f91410a1170  xubuntu-6.10-desktop-i386.iso
91eeb4820708f34bc4a738a9464d451a  xubuntu-6.10-desktop-powerpc.iso

```

---

### Post by CalcProgrammer1 on 2007-02-12
Hmm...this is odd.  I ran the CD test on my good desktop (AMD AthlonXP 2600+, 768MB RAM, 80/120GB) but it tested fine.  Is there anything special you need to do to install on old systems with 64MB?

---

