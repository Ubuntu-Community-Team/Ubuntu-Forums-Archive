---
title: "Windows Boot Loader and GRUB2 on Partitions"
date: 2010-08-20
forum: Installation &amp; Upgrades
---

### Post by Dylnuge on 2010-08-20
Hi,

I'm experiencing the problem described here: [https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/441941](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/441941) (where loading into Windows corrupts the MBR). None of the solutions in the bug thread work for me, however--I'm on a Dell system (so it's not HP tools) and I'm not running PC Angel or any similar service (I checked). I assume it is related to the Dell recovery partition, though my old laptop from Dell didn't have this problem even though it also had a recovery partition.

However, before I had partitioned and set up Ubuntu on my new laptop, I installed Wubi (for transferring over the files from my old laptop because I didn't have time to do a full install and deal with problems like this one). Wubi worked fine using the Windows Boot Loader. I understand that WBL isn't capable of loading Linux on its own, which is why I was wondering if it was possible to have GRUB installed on a separate boot partition (not the MBR) and loaded from Windows Boot Loader. All of the information I could find on it didn't work with Windows 7--but again, I know Wubi was capable of doing it. Does anyone know how to set this configuration up?

Thanks in advance,
Dylan

---

### Post by kansasnoob on 2010-08-20
I personally prefer option #2 here:

[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Windows_Writes_To_MBR](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Windows_Writes_To_MBR)

I wrote a more detailed HowTo about reverting to legacy grub here:

[http://ubuntuforums.org/showthread.php?t=1298932](http://ubuntuforums.org/showthread.php?t=1298932)

I believe it is possible to use Easy BCD 2.0 to boot with grub2 installed to Ubuntu's PBR but I've never done it. This may be helpful if you choose to go that route:

[http://neosmart.net/forums/showthread.php?t=4953](http://neosmart.net/forums/showthread.php?t=4953)

If you're running Ubuntu 10.04.1, installing grub2 to the Ubuntu partition rather than the mbr of a drive should be as simple as running the command:

```
sudo dpkg-reconfigure grub-pc
```

You'll first see debconf windows for "command line" and "default command line", you can normally just accept the defaults for both unless you've had to add any special boot parameters. (Just press the Tab key and the cursor will move to OK).

Next you'll see a warning, in part:

> Note: It is possible to install GRUB to partition boot records as well, and some appropriate partitions are offered here.  However, this forces GRUB to use the blocklist mechanism, which makes it less reliable, and therefore is not recommended.

Here again just "Tab" to "OK" and you should see a box similar to this:

[ATTACH]167031[/ATTACH]

There you can see I'm offered the options of my Ubuntu root "/" partition along with the MBR of each drive. (You can use the Space bar to select or deselect devices).

Note: Prior to 10.04.1 you'd be offered ALL devices and installing grub-pc to the PBR of Windows partitions was generally disastrous!

I hope this is helpful.

---

### Post by Dylnuge on 2010-08-20
Thank you very much for the detailed response!

I think I'll revert to GRUB legacy, as I'm familiar with it and not overly concerned with the advances in GRUB 2. Thanks again for the help!

---

