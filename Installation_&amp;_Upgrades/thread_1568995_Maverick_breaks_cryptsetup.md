---
title: "Maverick breaks cryptsetup"
date: 2010-09-06
forum: Installation &amp; Upgrades
---

### Post by SabreWolfy on 2010-09-06
I have an external USB drive encrypted with cryptsetup. The drive has no partition table -- it is encrypted as /dev/sdb. Once I created the encrypted device in Lucid, I used the following to access (mount) it (in Lucid):

sudo cryptsetup create XXX /dev/sdb
sudo mount /dev/mapper/XXX /media/YYY

This no longer works in Maverick Beta. The first command prompts me for the password, but the second one throws an error about the incorrect filesystem (which presumably means that mount cannot recognize what is at /dev/mapper/XXX). I cannot access my encrypted USB drive in Maverick :(

---

### Post by SabreWolfy on 2010-09-06
I think has something to do with this via dmesg:

```

[  479.983093] padlock: VIA PadLock not detected.
[  480.056973] padlock: VIA PadLock Hash Engine not detected.

```

Don't have time to go down this rabbit hole. Downgrading back to Lucid.

Bug report [here]("https://bugs.launchpad.net/ubuntu/+source/cryptsetup/+bug/631425") FWIW.

---

### Post by SabreWolfy on 2010-09-06
Solved. See comment #2 in the bug report [here]("https://bugs.launchpad.net/ubuntu/+source/cryptsetup/+bug/631425/comments/2").

(Basically, just do what it says [here]("http://code.google.com/p/cryptsetup/wiki/FrequentlyAskedQuestions#7._Issues_with_Specific_Versions_of_cryptsetup")).

---

