---
title: "In a right state...!"
date: 2010-02-28
forum: Installation &amp; Upgrades
---

### Post by TheRealJimShady on 2010-02-28
Hi everyone,

Really grateful for some help with my installation of Ubuntu please. This is where I am and some background...

- My laptop is a little old, it's a Samsung X50.
- The CD/DVD drive is buggered
- I don't believe it is able to boot from a USB
- The native OS is Windows XP

What I did...

- While in Windows I downloaded Wubi on recommendation from a friend.
- Installed Wubi/Ubuntu on a small partition of my HD
- Installed it, and then rebooted expecting a dual boot screen. Didn't get one for some reason.
- Fooled around in Windows, and found a menu option where I could change the default operating system when booting. Changed it to Ubuntu.
- When I restarted the PC I was given options to boot one off...
   - Ubuntu
   - Ubuntu recovery
   - Acronis Secure Zone
- Using the first option, I have been using Ubuntu for a week or so and really like it. I don't want to go back to Windows, so now want to expand the space that Ubuntu is using, but don't know how.

I've heard talk of the GParted CD, but as my CD drive is broke that isn't an option. I also though I might completely reinstall Ubuntu onto the laptop using a USB pen, but as the computer is quite old it won't boot from a USB drive.

Any ideas please everyone?  I'm an 'intermediate' Windows user, but very new to Linux, so please explain things slowly.... ;-)

Thanks in advance

The Real Jim Shady

---

### Post by raymondh on 2010-02-28
> **TheRealJimShady said:**
> Hi everyone,

Really grateful for some help with my installation of Ubuntu please. This is where I am and some background...

- My laptop is a little old, it's a Samsung X50.
- The CD/DVD drive is buggered
- I don't believe it is able to boot from a USB
- The native OS is Windows XP

What I did...

- While in Windows I downloaded Wubi on recommendation from a friend.
- Installed Wubi/Ubuntu on a small partition of my HD
- Installed it, and then rebooted expecting a dual boot screen. Didn't get one for some reason.
- Fooled around in Windows, and found a menu option where I could change the default operating system when booting. Changed it to Ubuntu.
- When I restarted the PC I was given options to boot one off...
   - Ubuntu
   - Ubuntu recovery
   - Acronis Secure Zone
- Using the first option, I have been using Ubuntu for a week or so and really like it. I don't want to go back to Windows, so now want to expand the space that Ubuntu is using, but don't know how.

I've heard talk of the GParted CD, but as my CD drive is broke that isn't an option. I also though I might completely reinstall Ubuntu onto the laptop using a USB pen, but as the computer is quite old it won't boot from a USB drive.

Any ideas please everyone?  I'm an 'intermediate' Windows user, but very new to Linux, so please explain things slowly.... ;-)

Thanks in advance

The Real Jim Shady

Hi.

It being a wubi install .... a filesystem within/of windows.... it is installed INSIDE your windows partition (possibly the C: drive).  So, the only way to increase its' size is to increase the "virtual" size or, migrate wubi-ubuntu to a real partition.

See the wubiguide for reference.  #'s 8.8 and 8.9.

[https://wiki.ubuntu.com/WubiGuide](https://wiki.ubuntu.com/WubiGuide)

raymond

---

### Post by TheRealJimShady on 2010-03-01
Thanks for this Raymond, I'll give it a go in the next day or so and then report back.

---

