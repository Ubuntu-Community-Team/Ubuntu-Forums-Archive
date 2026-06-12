---
title: "Install issues"
date: 2007-08-03
forum: Installation &amp; Upgrades
---

### Post by Romane on 2007-08-03
Good morning

I have just tried to install 7.04. After much hunting, this appears about the only place I can give my feedback. So, two beefs.

First - loads more work needed on the install routines. My X crashed at first boot. I suspect it is because it has a hissy fit about the drivers for my nVidia card (7300 GT) that the install process put in place. Something I can fix if I have access to the root account. But Ubuntu gave me no options for creating a password on the root account, and nothing I tried would give me that needed access when I needed it. This is, to me, a most serious failing.

The only reason I installed this version after my experience with other earlier versions is that the live CD booted beautifully into a graphical environment (albeit Gnome, which I dislike intensely, but is probably fixable later after install, and albeit a standard VGA resolution, for which I have the drivers on hand to fix after install) and it set up my networking perfectly. I assumed that at least on the first boot, Ubuntu would do the same, and for the video would allow a test of the drivers and provide the option if it failed to then go into a safe VGA mode so that the user could attempt a fix later, or even settle for and work with the reduced resolution.

But for me now, I have a fully installed and useless copy of Ubuntu 7.04 sitting on my hard drive.

After this experience, it will be at least a two version increment before I look at Ubuntu again. Each version I have tried has ended up only in dissatisfaction and disillusionment, most especially after all the hype that has surrounded the name. Mayhap by 9 point something it may reach a stage of maturity that will make it a worthwhile contender for Microsoft. But for now, the CD for 7.04 will go the same place as my earlier Ubuntu CDs - the bin and the tip.

Romane

---

### Post by 505 on 2007-08-03
So, do you want any help, or have you already given up on Ubuntu?
There is indeed no root account, but during installation you created an account for yourself. Even if X fails to start, you can log in using this account. If you need to execute a command with root privileges, prefix the command by 'sudo' and give your password.
If you don't like Gnome, download Kubuntu. It's Ubuntu with the KDE interface.
For the nVidia card, maybe you can download the official drivers from nVidia's site and install these. See if that gives you better results.

---

