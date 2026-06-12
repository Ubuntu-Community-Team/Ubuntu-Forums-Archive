---
title: "Laptop won't boot after installing 7.10. Urgent!"
date: 2007-10-21
forum: Installation &amp; Upgrades
---

### Post by oliverb4ss on 2007-10-21
I updated my Ubuntu 7.04 to 7.10 and after the mandatory restart the OS won't boot up.
The Ubuntu loading screen and the orange bar appear (the orange bar fully loads) and then the screen goes blank and nothing happens.

I\m using the 7.04 live-cd right now, but I REALLY need to get my OS working again.
Is there a way to undo the upgrade (doubtfully) or some way to fix it?
Formatting the drive isn't an option in this case.

Thanks in advance.

---

### Post by Octavgmail.come on 2007-10-21
i'm having the same issue although i havent even be able to install it yet.

---

### Post by oliverb4ss on 2007-10-21
No one?
I don't mean to be pushy, but this is quite an emergency.

---

### Post by rookie_paul on 2007-10-21
I had some problem too. Have you tried to do something after booting in recovery mode?

---

### Post by oliverb4ss on 2007-10-21
When I try to start in recovery mode, it says Error 32: Needs to be authenticated
And then nothing happens, again.

---

### Post by rookie_paul on 2007-10-21
Do you mean you can do nothing in recovery mode? Does it just freeze? This is a big problem! In this case, I am afraid I can't help. Sorry! :(

---

### Post by oliverb4ss on 2007-10-21
I mean that when I choose recovery mode (doesn't matter, which kernel version), all I get is the black screen with a message saying Error 32: Needs to be authenticated (Authentication needed or something similar).

So I can't get the OS to boot up in any way.

I really need the computer for some work- and school-related stuff. I could reinstall 7.04, but that's not until next weekend, when I can get my hands on an external hard drive.

Any other suggestions?

---

### Post by Whiffle on 2007-10-21
Try booting in regular mode, and then when you get to the ubuntu loading screen, hit ctrl+alt+F1, you may find some error messages there that would be useful.

---

### Post by Craigus on 2007-10-21
Do you have a separate /home partition ? If so, you could install 7.04, and tell the installer to format all of the partitions other than /home .

---

### Post by tajreed on 2007-10-21
Try booting to the 2.6.22-12 kernel rather than the 2.6.22-14. That worked for me. When I had the same problem.

---

### Post by oliverb4ss on 2007-10-22
No unfortunately I don't have a separate \home partition.

I also tried booting in normal and safe mode with both the new and the old kernel version.

Still, in normal mode I get the blank screen (completely blank, not even the slight glow to tell you that it's turned on) and when trying safe mode it says 'Error 32: Needs to be authenticated.' The same result with both kernels.

---

