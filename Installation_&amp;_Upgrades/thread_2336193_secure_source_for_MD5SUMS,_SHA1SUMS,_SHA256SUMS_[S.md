---
title: "secure source for MD5SUMS, SHA1SUMS, SHA256SUMS [SUGGESTION]"
date: 2016-09-05
forum: Installation &amp; Upgrades
---

### Post by MDM72 on 2016-09-05
I am currently using a Windows computer and don't have access to my Linux computers. I want download Ubuntu and verify that my download is secure. I'm fully capable of doing checksum checking, I just need to get the checksum files.

The problem I'm having is getting a secure copy of the checksum files. When I go to [https://help.ubuntu.com/community/UbuntuHashes](https://help.ubuntu.com/community/UbuntuHashes) , that webpage redirects me to where I can download the hash files from an unsecure http connection. If I don't trust the .ISO file, I really can't trust the hash files either. The "How To" pages even hint at this. From [https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM) , "The MD5 hash must be signed or come from a secure source (an HTTPS page) of an organization you trust."

I think an ideal solution would be to put these small files in an https portion of ubuntu.com so that I could easily be sure that my copy of Ubuntu is secure.

As a side discussion, while gpg may be an option, that would require downloading, installing, and running additional steps. It might be possible, but it's a much more complicated solution.

---

### Post by Dennis N on 2016-09-05
I have noticed that Linux Mint uses signed sha256sum which you verify with gpg. Then you use that verified sha256sum to check the integrity of the iso you downloaded. Is that what you had in mind? 

Reference link to their procedure:
[https://linuxmint.com/verify.php](https://linuxmint.com/verify.php)

Actually, it was very easy to do.

---

### Post by MDM72 on 2016-09-05
Dennis,

Ubuntu offers that option, and that's what I referring to.

Did you try running their instructions on a Windows computer? gpg does not come preinstalled and preconfigured on Windows, so no, it is not easy to do.

---

### Post by Dennis N on 2016-09-05
No, only with Linux Mint. I didn't realize Ubuntu had an option for verifying the sums. Thanks. Next time I install from Ubuntu, I will look for it.

---

### Post by ajgreeny on 2016-09-05
Just in case you are unaware of this, download the .iso image file with a torrent client and you don't need to bother with checking md5sum or sha256sum as the torrent checks as it downloads and if any packet from the total that is corrupt is deleted and downloaded again.

If you still want to check the files you have downloaded all the info is at [https://help.ubuntu.com/community/UbuntuHashes](https://help.ubuntu.com/community/UbuntuHashes)

---

### Post by oldos2er on 2016-09-06
> **MDM72 said:**
> I think an ideal solution would be to put these small files in an https portion of ubuntu.com so that I could easily be sure that my copy of Ubuntu is secure.

I would consider filing a bug about this; it does seem like simple common sense to host the checksums on a secure server.

---

