---
title: "Ubuntu 7.04 does not support my 64-bit CPU?"
date: 2007-06-27
forum: Installation &amp; Upgrades
---

### Post by bartek212 on 2007-06-27
I've tried to install few versions of Ubuntu including the last one and I am always getting the same error.

Actually I've found a few topics about this problem but it seems like I am the first one here with 64-bit CPU who have this problem?

Here's a screenshot from my Windows, but, believe me, I'm having the same problem when booting from CD (of course I checked the ISO image just few minutes ago and everything is alright, anyway I've tried few images from different sources and still the same :/).

[[IMG]http://img295.imageshack.us/img295/8983/ubuntu64bitvu2.th.jpg[/IMG]](http://img295.imageshack.us/my.php?image=ubuntu64bitvu2.jpg)

Any ideas?

Thanks.

---

### Post by derjames on 2007-06-27
hey man... the problem is because your guest VM is running in a 32 bits environment... I don't think your winXP pro is the 64 bit edition...

---

### Post by Ayuthia on 2007-06-27
When you boot from the CD, is it giving you this message or is it doing something else?  What brand PC are you running and what type of video card do you have?

From your Windows snapshot, it looks like you are running a 32-bit Windows system and trying to install Ubuntu 64-bit using Virtual PC which should not work because Virtual PC is running in 32-bit mode.

---

### Post by xzero1 on 2007-06-27
Run grc's program  "securable" under windows. It will check for 64-bit compliance. See [http://www.grc.com/securable.htm]("http://www.grc.com/securable.htm")

Does your bios recognize your cpu correctly? Could there be a bios setting that turns off 64 bit?

---

### Post by bartek212 on 2007-06-27
Here's my pc's result:

[[IMG]http://img502.imageshack.us/img502/1277/athlon64x2wt8.th.jpg[/IMG]](http://img502.imageshack.us/my.php?image=athlon64x2wt8.jpg)

Guys I wrote in my first post here that I've THE SAME problem when booting from CD, I just made this screen under my Windows XP to prove that I really have 64-bit CPU. And, actually I don't know any other way to make SS from bootscreen :P

Anyone here have a X2/Athlon 64 CPU with Ubuntu installed?

I'm going to find something interesting in my bios (my motherboard is DFI NF4 Infinity - Socket 939) but I think it recognizes my CPU correctly :/

---

### Post by Ayuthia on 2007-06-27
Here is a link that has someone who just upgraded his processor to the 3800+:
[http://ubuntuforums.org/showthread.php?p=2905031](http://ubuntuforums.org/showthread.php?p=2905031)

Unfortunately, I still have not found anything that matches your issue exactly (3800+, trying Feisty, long mode issue).

---

### Post by xzero1 on 2007-06-27
I run 64 bit Ubuntu 7.04 on an athlon 64 x2 with no cpu related problems. You may want to try a different live distro that has better error reporting than Ubuntu, say Knoppix 64. If you can run 64 bit on another os, that would confirm an Ubuntu bug. Just a thought: could your cpu be overheating? Do you overclock your cpu?

---

### Post by bartek212 on 2007-06-28
Thank You guys!

xzero1 was right I've upgraded my BIOS to latest one and after that I'm able to install Ubuntu! :)

Thank You so much! Finally I've done this! :D

---

