---
title: "Upgraded to 11.10 - Blank Screen - Here's How I Fixed It"
date: 2011-10-14
forum: Installation &amp; Upgrades
---

### Post by LudwigvonMises on 2011-10-14
I normally don't post on these forums. I usually grab what info I need and run. But after seeing all of the problems in the 11.10 upgrade, I wanted to post this and see if I could help anyone out.

I did the upgrade from 11.04 to 11.10 on an Asus Eee PC Netbook. Walked away for a few hours and came back to a blank screen. I immediately came to this forum and saw a bunch of people with the same problem, so I started to attempt to fix it. I was getting the "Network Connection" screen forever and couldn't get anything to load. GRUB worked, but I couldn't boot into recovery mode. So I tried the solution of moving the /var/run folder(s) (it's post #24 on one of the bug posts. It's posted all over the threads that are active). Not only did it not work, it made things worse. I just got flashing screens and then hanging with a couple lines of info about loading packages or something.

So I tried to do a manual upgrade from the command line, and it told me there were no new versions of Ubuntu. That meant that 11.10 was active on the computer with something messed up. So I just tried a
```
sudo apt-get update
```
to see what happens. Well, it took about half an hour and loaded a ton of stuff. So I guess my upgrade was incomplete. When it finished I rebooted and everything is perfect now. No freezes, wireless works, mousepad works, PulseAudio works (didn't work for my mic in 11.04).

I'm not an Ubuntu expert so maybe some more knowledgeable people can comment and tell the rest of the forum what happened, why it worked for me, and if it could work for others. I just hope I can save some people a lot of time and frustration if they have a similar problem.

Good luck everybody.

---

