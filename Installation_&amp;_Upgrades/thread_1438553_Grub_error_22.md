---
title: "Grub error 22"
date: 2010-03-25
forum: Installation &amp; Upgrades
---

### Post by RadioactiveFallout on 2010-03-25
So, I looked around for a while to try find an answer to this problem, and my case seems a bit unique.

I purchased a new computer, and after about 2 months of use decided I needed something off the hard-drive of my obsolete PC. I took it out of my old PC, along with it's IDE cable. I had installed Ubuntu on another hard-drive contained within my old PC, which has since failed. I am left with one hard-drive with Windows 7, which is bootable, one failed hard-drive and an old IDE hard-drive with Windows XP. When attempting to boot Windows XP, I get Grub error 22. Downloading a Ubuntu distro is not an option at current, but may be soon. How can I boot Windows XP? I only have a Windows 7 bootdisk. Within "6-10", which will be more like 20+ with an international mail redirection, I will have the latest Ubuntu. 
How can I boot Windows?

---

### Post by dstew on 2010-03-25
It seems that your XP hard drive has the Grub boot loader in its MBR, and grub stage 1.5 in its boot sector. Does it say "grub stage 1.5" before it gives you the error? Anyway, it won't boot because it can't find its stage 2 file, which is probably on the Ubuntu disk.

Regarding booting XP, there are two problems. First, you need some functional boot loader. If you can get the Windows 7 boot loader to boot XP,  that might be enough. I don't know anything about Windows 7, so you would have to look that up. You will need to change your BIOS settings so the Windows 7 disk boots before the XP disk.

But the other problem with XP is that, unlike Ubuntu, it is installed with specific drivers for a specific hardware system. It might not boot in your new computer because it doesn't have the basic drivers for your new hardware. Ubuntu, on the other hand, will look at a system, and load the appropriate drivers. You can take an Ubuntu hard drive out of one computer, and put it in another, and it will usually boot. XP will usually not boot.

If you only want some files off of the old disk, can't you just copy them over into your Windows 7 system? Why do you need to boot XP?

---

### Post by RadioactiveFallout on 2010-03-27
Yes, it says "Grub stage 1.5", then gives "Error 22"
I tried using my W7 disc to replace the MBR on the XP HDD, but that didn't work.
I have the files that I need, however a few programs of mine don't run on W7, so I would like to boot XP and run them.

---

### Post by dstew on 2010-03-27
You also have to change the boot order in BIOS so the XP disk boots before the Windows 7 disk. And, you might need to do fixboot in addition to fixmbr. Still, XP will probably not run on a different system for the reasons I put in my last post. But, these are all Windows issues, and I don't know very much about these things. You might try a Windows forum.

---

### Post by RadioactiveFallout on 2010-03-27
Alright. Thanks anyway.

---

