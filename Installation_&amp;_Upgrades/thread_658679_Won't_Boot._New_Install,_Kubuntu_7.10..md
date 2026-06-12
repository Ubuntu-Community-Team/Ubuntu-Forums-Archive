---
title: "Won't Boot. New Install, Kubuntu 7.10."
date: 2008-01-04
forum: Installation &amp; Upgrades
---

### Post by Monster_user on 2008-01-04
I just reinstalled Kubuntu 7.10, and now it freezes at the loading screen. The blue bar does not move.

Help?

**[Solved]**
*See below.*

---

### Post by PmDematagoda on 2008-01-04
Can you boot Kubuntu in Recovery Mode?

---

### Post by Monster_user on 2008-01-04
I don't know.

Unfortunately, I am using another distribution's LILO boot loader, and I have to add Kubuntu in manually.

After letting it sit for a while, Kuibuntu did boot into the initramfs BASH prompt.

---

### Post by Monster_user on 2008-01-04
Nope. It won't boot into the Recovery Mode.

It is hanging up on the following message.

> [ 30.664121] ide0: I/O resource 0x3F6-0x3F6 not free.
 [30.664175] hda: ERROR, PORTS ALREADY IN USE
[ 30.731980] ide1: I/O resource 0x376-0x376 not free.
[ 30.732038] ide1: ports already in use, skipping probe.


I have one 160gb HDD, and a DVD-RW drive.

After about a minute, it loads Busybox, that initramfs Bash prompt.

Odd... It says this issue was fixed in Dapper,...
[https://launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/76872](https://launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/76872)

Looks like its back to 6.10.

---

### Post by Monster_user on 2008-01-06
PmDematagoda, thank you for trying to help.

I've figured out what the problem was. The Kubuntu install CD detected my partitions in the wrong order. It labeled my root partition as hda8, when it was the 6th partition (hda6).

I manually edited fstab to correct the problem, and all was well. Having multiple distributions installed at one time, does come in handy.

Now to get Ndiswrapper reinstalled...

---

