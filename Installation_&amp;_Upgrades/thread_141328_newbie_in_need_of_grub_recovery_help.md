---
title: "newbie in need of grub recovery help"
date: 2006-03-08
forum: Installation &amp; Upgrades
---

### Post by Mlafflin on 2006-03-08
Hello, I am trying to tri boot. PLease help me!
I am doing a paper on three different linux OS's, and for research I tried installing SUSE on a laptop (toshiba) which already had an XP partition and an ext3 with ubuntu, which I really like. Then I tried installin SUSE and right at the end it failed. The very last thng it does are four steps
-udating configuration (success)
-copy files to installed sysm(sucess)
-install boot mgr (this is where it froze)
-prep system for boot (never go there)
there were two buttons at the bottom of the page, one was cancel (not sure, it was on the bottom left)
the other was accept)
I chose accept and that was it. a message that said unsuccesful or wahatever and I was restarting the computer. when I did I never again saw my Grub loader.
I had to fix mbr after trying to fid something either on my ubunt live and regualr cd and also my suse.
I'm very new to linux and would like to finish this paper which is due in three hours. PLease help!

---

### Post by munga_bill on 2006-03-08
[https://wiki.ubuntu.com/RecoveringUbuntuAfterInstallingWindows](https://wiki.ubuntu.com/RecoveringUbuntuAfterInstallingWindows)
Just try one of these methods for restoring Grub.
Here's another way:[http://www.ubuntuforums.org/showthread.php?t=114332](http://www.ubuntuforums.org/showthread.php?t=114332)

Good luck with your paper!

---

### Post by Mlafflin on 2006-03-08
Thank you, This is an all nighter. I have complete cofidence this is gonna work. I wish I could get suse working , I think the reason it didn't work might have to do with the fact that the auto partitioning looked like it tried  using the swap partitiion  that was already there? But I'm not sure because I'm newbie

---

### Post by munga_bill on 2006-03-08
It's quite okay to share the same swap area between linux distros, the only thing you need to be careful of with that is not to use hibernation or you could lose data. Otherwise, for most people it is fine to share the swap area.
I don't know anything about Suse, doesn't Suse use Grub? It should be simple to add more operating systems if they all use Grub. Even if they don't, and you install their bootloader to their own partition, you can still configure grub or re-install Grub, and it should be able to find it and boot it. Grub can boot other bootloaders (chainload) or other operating system's kernels directly.

---

