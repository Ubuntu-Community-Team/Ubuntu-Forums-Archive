---
title: "Problems"
date: 2008-04-21
forum: Installation &amp; Upgrades
---

### Post by Exsecrabilus on 2008-04-21
I burned a copy of Hardy RC amd64 onto a disc.

I inserted it into my disc drive (running Gutsy i396.)

It won't do anything.

Is this because the versions are different?

My computer is capable of the amd64 one, just to let you know.

So does this mean I have to make a fresh install?

---

### Post by Rocket2DMn on 2008-04-21
When you burned the disc, did you burn it as an image and not a data disc? See [https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)
You should also check the md5sum on the image file
[HowTo]("https://help.ubuntu.com/community/HowToMD5SUM")
[Hashes]("https://help.ubuntu.com/community/UbuntuHashes") to check against
Then burn the disc at a slow speed like 4x to prevent write errors, then reboot from the CD (may have to change BIOS boot order).

---

