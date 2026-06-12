---
title: "ubuntu 21.04 will not install on lenovo"
date: 2022-05-24
forum: Installation &amp; Upgrades
---

### Post by erfanyoosefian89 on 2022-05-24
Hi! I have a [Lenovo ThinkBook 15]("https://www.bhphotovideo.com/c/used/1558129?gclid=Cj0KCQjwhLKUBhDiARIsAMaTLnGd12UYBbUexlCig5e8ZeIY3TcIngT_xBsmxsSbzSovGXV8cPKbkbcaAvajEALw_wcB") which I got off of amazon a few months ago. anyway, I'm trying to dualboot win11 and ubuntu rn. It does get to the "grub screen" and will go to the fancy loading animation but just gets stuck there.. :( I'd be happy if someone was to help. Thanks!
The image below is what it gets stuck on.

---

### Post by tea for one on 2022-05-24
> ubuntu 21.04 will not install on lenovo

Ubuntu 21.04 reached End Of Life (EOL) in January 2022.
Any reason not to try Ubuntu 22.04?

---

### Post by coley9225 on 2022-05-24
Hello, I have a lenovo ideapad 320 and had an issue like that. When I installed lubuntu on my computer, I had to install the system only, NO BOOTLOADER. There is usually an option in the app menu to 'install system files', or something like that. Use that option. The installer will warn of not being able to boot system without bootloader, that's ok. It *should* install the system files and skip installing grub. When the install is complete and the option comes to restart or continue testing, CHOOSE CONTINUE TESTING.
*DO NOT REBOOT YET.*
Download and install boot-repair. Follow the on screen prompts. When boot-repair is finished, then reboot computer and you should see the grub menu. Choose ubuntu and enjoy(hopefully).

I again note that this worked for me, and may or may not work in your case. Use this solution at your own risk.

I would strongly advise you to do a full backup of you windows if you haven't already, just in case. I would also note, if you decide to install additional linux distros, skip the boot-repair. Just reboot into the working linux distro and update grub, then you should be able to reboot to the new install.

Best of luck. This issue fought me for a year before I learned of this method. Hope it works for you as well.

---

### Post by guiverc on 2022-05-24
I'll repeat what @tea for one said, Ubuntu 21.04 (*and all flavors*) are [B]*end-of-life*
[/B]
- [https://fridge.ubuntu.com/2022/01/21/ubuntu-21-04-hirsute-hippo-end-of-life-reached-on-january-20-2022/](https://fridge.ubuntu.com/2022/01/21/ubuntu-21-04-hirsute-hippo-end-of-life-reached-on-january-20-2022/)> As of January 20, 2022, Ubuntu 21.04 is no longer supported. No more  package updates will be accepted to 21.04, and it will be archived to  old-releases.ubuntu.com in the coming weeks.


    The original End of Life warning follows, with upgrade instructions:


    Ubuntu announced its 21.04 (Hirsute Hippo) release almost 9 months  ago, on April 22, 2021, and its support period is now nearing its end.  Ubuntu 21.04 will reach end of life on January 20, 2022.



I'd suggest a *supported* release such as Ubuntu 20.04 LTS from the prior *development* *cycle*, or Ubuntu 22.04 LTS being the *final* LTS for the *development cycle* 21.04 was part of.

---

