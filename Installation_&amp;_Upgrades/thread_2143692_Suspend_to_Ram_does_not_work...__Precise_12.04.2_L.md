---
title: "Suspend to Ram does not work...  Precise 12.04.2 LTS"
date: 2013-05-09
forum: Installation &amp; Upgrades
---

### Post by jeanjean84 on 2013-05-09
Hello!
I have a problem with Suspend to Ram for my computer since upgrading to Precise!
I like Precise! I use it with Gnome Classic. Unity is good.... but I prefer Gnome Classic and its drop-down menus!
But that's not the point, I believe! ;)

My problem is with the Suspend to Ram!

On Lucid, I managed, with the "nomodeset" option in grub, to suspend to ram with the command "sudo / usr/sbin/s2ram-f-a 3." Super!
Without "nomodeset" on wake up, I had an unreadable screen with random lines! Blind reboot or magic buttons! :(

With Precise, the "nomodeset" option in grub works, with correct waking up too ......... but with "1024x768" screen resolution, impossible to change ! And not very nice! :(
Without the "nomodeset" option, I have a "1440x900" "definition on my screen Hewlett Packard 19! Nicer to work!
But no suspend to ram possible: on waking up, the screen is unreadable with the random lines! Back to blind reboot or magic buttons! As before in Lucid!

I tried so many tricks gleaned here and there!!! Scripts, grub options, tuxonice, hibernation, etc. .... Nothing seems to work!
Either suspend to ram does not work (not stopping the computer), either the waking up produces the famous random lines ...

So I come here to ask for help!
I want to start my tests from the scratch again: my setup:

* Graphics card: ATI
    > ~ $ Lspci-vnn | egrep "VGA | 3D | Display"
    01:00.0 VGA compatible controller [0300]: Advanced Micro Devices [AMD] nee ATI RV370 5B60 [Radeon X300 (PCIE)] [1002:5 b60] (prog-if 00 [VGA controller])
    01:00.1 Display controller [0380]: Advanced Micro Devices [AMD] nee ATI RV370 [Radeon X300SE] [1002:5 b70] 

* Precise 12.04.2 LTS without Compiz.

Tell me which indications I have to give for diagnosis and help!
Please HELP! 
I'm tired of not being able to suspend to ram ......
Thanks!
Best regards

jeanjean84

---

### Post by jeanjean84 on 2013-05-10
HELP! 
Is there anybody there? :(

---

### Post by jeanjean84 on 2013-05-13
Up! :(

---

### Post by jeanjean84 on 2013-05-18
Oups!..... :( :( :(
First time without ANY answer to a REAL problem in almost 10 days...
Ubuntu community on the forums NEVER failed me since 2005...
I know there are a lot of posts about my question on the forum.... but I need PERSONALISED help, because _none of them_ works for me...
I REALLY need help!
Stopping and rebooting my computer is not very good (e.g. for the condenser of the motherboard...)... leaving my computer on all the time is not the best option either...
So PLEASE: HELP!  S.O.S. 
Thanks for your early reply... :)
Best regards

---

### Post by thedeerhunter270 on 2013-06-12
I had the same problem.

What I did was change the video driver to the 'version current' recommended, from version 173.

Now suspend works fine.

hope that helps.

---

### Post by jeanjean84 on 2013-06-14
Thanks for replying, thedeerhunter270!

> **thedeerhunter270 said:**
> I had the same problem.

What I did was change the video driver to the 'version current' recommended, from version 173.

Now suspend works fine.

hope that helps.

How did you change the video driver to the 'version current' recommended?

---

### Post by jeanjean84 on 2013-07-04
Still no help....
And the worst is that it works on my old Window$ XP.....
Shame.....
Please help! :(

---

