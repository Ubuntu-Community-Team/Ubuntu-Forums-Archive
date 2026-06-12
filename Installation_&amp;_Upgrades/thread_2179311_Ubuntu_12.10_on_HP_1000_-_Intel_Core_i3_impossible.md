---
title: "Ubuntu 12.10 on HP 1000 - Intel Core i3 impossible"
date: 2013-10-07
forum: Installation &amp; Upgrades
---

### Post by rocha.br on 2013-10-07
Hi guys!

I've been unsuccessfully trying to install Ubuntu 12.10 on my HP 1000 - Intel Core i3. This notebook already has Ubuntu 9.04 on it, running fairly well. I have already set the Bios for booting Ubuntu 12.10 from CD/DVD rom, however it won't install. Here is what I'm doing:

- Insert Ubuntu DVD
- Restart the computer, hitting F10 for boot options and choosing boot from DVD rom
- The splash screen for instalation appears with "language options"
- After choosing the language option, I get the "Installation options" screen (Run Ubuntu without installing; install Ubuntu and the other choices)
- Choosing any of the options, the prompt start blinking on the screen for a few seconds, the DVD rom starts spinning but then the screen becomes dark, with no information at all for proceeding with the installation and nothing else happens after this. 

What can be happening? How can I solve this? Is there a way to install Ubuntu 12.10 using the terminal? 

Thank you for the help! 

Luciana

---

### Post by Bucky Ball on 2013-10-07
At that options screen after you select a language and you have the option to install, try, etc., don't select anything. Instead, hit F6. Choose 'nomodset'. Continue. Did that work? ;)

PS: You'd be better off starting with 12.04 LTS (long-term support) as it is supported until April 2017 and very stable. Support for 12.10 will run out soon.

---

### Post by sanderj on 2013-10-07
On top of what BuckyBall says: your laptop is new enough to boot from USB stick. So if the CD + workaround doesn't work, use UNETBOOTIN to write Ubuntu 12.04 LTS to a USB stick and boot from that.

HTH

---

### Post by rocha.br on 2013-10-08
Hi guys, yes, it worked. Not right away, but after a few trials I managed to get it running smoothly :) 

As for booting from USB stick, I couldn't make it work, so after dozens of trials I gave up and bought the DVD. 

Thank you for your help!

---

