---
title: "&quot;Invalid Format&quot; when trying to boot Ubuntu"
date: 2010-06-27
forum: Installation &amp; Upgrades
---

### Post by jenokawa on 2010-06-27
(Before I start, can I just say that I've joined these forums to ask this question, and I don't really know where to post this  -  sorry if i've put my question in the wrong section of the forum or something :S)

I've been looking into trying out ubuntu, having heard good things about it online, so I went to [http://wubi-installer.org/](http://wubi-installer.org/) to try it out by dual-booting it alongside windows xp. I installed ubuntu, rebooted my pc and selected 'Ubuntu' at the boot menu, but after [this screen]("http://humphreybc.files.wordpress.com/2010/03/boot1.png"), the monitor goes black and my TV displays the bouncing message of 'Invalid Format'.

I've tried booting in safe graphics mode, which unfortunately didn't solve anything (or maybe I did it wrong). When looking online I've seen it seems to happen to lots of people with monitors like mine that can show TV and DVD as well as pc. 

I'd appreciate any help, I'm reasonably tech-savvy but I've never tried Ubuntu before.

---

### Post by Chame_Wizard on 2010-06-27
I read that WUBI is giving problems,if Ubuntu is installed INSIDE Winblows.

---

### Post by darkod on 2010-06-27
First, wubi is not a dual boot along side XP, it will be inside XP.

This is mostly due to video driver. What you can try is after selecting Ubuntu in the windows bootloader, when you see the grub2 menu after that, highlight the ubuntu entry but don't hit Enter. Hit 'e' instead.

When the boot lines show, use the arrows keys and End to go to the end of the line starting with linux. At the end add nomodeset. Press Ctrl + X to try and boot.

If that works, there is a way to make it a permanent fix, the above method is only temporary.

---

### Post by jenokawa on 2010-06-27
Thanks for replying!

Sorry,darkod, but I'm not sure what the grub2 menu is. I've never tried anything other than windows until now, so I'm new to booting anything else. I'll try what you say, though, and see how far I can get.

thanks again!

---

### Post by darkod on 2010-06-27
> **jenokawa said:**
> Thanks for replying!

Sorry,darkod, but I'm not sure what the grub2 menu is. I've never tried anything other than windows until now, so I'm new to booting anything else. I'll try what you say, though, and see how far I can get.

thanks again!

The grub2 menu is the second boot menu you get after selecting Ubuntu in the windows bootloader. You should get a second menu asking what you want to boot.

---

### Post by jenokawa on 2010-06-27
> **darkod said:**
> The grub2 menu is the second boot menu you get after selecting Ubuntu in the windows bootloader. You should get a second menu asking what you want to boot.

I understand, I'll go ahead and try it. Thanks for having patience with me!


EDIT: I've done as you said, and the text 'Booting a command list' appears after I finish and press Ctrl+X. It then claims that '...root.disk does not exist' and that it is 'dropping to a shell' - from then on I can only type in commands or restart. Does this mean there are more problems, or have I done something wrong? :(

---

