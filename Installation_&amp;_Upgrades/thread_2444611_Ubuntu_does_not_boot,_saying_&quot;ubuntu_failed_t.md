---
title: "Ubuntu does not boot, saying &quot;ubuntu failed to start daemon for power management&quot;"
date: 2020-06-01
forum: Installation &amp; Upgrades
---

### Post by jlw1808 on 2020-06-01
I was working on my system, and ended up doing "sudo apt-get autoremove", along with lots of other apt-get and apt commands. Upon restarting the system I get a terminal window with lots of messages that say "OK" in green, and some that say "FAILED" in red. All the ones that say failed have to do with "Daemon". after printing a few more items, it finally gets stuck at "ubuntu failed to start daemon for power management", then starts saying "A start job is running for Hold until boot process finished up (1min 33s / no limit)". I do not have too much experience with linux or ubuntu, and I am clueless on why this does not boot...

I saw someone mention a boot repair on the fourms, so I ran that and the machine still doesn't boot, here is the output from it: [https://paste.ubuntu.com/p/cpSvnxXw4c/](https://paste.ubuntu.com/p/cpSvnxXw4c/)

---

### Post by CelticWarrior on 2020-06-01
welcome.

A few notes regarding your problem:
> ended up doing "sudo apt-get autoremove"
is perfectly fine. Unless the system is seriously broken that command is harmless.

Now, what can happen after > lots of other apt-get and apt commands is anyone's guess. It would be great if you remember what were those commands exactly because it looks like you removed some important stuff.

---

### Post by jlw1808 on 2020-06-01
Well I was trying to install pyhole... so basically all commands listed on the site is what I ran... I believe I was getting a different boot problem Initially, when I looked it up I believe it was something to due with graphics drivers. I did end up putting in a old graphics card and booting using that rather than integrated graphics, so the system is now using a gpu and has a different boot problem I believe.

---

