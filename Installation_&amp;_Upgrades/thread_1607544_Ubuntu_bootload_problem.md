---
title: "Ubuntu bootload problem"
date: 2010-10-27
forum: Installation &amp; Upgrades
---

### Post by Salmigondis on 2010-10-27
Hello,

I'm new to this forum, so I'm sorry if I seem completely stupid to you.

I've been using Ubuntu for a couple years, and have really enjoyed the experience. Recently though, I also felt like installing Arch Linux onto my laptop which already had a Vista/Ubuntu 10.04 partition. In doing so, I lost access to the Ubuntu partition on my hard drive. The Arch linux grub had replaced the Ubuntu grub.

So the main question is, does anyone know how I could re-access or re-install the original Ubuntu grub? If not, then can someone help me with adding a boot option in Arch's Grub? I've already tried some things, though obviously, none have worked sofar.

Thanks for any help.

---

### Post by mikewhatever on 2010-10-28
Here's how to reinstall grub from Ubuntu live cd
[https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202](https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202)

Boot Ubuntu after reinstalling, and if other OSs aren't detected, run **sudo update-grub** .

---

