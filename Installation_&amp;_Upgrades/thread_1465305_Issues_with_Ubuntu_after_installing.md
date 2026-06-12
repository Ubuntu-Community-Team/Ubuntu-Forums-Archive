---
title: "Issues with Ubuntu after installing"
date: 2010-04-29
forum: Installation &amp; Upgrades
---

### Post by dmata82 on 2010-04-29
Good morning,

I just installed Ubuntu 9.10 i386 in a Toshiba Satellite L35, after completing the installation i had to restart the computer three times in order to boot properly, those times it would freeze in a black screen showing this:

[Linux-bzImage, setup=0x3400, size=0x3b26e0]
[Initrd, addr=0x149ae000, size0=57d098]


As I say before, after rebooting three times it would load Ubuntu and work properly but a little slow for me.

Then after setting up the wireless connection and start to get the feel of the new OS it froze. I restarted the laptop two more times, remember the issue two paragraphs ago, and then again it froze.

This is very frustating because i thought that ubuntu was suppoused to be more robust than windows, but it seems that this is not the case. My guess is that this is memory issue.

What would you recommend I should do?

Thank you in advance

---

### Post by PeterOakland on 2010-05-12
I have a very similar issue:
I upgraded 9.10 to 10.04.
I get this right after grub:
[Linux-bzImage, setup=0x3400, size=0x3d4860]
[Initrd, addr=0x2f7cf000, size=0x7981ec]

Then, after about 15 seconds, that goes away and a green screen flashes very quickly, and then I get the splash screen, with the logo and the white dots turning red beneath.
That doesn't last long, and then I'm in my desktop, ready to go.

This does not happen when I boot from the CD directly.

What is it all about, and is there a way to get it to stop printing the ascii?

Thanks.

---

