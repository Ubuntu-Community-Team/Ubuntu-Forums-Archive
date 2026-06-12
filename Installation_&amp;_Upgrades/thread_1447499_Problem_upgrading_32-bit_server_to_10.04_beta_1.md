---
title: "Problem upgrading 32-bit server to 10.04 beta 1"
date: 2010-04-05
forum: Installation &amp; Upgrades
---

### Post by rickwookie on 2010-04-05
I thought I'd give 10.04 a try since it's an LTS release and I was still using Jaunty.
I did the upgrade over SSH using sudo*do-release-upgrade*-d and at first it just upgraded me to Karmic. After the reboot I ran the same command again and it looked like it was upgrading this time to Lucid.
Now however after the reboot I no longer could log in (no SSH) and after inspecting the system locally by digging out and old monitor and keyboard, it seams the system hangs during boot.

I went into the Grub menu and found that there is no server kernel listed (apart from the old Jaunty one), only generic-pae and generic. None of these will boot, and if I try the recovery modes the keyboard doesn't function when I get to the recovery menu. Also if I boot the old 2.6.28-17-server, it does boot, but the keyboard also won't function once it boots. I can SSH in once the old kernel has booted, but when I tried to install linux-image-2.6.32-19-server via apt, it can't be found. Furher investigation online sems to indicate that there's only a 64-bit server package and no 32-bit package.

What's that all about, is 32-bit no longer supported on the server platfom, and if so is my install now screwed?

---

### Post by Mark Phelps on 2010-04-05
Since 10.04 is still in beta testing, you'd probably get faster and better responses if you posted your question in the beta testing forum: Development & Programming, Lucid Lynx Testing.

---

