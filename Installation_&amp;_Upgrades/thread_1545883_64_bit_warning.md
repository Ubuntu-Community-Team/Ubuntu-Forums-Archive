---
title: "64 bit warning"
date: 2010-08-04
forum: Installation &amp; Upgrades
---

### Post by jackheart on 2010-08-04
Why does it say that the 64 bit version is not recommended for daily desktop use?

I am so excited to finally have a computer of my own that if fast enough  to run things like Ubuntu.. Hope I am not asking to many  questions. I will be sure to try and document my endeavors so I may help  others.

---

### Post by howefield on 2010-08-04
See post number 62 for an attempt at explanation.

[https://bugs.launchpad.net/ubuntu-website-content/+bug/585940](https://bugs.launchpad.net/ubuntu-website-content/+bug/585940)

---

### Post by dtfinch on 2010-08-04
The warning seems outdated to me. Unless you have a very old computer, or a netbook with one of the earlier atom processors (N2xx or Z5xx), it should be fine. Some people say there are issues with Flash support, but it works fine for me, and I often do Flash development using the Flex SDK on it. I haven't had any trouble running 32bit windows apps (games) on wine either on 64 bit.

We're probably at or nearing a point where more developers are on 64 bit than 32 bit, so IMHO it won't be long before 32 bit becomes the more problematic of the two.

---

### Post by jackheart on 2010-08-04
Thanks a lot! I will re-ask this in the Studio version forum, but is there any info about compatibility/issues with the packages in the 64bit version of Ubuntu studio?

---

### Post by dabl on 2010-08-04
> **jackheart said:**
> Thanks a lot! I will re-ask this in the Studio version forum, but is there any info about compatibility/issues with the packages in the 64bit version of Ubuntu studio?

You can read the release notes, here: [https://wiki.ubuntu.com/UbuntuStudio/10.04release_notes](https://wiki.ubuntu.com/UbuntuStudio/10.04release_notes)

and here: [https://wiki.ubuntu.com/LucidLynx/ReleaseNotes](https://wiki.ubuntu.com/LucidLynx/ReleaseNotes)

I read 'em all -- there are zero "64-bit" issues.

As mentioned above, Adobe pulled their 64-bit version of flash, due to bugs that cause security vulnerabilities, but there are ways to cope with that.


FYI, there used to be a 64-bit forum here: [http://ubuntuforums.org/forumdisplay.php?f=343](http://ubuntuforums.org/forumdisplay.php?f=343)

But if you check just that first page, you will note that of 20 posts, there are exactly zero true 64-bit issues.  What you had/have is new users who have installed the 64-bit architecture, encountered their first problem or question, and immediately (and wrongly) leaped to the assumption that the issue must be related to the 64-bit architecture.  I don't blame the forum and/or Canonical for getting tired of it and just warning off newbies from even installing it. While it won't take full advantage of the underlying 64-bit hardware, including memory beyond 3.3G, the 32-bit OS will run fine on 64-bit hardware.  And generates a lot fewer "my 64-bit system won't mount a USB stick" posts, too.

---

### Post by jackheart on 2010-08-04
64 bit wont read my USB drive! forget that!

just kidding. I will cross that bridge when I get there. I am perfectly capable of reading wikis and forums, of using comand line, posting in the forums, and not blaming others for something gone awry. Isnt that the point of having opensource community based software? we have bugs, then we try to fix them.

Thanks again!

---

