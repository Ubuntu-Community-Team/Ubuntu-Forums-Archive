---
title: "Ubuntu 9.10 will not start; at a loss!!!"
date: 2009-11-22
forum: Installation &amp; Upgrades
---

### Post by juny20 on 2009-11-22
Hello everyone,
I am at a complete loss here. I updated my laptop from 9.04 to 9.10. Installation went perfect. The system was working perfectly fine. Two days ago, when I turned the laptop on, after showing that grub was starting, the following screen came up. Nothing will respond after this screen is on. I was not able to do anything and I don't understand what this means. I search Google to no avail. I can boot using the Live CD, but I just don't know what to look for and what to fix. Attached is a picture of the screen. Any help will be greatly appreciated!!!

---

### Post by juny20 on 2009-11-23
Hello, just wondering if anyone else experienced the same problem.](*,)

---

### Post by falconindy on 2009-11-23
It's a kernel panic. Looks like either faults on the hard drive or bad memory. Can you boot the recovery kernel? Barring that, can you boot off a LiveCD and run fsck on each drive?

---

### Post by juny20 on 2009-11-23
Hi falconindy, thanks for the reply!
Yes, I can boot using the LiveCd.
I will try that and will report. The laptop is about 10 years old, so I wonder if the hard drive or the memory are going bad?

---

### Post by juny20 on 2009-11-29
I was not able to fix the problem. I had to re-install 9.10. This time, I used Ext3 instead of Ext4. So far so good. My laptop is about 10 years old. It is a IBM Thinkpad P3 512mb ram 10gig hd. I also installed LXDE as the window manager as it is lighter on system's resources. I am guessing that the Ext4 caused some of the problem? Again, it is just a guess.

---

