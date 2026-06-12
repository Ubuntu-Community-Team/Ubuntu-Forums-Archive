---
title: "Windows 8 and GRUB"
date: 2012-10-28
forum: Installation &amp; Upgrades
---

### Post by GJ1234 on 2012-10-28
Hello everybody,

I'm currently planning to update to the newest OS from Microsoft, Windows 8.
But I do have quite a few question before I make my o so valuable laptop a piece of not-booting sh*t.
Let me first give you the situation, I used the GRUB-customizer tool to set Windows 7 as the default boot option, and when I'd feel to use Ubuntu 12.04 I could boot in that OS. (see attachment)
I was planning to upgrade to Ubuntu 12.10 but people told me it would definitely give me problems with my boot-order and GRUB.
So would this Windows 8 update which will replace my Windows 7 installation mess with GRUB and/or my boot-order?
Any help is greatly appreciated, thanks in advance!

---

### Post by darkod on 2012-10-28
Is the upgrade to 12.10 something you need or just because it's the latest? If 12.04 LTS is doing the job for you, I suggest to keep it since it's LTS and it's supported 5 years.

On the windows side, the windows installer does not offer to skip installing the bootloader so it would definitely overwrite grub2 on the MBR with the windows bootloader, making only windows bootable.

But reinstalling grub2 back to the MBR is a very easy operation using the cd in live mode. Only the cd has to be the same version of ubuntu that you are running.
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)

---

### Post by GJ1234 on 2012-10-28
> **darkod said:**
> Is the upgrade to 12.10 something you need or just because it's the latest? If 12.04 LTS is doing the job for you, I suggest to keep it since it's LTS and it's supported 5 years.

On the windows side, the windows installer does not offer to skip installing the bootloader so it would definitely overwrite grub2 on the MBR with the windows bootloader, making only windows bootable.

But reinstalling grub2 back to the MBR is a very easy operation using the cd in live mode. Only the cd has to be the same version of ubuntu that you are running.
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)

I was willing to upgrade to 12.10 because I read it was faster, which I like.
But I do not understand which CD I should use?

---

### Post by Mark Phelps on 2012-10-28
> **GJ1234 said:**
> I was willing to upgrade to 12.10 because I read it was faster, which I like.
But I do not understand which CD I should use?

As the saying goes ... your mileage may vary ... but on my PC, 12.10 runs noticeably SLOWER than 12.04 -- using the same hardware.  So, if you're upgrading only for faster performance, that may not be a really good idea.

---

