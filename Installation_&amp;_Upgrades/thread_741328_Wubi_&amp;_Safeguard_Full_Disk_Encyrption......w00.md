---
title: "Wubi &amp; Safeguard Full Disk Encyrption......w00t"
date: 2008-03-31
forum: Installation &amp; Upgrades
---

### Post by BrandonBan6 on 2008-03-31
Ok guys,

I was excited to learn that the 8.04 beta was going to include Wubi. Upon hearing about Wubi, I thought it might be the answer to my companies requirement of Full Disk Encryption by Utimaco Safeguard. I installed Kubuntu 8.04 beta w/wubi and then rebooted. I logged into the Safeguard credential screen, then selected "Kubuntu", the Splash screen came on and then went to a black console-like screen that stated in parenthesis (initramfs). So I decrypted the hard drive (I have the fortunate access to do so), and then rebooted, and Kubuntu loaded perfectly. Re-encrypted the harddrive and the problem is back. Partitioning my harddrive is not an option as Safeguard is required and does not (at least to my knowledge) support a dual os-boot partition. Anyone have any thoughts or suggestions?

I'm fairly new to Linux and Linux commands, but I will try to keep up with the tech garble as best as I can! 

Thanks!
B

---

### Post by mrsteveman1 on 2008-03-31
I'm going to go out on a limb here because I'm not familiar with Safeguard, but their site says this:

> SafeGuard® Easy's sector-level hard drive encryption combined with secure pre-boot user authentication ensures that disk data remains encrypted and hack-proof — even if your laptop is lost or stolen! 

Basically this is all software, with a small bootloader at the start of the disk, which authenticates the user and decrypts what it needs to load the kernel for an OS like windows, and then once Windows takes over it has its own driver to do the decryption the rest of the time while the OS is running.

For this to work you definitely need a Safeguard driver for Linux, and there might not be one.

---

### Post by BrandonBan6 on 2008-03-31
Thanks Steveman, I'm afraid you are probably right about there not being one.........maybe someday! Guess I will stick to just running it at home! Thanks for help!

---

### Post by sebastjanp on 2008-04-29
> **BrandonBan6 said:**
> Thanks Steveman, I'm afraid you are probably right about there not being one.........maybe someday! Guess I will stick to just running it at home! Thanks for help!

I have the same problem but have just got an idea.
We are using Partition mode to encrypt disk partitions with SafeGuard. 
I will try to encrypt only partitions which have windows installed and left one partition decrypted. Then I'll try to install with wubi to that partition.
Problem is that I will be able to try this not before Monday 5th of May so if you can do it sooner... I'll be happy to know if its possible :)

My English is not perfect so sorry about that ;)

---

### Post by BrandonBan6 on 2008-04-29
> **sebastjanp said:**
> I have the same problem but have just got an idea.
We are using Partition mode to encrypt disk partitions with SafeGuard. 
I will try to encrypt only partitions which have windows installed and left one partition decrypted. Then I'll try to install with wubi to that partition.
Problem is that I will be able to try this not before Monday 5th of May so if you can do it sooner... I'll be happy to know if its possible :)

My English is not perfect so sorry about that ;)
Thanks sebastjanp,

It is worth a shot, I do not know how well it will operate. I actually am now trying to run linux with a VMware windows. There is an open source encryption solution out there. Let me know either way though, or at least how far you get!

---

### Post by mrsteveman1 on 2008-04-30
Same issue, once the linux kernel loads there will be no way for the kernel to read and write from the encrypted partition with the wubi install on it.

All wubi does is put linux root in a file on the windows partition, once the kernel loads its all native like normal.

---

### Post by BrandonBan6 on 2008-05-23
Thanks Steve.........I actually ended up convincing my boss to allow me to run Windows inside Linux un-encrypted for the time being. :)

---

