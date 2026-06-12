---
title: "Installation apparently.. &quot;hides&quot; my other operating system."
date: 2007-06-17
forum: Installation &amp; Upgrades
---

### Post by Blake990 on 2007-06-17
When I try to install Feisty Fawn, the installation goes smoothly.  No hassles.
Except for the fact that I can no longer get back to Windows unless I remove Ubuntu.


I'd install Ubuntu onto my 19 GB hard drive, and that would go fine.  It's installed specifically on that HD, and nothing anywhere else.  When I try to reboot the computer, it boots up on ubuntu, which is fine; but when I want to boot up on Windows XP, I get a DOS error that states that Windows cannot be found.  So I go into Ubuntu, look at the other hard drive files, and I see that they're all there.  Including the Windows folder.

So.. I mean.. How would I go about fixing this?
I really want to use Ubuntu, but I'd also like to use Windows as a gaming platform, but apparently it won't let me.
I don't want to keep having to reinstall Windows, and having to call Microsoft and have to get my key activated by foreign people who don't even understand me...over and over...

Please help me.

---

### Post by ryanVickers on 2007-06-17
Look in the file /boot/grub/menu.lst and see if what it's using to boot windows (the partition number) is correct.  If it's the first partition, then 0, if it's the second, then 1, etc.

---

