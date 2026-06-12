---
title: "Where is MD5 checksums?"
date: 2007-10-21
forum: Installation &amp; Upgrades
---

### Post by dvh on 2007-10-21
Why can't be md5 checksums of currently downloaded CD on the same webpage as a download link for Ubuntu 7.10 cd?

---

### Post by Sef on 2007-10-21
[MD5sums page]("http://releases.ubuntu.com/7.10/")


MD5sums:

> ebf7ad055bc39634065daa10de980d7e *ubuntu-7.10-alternate-amd64.iso
9a4ae3cfd68911a861d094ec834c9b48 *ubuntu-7.10-alternate-i386.iso
61c87943a92bc7bf519da4e2555d6e86 *ubuntu-7.10-desktop-amd64.iso
d2334dbba7313e9abc8c7c072d2af09c *ubuntu-7.10-desktop-i386.iso
43ff753b260729b12c7d21d3a6db8c73 *ubuntu-7.10-server-amd64.iso
7d88cd87df509a740d9f47b9bbf1375e *ubuntu-7.10-server-i386.iso
5308a79f5e652edba5be84644ee14b09 *ubuntu-7.10-server-sparc.iso


---

### Post by logos34 on 2007-10-21
> **dvh said:**
> Why can't be md5 checksums of currently downloaded CD on the same webpage as a download link for Ubuntu 7.10 cd?

You've got a point. I agree. When you go to the [main download page]("http://www.ubuntu.com/getubuntu/downloading?release=desktop-newest&arch=i386&mirror=http%3A%2F%2Fmirror.fslutd.org%2Flinux%2Fdistributions%2Fubuntu%2Frelease%2Fcd%2F&debug=%5B%27country_US%27%2C+%27country_UK%27%2C+%27continent_NA%27%5D&download-button=") why don't they put the md5sum right under the desktop iso link???  Instead of making you dig for it?

---

### Post by Eoghanalbar on 2007-10-27
> **logos34 said:**
> You've got a point. I agree. When you go to the [main download page]("http://www.ubuntu.com/getubuntu/downloading?release=desktop-newest&arch=i386&mirror=http%3A%2F%2Fmirror.fslutd.org%2Flinux%2Fdistributions%2Fubuntu%2Frelease%2Fcd%2F&debug=%5B%27country_US%27%2C+%27country_UK%27%2C+%27continent_NA%27%5D&download-button=") why don't they put the md5sum right under the desktop iso link???  Instead of making you dig for it?

Well, it links to "Learn how to verify that your CD download ok: https://help.ubuntu.com/community/HowToMD5SUM", which eventual links to "[Ubuntu Hashes]("https://help.ubuntu.com/community/UbuntuHashes")".

Obviously, I didn't notice that in the first place myself, otherwise I wouldn't have done the google search that got me to this thread. :P

---

### Post by MQMike on 2007-10-27
Makes sense to keep the MD5 sum separate from the Ubuntu file—for security reasons.  If one is corrupted maliciously, there’s a good chance the other will be messed with also if the two are together.

---

