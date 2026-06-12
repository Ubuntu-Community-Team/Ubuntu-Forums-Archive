---
title: "Live CD for 11.04 doesn't work"
date: 2011-08-28
forum: Installation &amp; Upgrades
---

### Post by Sugoi48 on 2011-08-28
I swear I followed the instructions character for character. The CD calls itself "Ubuntu 11.04 amd" and has 19 files/folders visible upon opening.

When I try to boot from the CD, I get to the deep purple screen with the the <symbol?>=<person> thing at the bottom, followed by a black screen with a flashing underscore in the top left corner. It stays like this indefinitely. What am I doing wrong?

Thank you

---

### Post by saltmarshlamb on 2011-08-28
Did you check that the downloaded iso was good before you burnt it? Did you check the integrity of the burnt cd?

[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)
[https://help.ubuntu.com/community/UbuntuHashes](https://help.ubuntu.com/community/UbuntuHashes)

[https://help.ubuntu.com/community/Installation/CDIntegrityCheck](https://help.ubuntu.com/community/Installation/CDIntegrityCheck)

You might need to use some boot options - [https://help.ubuntu.com/community/LiveCDBootOptions](https://help.ubuntu.com/community/LiveCDBootOptions)

Does the machine have sufficient specs to boot the livecd?

---

### Post by YesWeCan on 2011-08-28
When you see the purple screen with bizarre icons at the bottom (who's idiotic idea were these icons?) press a key, this should give you a menu.
Select check disc for errors to make sure the CD is recorded ok.
Try F6 nomodeset option

---

### Post by Sugoi48 on 2011-08-28
Thanks, but...
The checksum matched
7de611b50c283c1755b4007a4feb0379
When I tried to check the disk integrity, I got the black screen with the underscore. Same for the try and install options.
Any other ideas? Thank you

---

### Post by YesWeCan on 2011-08-28
> **Sugoi48 said:**
> When I tried to check the disk integrity, I got the black screen with the underscore. Same for the try and install options.
Any other ideas? Thank you
Burn a new CD.

---

