---
title: "Preparing for 18.04"
date: 2018-03-25
forum: Installation &amp; Upgrades
---

### Post by derek_stewart2 on 2018-03-25
I'm currently running 16.04 on a dual-boot UEFI laptop with Windows 8.1. I shrank the C partition on Windows and installed Ubuntu in the free space. I'm looking to remove Windows altogether from the laptop and install 18.04 as the sole OS (once it's available.) Am I right in assuming when I come to do the install that the entire hard disk will be claimed when I opt for "Erase everything and install Ubuntu." I've read through the UEFI Wiki, but I'm a bit paranoid that I've overlooked something.

---

### Post by RobGoss on 2018-03-25
I can't see any reason why it would not use the entire disk if you choose this option at installation

---

### Post by oldrocker99 on 2018-03-25
You might look up how to create a separate /home partition, which makes reinstalling a breeze. If you choose "Something Else" at the what-do-you-want screen, you can repartition a smallish parittion for /, and the rest as a separate partition for /home. I use a 64GB / partition, which leaves a lot of room for the /home folder, and I've not yet run out of space in the root.

Ask away if you have trouble doing this.

---

### Post by sudodus on 2018-03-26
The following link may help you choose, if you want to participate in the development/testing or if you want a smooth ride,

[Ubuntu Development version / How to participate](https://askubuntu.com/questions/1018033/ubuntu-development-version-how-to-participate/1018060#1018060)

> 
...

As a matter of fact, if you want a really smooth ride, you should wait until July or August (2018 until Ubuntu 18.04.1 LTS), when the first point release is available.

My experience from previous versions with long time support, LTS, is that the first point release is debugged and polished.

---

