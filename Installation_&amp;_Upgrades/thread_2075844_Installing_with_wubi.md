---
title: "Installing with wubi"
date: 2012-10-24
forum: Installation &amp; Upgrades
---

### Post by deepak7 on 2012-10-24
Hi,
  I am total newbie to linux and like to try ubuntu 12.04 LTS.I once messed up with installation and corrupted my windows partition.So i decided to install ubuntu inside windows using wubi.
I heard somewhere that 12.04 doesnt support installing inside windows.Is dat true? If it is,I don't mind trying another version of ubuntu!! 

One more question!! 
Where to install ubuntu? one my windows drive or another drive?:confused:

THanks in advance!

---

### Post by Pilot6 on 2012-10-24
12.04 can be installed using wubi. If you use wubi it does not matter on which partition you install it. This matters only for real install.

---

### Post by Karlchen on 2012-10-24
Hello, deepak7.

Ubuntu 12.04.1 does support Wubi installations. Both the 32-bit and the 64-bit editions do. ([SIZE=1]Have installed both editions through Wubi successfully.[/SIZE])

_About the question which drive to use for the Wubi installation:_

Well, in the end it is your decision.

Personally, I prefer putting the Wubi installation on a non-system disk. I.e. if my machine has got drives C: and D:, C: being the Windows system drive, D: being a data drive, then I will prefer installing Ubuntu on drive D:.

The reason is that this host drive where Ubuntu lives will be easily accessible from inside Ubuntu by going to the mount point /host. As this gives access to the complete drive, it simply makes me feel better if the Windows operating system is on another drive.

But as stated earlier:
It is your decision. Use the drive which suits you best and which holds an NTFS filesystem. FAT32 will not be good enough.

Kind regards,
Karl
--
P.S.:
You may find the official **[Wubi Guide]("https://wiki.ubuntu.com/WubiGuide")** helpful.

---

### Post by FadeToBen on 2012-10-24
> **deepak7 said:**
> Hi,
  I am total newbie to linux and like to try ubuntu 12.04 LTS.I once messed up with installation and corrupted my windows partition.So i decided to install ubuntu inside windows using wubi.
I heard somewhere that 12.04 doesnt support installing inside windows.Is dat true? If it is,I don't mind trying another version of ubuntu!! 

One more question!! 
Where to install ubuntu? one my windows drive or another drive?:confused:

THanks in advance!

So the Wubi installer is very cool for the simple fact that you can dual boot without having to assign the install to a different partition. I used the Wubi installation while i was getting used to Ubuntu and I emplore everyone to try it out! The best part is that if you find that Ubuntu isn't your cup of tea, you can just install it from  add/remove programs in Windows. You should be able to install on the partition you boot from, and I tried 12.04 through Wubi and it worked fine for me!

---

### Post by deepak7 on 2012-10-24
Ok thank you for the quick replies...surely install ubuntu ASAP!

I heard installing ubuntu using wubi will have performance issues! is dat true!!

---

