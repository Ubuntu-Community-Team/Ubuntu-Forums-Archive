---
title: "Is it possible to install Lubuntu 18.10 via terminal?"
date: 2018-10-25
forum: Installation &amp; Upgrades
---

### Post by thatrandomguy+ on 2018-10-25
Hello,

I've been given the impression that creating a LUKS encrypted LVM setup utilizing the Calamares GUI installer is currently not possible. This may or may not have something to do with UEFI-enabled systems having a conflict but don't quote me on that.

I finally managed to install Lubuntu with LVM setup yesterday with the installer but it's not encrypted.

I am now wondering if there's a way to do this all from the terminal since the calamares installer won't cooperate.

Any clues? :?

---

### Post by TheFu on 2018-10-25
Did you see [https://ubuntuforums.org/showthread.php?t=2399092&highlight=paddy+cryptsetup](https://ubuntuforums.org/showthread.php?t=2399092&highlight=paddy+cryptsetup) ?

---

### Post by thatrandomguy+ on 2018-10-25
@TheFu
I spent an hour working on this. That solution doesn't work with Lubuntu 18.10 as the Calamares installer is used instead of Ubiquity. The method involved in that tutorial seems to require it, but I tested it anyway.

Since Calamares doesn't come with the same options as Ubiquity, I had to BS some steps because the installers are distinct. As one would expect, the install failed. I tried it twice playing around with the options and tried to map things as closely as I could to what it was asking for. Ultimately, there's no compatibility with it.

I then thought I could simply encrypt the root partition and then later encrypt home and swap with ecryptfs but when that install booted, grub didn't load properly and I was presented with a terminal.

I'm assuming that has something to do with that bug I've been told conflicts with LUKS on EFI machines. :?

For the moment, I have no choice but to take a break. Nothing seems to be working.

---

