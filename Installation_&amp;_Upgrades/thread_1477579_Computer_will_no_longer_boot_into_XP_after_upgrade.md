---
title: "Computer will no longer boot into XP after upgrade"
date: 2010-05-08
forum: Installation &amp; Upgrades
---

### Post by dizzykittystudios on 2010-05-08
Hi all, my knowledge of how Linux works is very limited.  I've used it for about a year, but just doing very basic tasks (browsing the internet, listening to music, etc).

Anyway, I upgraded to the newest edition of Ubuntu and installed the new Grub as the update seemed to recommend installing it to every partition and hard drive.  I've seen that other people are now having issues from doing that as well.

I am able to boot into Linux just fine; it is working great.  However, when I attempted to load Windows XP from Grub, the computer would just restart.  I followed the recommendation listed here: [http://ubuntu-ky.ubuntuforums.org/showpost.php?p=8930595&postcount=3](http://ubuntu-ky.ubuntuforums.org/showpost.php?p=8930595&postcount=3) which seemed to fix the problem for Windows 7 users.  Now, all I get when I attempt to load XP is a blank screen with nothing but a blinking cursor (but hey, at least the computer isn't just automatically re-booting, that's some sort of progress...maybe...)

If the problem has already been solved else where, please direct me to that post.  I did a search and couldn't find anything that seemed to address this specifically.

Thank you for all of your help.

---

### Post by dizzykittystudios on 2010-05-08
Just an update...

I attempted a "fix" that I found on another website which suggested using my Windows XP disk and running fixmbr.  I did so and that completely screwed things up.  Now, when my computer boots, after is passes the BIOS screen, it's just blank.  So, now the computer is completely useless and I hope that I can at least salvage the data on it.

I could definitely use some help.  Anyone...

---

### Post by bcbc on 2010-05-09
Hi, you can boot off an ubuntu install cd and mount your disk to recover data.

When you ran fixmbr you installed the windows bootloader to your drive. That boots the partition marked with the boot flag (windows). Basically, you're getting the same result now as you got when you selected to boot windows from the grub menu, but now you don't have the option to boot ubuntu.

You can reinstall the grub2 bootloader and that at least will allow you to boot ubuntu: [http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)

You should try the fixboot command from the windows xp disk to fix the bootsector, rather than fixmbr. It's worth a shot...  however I've seen a few cases where nothing seemed to get the job down.

---

### Post by dizzykittystudios on 2010-05-09
Thank you bcbc!  Running fixboot made it so I can now boot into WinXP.  I guess it erased GRUB, which is fine by me since that is probably a lot easier to reinstall than attempting to start all over again.

If I do, by chance, decide to use Linux again, how would I install GRUB?  And should I install it only to the partition that has Linux?

*edit*
I just re-read your post and realized that you pasted a link for installing GRUB.  Thanks again for your help.

---

### Post by bcbc on 2010-05-09
> **dizzykittystudios said:**
> Thank you bcbc!  Running fixboot made it so I can now boot into WinXP.  I guess it erased GRUB, which is fine by me since that is probably a lot easier to reinstall than attempting to start all over again.

If I do, by chance, decide to use Linux again, how would I install GRUB?  And should I install it only to the partition that has Linux?

*edit*
I just re-read your post and realized that you pasted a link for installing GRUB.  Thanks again for your help.
Oh that's great! You're welcome :)

---

