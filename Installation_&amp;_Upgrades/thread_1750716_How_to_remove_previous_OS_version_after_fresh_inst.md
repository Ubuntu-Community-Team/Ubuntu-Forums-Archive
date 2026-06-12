---
title: "How to remove previous OS version after fresh install?"
date: 2011-05-05
forum: Installation &amp; Upgrades
---

### Post by davek22 on 2011-05-05
I have to start all my posts by stating I am not a computer techy and only a novice to the world of linux. 

Anyway, I recently was updating to 11.04 and my wife closed laptop lid during upgrade. Long story sort, system crash.  I ended up copying my data to a thumb drive and did a new install from live cd. After loading the live 11.04 cd, it gave me a choice of "repair" previous version (or something). that is what I did.

Once 11.04 was loaded, it didn't import existing data so I did that myself (thanks to this forum).

I should add that this is a lap top that never had windows...only 10.04 from day 1.

**Everything is running great with exception  for a minor problem...**

**After booting up, and right after dell splash, I get a screen that says GNU GRUB version 1.99 etc**. It asks which OS to install or in 10 sec. my Natty automatically loads. I guess first one listed loads? Choices listed is (not copy/paste but by scribble notes):
[I]Umbunt, with Linux 2.638...generic
[/I][I]Umbunt, with Linux 2.638...generic (recovery mode)
Previous Linux versions
(then 2 memory test lines)

[/I]So, how do I get rid of this screen during bootup? I don't need any other version since I already retrieved my important data. So if removing previous versions is key, then I need to know how to do that.

thanks in advance.

---

### Post by gordintoronto on 2011-05-05
It actually asks which version to run, not install. It's a normal part of the boot process, not a problem at all. 

When there is an update to the kernel, there are always a few computers which don't like the new kernel, and this is how you can choose to use the previous version, or a "safe mode" version of the new kernel.

---

### Post by davek22 on 2011-05-06
Solved my problem after a deeper search. 

I downloaded an app called "startup manager". I simply adjusted some settings to hide that screen during bootup and to change the seconds to zero for making the decision.

Now loads just like before.:P

---

