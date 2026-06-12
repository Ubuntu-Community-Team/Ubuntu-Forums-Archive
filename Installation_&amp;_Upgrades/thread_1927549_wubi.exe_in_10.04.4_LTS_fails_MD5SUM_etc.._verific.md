---
title: "wubi.exe in 10.04.4 LTS fails MD5SUM etc.. verification"
date: 2012-02-18
forum: Installation &amp; Upgrades
---

### Post by bentledr on 2012-02-18
wubi.exe in 10.04.4 LTS fails MD5SUM etc.. verification

It is a new build dated 07/02/12 and is different from that supplied with 10.04.3  but has been given the same MD5SUM/SHA1SUM/SHA256SUM 

I have downloaded it several times and conclude that it is OK so it would seam that the old MD5SUM/SHA1SUM/SHA256SUM has been included as it is the same as was supplied for the verification of wubi.exe in the 10.04.3 release.

Therefore the checksum files need to be updated for the 10.04.4 release to reflect the new version of wubi.exe

---

### Post by mörgæs on 2012-02-18
This is an important bug. Please open a bug report in Launchpad (if it is not already done).

---

### Post by bentledr on 2012-02-18
Also the checksums for the source DVD's contain the details for the previous release (10.04.3) presumably also in error.

---

### Post by bentledr on 2012-02-18
Bug report filed as Bug #935763

---

### Post by Daviey on 2012-02-19
Apologies for this oversight, the process involved to generate the checksums doesn't regenerate entries for files replaced with the same file name.

It should now be resolved, and normal service resume.  Thanks for discovering and reporting so promptly!

Thanks.

---

### Post by mörgæs on 2012-02-19
Thanks for being fast in solving it. 

If you have the rights, could you update this page, please?
[https://help.ubuntu.com/community/UbuntuHashes](https://help.ubuntu.com/community/UbuntuHashes)
(or should I open a new bug report for that?)

---

