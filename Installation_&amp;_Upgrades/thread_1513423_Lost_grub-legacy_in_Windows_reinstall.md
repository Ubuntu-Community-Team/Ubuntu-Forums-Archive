---
title: "Lost grub-legacy in Windows reinstall"
date: 2010-06-19
forum: Installation &amp; Upgrades
---

### Post by person51090 on 2010-06-19
Hello all,

I dual-boot ubuntu 9.04 and windows 7. I recently reinstalled windows, and it wiped grub-legacy off of my MBR.

Reinstalling grub shouldn't be tough, right, especially with clear instructions? Anyway, I can't get anywhere with the official instructions here: [https://help.ubuntu.com/community/DualBoot/Grub#Ubuntu%209.10%20&%20earlier](https://help.ubuntu.com/community/DualBoot/Grub#Ubuntu%209.10%20&%20earlier)

The first issue is that the current live CD has no program "grub" in terminal. I dug up an old live cd, but I couldn't get anything with the directions:
> 4. Find where Grub is. If this gives a few different answers then you will need to find the correct one, perhaps by trial-and-error. 

find /boot/grub/stage1

That command didn't find anything, nor did some similar commands found on google.

So I'm really at a loss. What should I do?

Thoughts:
-Can I install Grub 2 on my MBR? Will that work with 9.04?
-Can I access my 9.04 install, copy files to Windows, and then just format the partition and clean install 10.04?

Thanks for the help! I'm somewhere between noob and novice.

---

### Post by darkod on 2010-06-19
1. To reinstall grub1 you will need liveCD with grub1 on it, in other words version 9.04 or earlier. It's best to be 9.04.

You need to run the find command only from grub> prompt. If you don't have it, something went wrong.

You should get the prompt easily by executing in terminal:

sudo grub

After that continue with the rest of the commands.

2. It will not work if you simply install grub2 to the MBR. It needs to be installed also in your ubuntu installation and have its config files there. So, you can't simply do that and expect it to work.

3. Yes, you can access your 9.04 partition from the live mode, copy anything you need, and install 10.04 over the 9.04.

Have in mind that ubuntu doesn't simply use the same partition unless you specifically tell it to using manual partitioning in the installer. If you use any of the guided methods it will simply create parallel installation dividing up your hdd even further.

If you need instructions for that, just ask.

---

