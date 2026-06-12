---
title: "Doesn't even boot!"
date: 2006-06-02
forum: Installation &amp; Upgrades
---

### Post by Landser on 2006-06-02
Hello,

I am having problems while trying to boot from the desktop CD, in breezy it used
to boot successfully if I add "acpi=off" to the boot command line....

But now, if I run it normally (without turning off acpi) it just restarts the machine! And even if I use "acpi=off" then it just freezes at "Configuring some drivers" in the boot screen

I have an HP machine with an MSI-6557 (Gamila) motherboard, an ATI Radeon 9250 and 512 MB ram.

Can someone please help me?.. This is so frustrating, Breezy used to work fine and now Dapper doesn't even boot! They surely broke something with this release

---

### Post by catlett on 2006-06-02
For a "work around". You can boot to the breezy cd and then run sudo apt-get dist-upgrade. You will be prompted about dapper and given an option to update breezy or upgrade to dapper.

P.S. This is asssuming you are trying to install. If you are just trying to run the live session, try downloading the latest version (if you haven't already. hopefully it will have better results)

---

### Post by byen on 2006-06-02
Please see [this thread]("http://www.ubuntuforums.org/showthread.php?t=140981") as I think it might help... if not let us know! Goodluck

---

