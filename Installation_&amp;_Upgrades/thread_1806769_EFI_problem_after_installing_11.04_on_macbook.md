---
title: "EFI problem after installing 11.04 on macbook"
date: 2011-07-18
forum: Installation &amp; Upgrades
---

### Post by kasperelkjaer on 2011-07-18
Hello, 
I have a Macbook 5,2, on which I'm triple booting OS X - Linux - Windows, using bootcamp and rEFIt.

I had a variation of Ubuntu 10.04 called Uber Student as the linux installation.
I installed Ubuntu 11.04 AMD64 instead, by choosing the EFI boot option.

Now this gave me some problems. When I shot down, the Macbook gives me a troubling long beep sound.

When I start up, I'm still able to boot up into rEFIt and Grub2, but there is a big delay with the screen being black for about 30 seconds and the little white light in the left corner of the Macbook is blinking feverishly. I read something about a guy which had a similar problem and the process seemed to mess up the firmware on his Macbook, so he had to have his MB changed. I really hope this is not the case.

What is going on here? What's up with the scary beep sound and the long boot up delay?

Secondly, when I want to do an update of the Ubuntu system, the update manager asks me to do a partial upgrade, which includes removing the grub-EFI, resulting in a system that won't boot...

Has these problems been reported before? Are the any solutions for this problem?

Thanks, Kasper

---

### Post by kasperelkjaer on 2011-07-18
Here's a video of what happens when I reboot or shut down the computer.

[http://www.dailymotion.com/video/xjz32y_efi-problem-after-installing-ubuntu-11-04-on-macbook-5-2_tech](http://www.dailymotion.com/video/xjz32y_efi-problem-after-installing-ubuntu-11-04-on-macbook-5-2_tech)

---

### Post by kasperelkjaer on 2011-07-19
Okay, I solved it!

If anyone encounters the same problem, I solved it by following this guide:

[http://pubmem.wordpress.com/2011/04/09/flash-efi-firmware-update-manually-on-a-macbook-51/#comment-78](http://pubmem.wordpress.com/2011/04/09/flash-efi-firmware-update-manually-on-a-macbook-51/#comment-78)

By manually flashing the EFI firmware, the beep sound and the long startup delay is now gone and I'm still able to boot into any OS. :)

---

