---
title: "Breezy better than Dapper?!"
date: 2006-06-16
forum: Installation &amp; Upgrades
---

### Post by dregs on 2006-06-16
I was running Breezy. I upgraded to Dapper to get support for suspend to RAM and for my built-in SD card reader on my Inspiron 6000. Well, the SD card reader works sometimes, and suspend to RAM never wakes up. Requires a reboot.

Furthermore, the following things broke after upgrade:

1. My front-panel buttons (play/pause, prev/next, etc.) no longer control playback in Amarok
1b. while attempting to set these buttons up (using the System > Preferences > Keyboard Shortcuts app that works fine in Breezy) I was unable to fix the problem... but I was able to completely disable the 'm' and '0' keys (which fortunately came back after a reboot). I didn't have any weird problems like that in Breezy.
2. RealPlayer was uninstalled.
3. Xchat was unistalled.
4. My touchpad settings reverted to @#$%ed up, and the fix that worked in Breezy didn't work in Dapper. I had to re-Google to find a way to get the touchpad to be humanly usable.
5. During upgrade, at the very end, it told me that something had gone wrong while trying to upgrade Samba and that my system might be in an unusable state. Maybe that's to blame for some of these problems. Thing is, I don't really want to do a clean reinstall of a machine I use every day. I did rsync my home directory to an external drive before the upgrade, but it would be very annoying to have to interrupt my work and install from scratch-- especially if I then have to re-evaluate Breezy vs. Dapper at that point.

Breezy was great. What happened?

In fairness, one thing that went well is that Audacity started working in Dapper, and a drum sequencer that I had installed (and forgotten about because it never showed up in the menu) showed up in the menu. Also, the upgrade process preserved all my settings, preferences, files, etc. and all my apps (I think) except the aforementioned two. And connecting to the network happens faster. 

I see that there are a few improvements in the kernel, but seemingly at the cost of some stuff that used to work for me and now doesn't.

What can I do to fix my samba problem? What can I do to fix these other problems? Why doesn't suspend work for me? It works for other people with Inspiron 6000s, or so I have heard.

Peter

---

### Post by givré on 2006-06-16
Breezy better than dapper ? definitly not

Breezy better than breezy-upgrade-to-dapper ? definitly not

breezy better than breezy-with-quite-a-lot-of-change-upgrade-to-dapper ? probably, 
because the upgrade mechanism seams to not be very powerful for that kind of situation, so you can encouter some problem, that you could fix but with some time.

What i always recommend : A fresh install (with the alternate CD to be sure to have no issue)

---

### Post by dregs on 2006-06-16
Well, what qualifies as "quite a lot of change?" Installing a few applications shouldn't count as "change" in a real-world OS, so I assume you're talking about my few edits to the X11.conf file to make the touchpad work in Breezy. 

Other than that, I didn't change anything (except through the GUI, for example setting up my WEP key, adding FTP passwords, setting up the media buttons, etc.) I didn't buy a computer so I could play with configuration files.

So what's "quite a lot of change?"

Peter

---

### Post by givré on 2006-06-16
I can't say what is "quite a lot of change", i just wanted to share my view about it after passing a lot of time in this forum to resolve the problem of people. And for me it appears clearly that people encouter lot of problem when they dist-upgrade from breezy, but a freash install of breezy and just after a dist-upgrade seams equivalent to an install of dapper.

Did you see this poll, it's quite interesting [http://www.ubuntuforums.org/showthread.php?t=187024&highlight=dapper+install](http://www.ubuntuforums.org/showthread.php?t=187024&highlight=dapper+install)

The result is (when you sum some problem with any problem at all, because you always encouter problem,even small, with an install of linux, isn't it)

-For a fresh install :14 % had encountered big problems
                           86 % had small or no problem

-For a dist-upgrade :45 % had encountered big problems
                            55 % had small or no problem

That's facts. So what i would recommand to the developper is a better tool to upgrade.

But dapper is definitly better than breezy

---

### Post by dregs on 2006-06-16
Well, I fixed the samba problem (a lot of people seem to be having it) and I'm going to see if it fixes any of my other problems. So far, it doesn't seem to fix the media buttons. I can't do a clean install right now, so I guess I am waiting to see what happens during the next update.

---

### Post by ezsit on 2006-06-19
> Breezy better than dapper ? definitly not

Breezy better than breezy-upgrade-to-dapper ? definitly not

breezy better than breezy-with-quite-a-lot-of-change-upgrade-to-dapper ? probably, 
because the upgrade mechanism seams to not be very powerful for that kind of situation, so you can encouter some problem, that you could fix but with some time.

What i always recommend : A fresh install (with the alternate CD to be sure to have no issue)

This is very subjective. I have 5.10 running very well on two older AMD machines (1.0 ghz) and an older celeron (2.0 ghz). I don't have many drives, two internal IDE drivers on each computer and cd/dvd burners, some usb external devices (printers, scanner, cameras, mp3 players, etc.). Everything works beautifully under 5.10!

I read the forums and decided NOT to upgrade to 6.06. Why? Because everyone seems to be complaining about problems with very simple things like IDE and SATA problems, video problems, etc. Things that should just work. 

5.10 worked like a charm from install to present, never a problem. I think I'll just wait till 7.06(?). 5.10 should receive updates till then and maybe Ubuntu can work out a better development schedule and practice that yields a more stable release.

---

### Post by givré on 2006-06-20
How could you say that without trying it. Of course peaple complain, but of course, that's not new, this forum is made for that. At the beginning of breezy also, and for evry release, and you could be sure that it will be the case for the following.
A lot of people who complain here are really really beginner, and of course they don't know how to configure there system (when it's not automatic) but we are here for that, and after all is ok.
But everything is not better, there is two big problem in dapper, the new graphical installer (should be update nearly), and the upgrade from breezy, which are source of a lot of issues. But the alternate cd is made for that.
It rocks solid for a lot of people, you should give him a try.

---

### Post by lordmule on 2006-06-20
In my own experience the upgrade managed to increase the disk usage despite having removed the extra kernels and clean the apt repos. The worst part was a massive performance degradation with keystroke response times reaching 1/2 second. I had no choice but to perform a clean install.

---

