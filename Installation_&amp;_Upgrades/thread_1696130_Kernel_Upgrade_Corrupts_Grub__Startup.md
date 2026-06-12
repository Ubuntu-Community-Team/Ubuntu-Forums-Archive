---
title: "Kernel Upgrade Corrupts Grub / Startup"
date: 2011-02-26
forum: Installation &amp; Upgrades
---

### Post by GutsyVirgin on 2011-02-26
*My Linux skill level is still fairly novice even after 3+ years of dual booting Ubuntu & Windows.*

I get this problem with Maverick Meerkat (10.10) every time I try to update from the kernel from 2.6.35-22-generic to the 2.6.35-25-generic. It's driving me freaking batty!

[INDENT]_The Problem_:
Whenever I update the kernel, it somehow corrupts my grub2 in that when I reboot, my Windows bootloader no longer shows up (not the real issue) and it boots me into this weird shell (no gui whatsoever) where it asks me to login to my account. After I login, it's just like working in the terminal but without a gui. What's weird is that I'm stuck in this mode for about 2 mins at which point it decides to go ahead and boot into the Ubuntu gui environment (I don't know the shell command for loading the gui, not that it matters).

So anyway, I've finally got somewhat used to how Grub2 works and **created** the **"11_Windows" file in the grub.d folder** and try to run **update-grub** but it **locks up at** the first step ("**Generating grub.cfg ...**"). I think if I were simply able to run this ONE FREAKING COMMAND all my problems and weirdness would go away. Problem is I don't know how to fix my apparently corrupted grub or update-grub command, whatever the root problem may be.[/INDENT]

Any of you smart fellows have a good idea as to what my problem is and how to fix it? Have I done well at assessing my problem? I'm doing my best to learn, but Linux is really a completely different (better?) environment than Windows, lol.

Cheers! ;)

---

