---
title: "Trouble with Trusty 14.04.1 Checksums"
date: 2014-08-04
forum: Installation &amp; Upgrades
---

### Post by BlueAZ on 2014-08-04
Hello,   I've downloaded the iso for Trusty twice now, but I can't get the right hash.  This is for installing on my netbook, a Toshiba, if that matters.  The first download was on that netbook.  I used the Ubuntu boot-disk creator to load to USB, but it wouldn't work.

So I downloaded it again on my desktop.  What I got was ubuntu-14.04.1-desktop-i386.iso .   This time I decided to check the hash.  Using md5sum from the Terminal, I get a hash of:   a4fc15313ef2a516bfbf83ce44281535  for this iso.  But that doesn't match any of the hashes listed online for Ubuntu 14.04 or 14.04.1 or any other release.  Since I'm downloading from Ubuntu sources, why isn't the hash matching, and what can I do?

Thanks,   Blue

---

### Post by papibe on 2014-08-04
Hi BlueAZ.

According to [this]("http://releases.ubuntu.com/14.04.1/MD5SUMS") (found from [here]("http://releases.ubuntu.com/")), you have the right hash for the 32bit desktop.

Let us know how it goes.
Regards.

---

### Post by BlueAZ on 2014-08-06
Thank you so much!  I had looked at:  [https://help.ubuntu.com/community/UbuntuHashes](https://help.ubuntu.com/community/UbuntuHashes)  which didn't have the 14.04.1 hash.  Someone should update that.
I had also gone to  [https://help.ubuntu.com/community/UbuntuHashes](https://help.ubuntu.com/community/UbuntuHashes)   but couldn't figure out how to find the hashes...  Guidance on the site would be helpful.
Will go for install now!
Thanks again!!

---

