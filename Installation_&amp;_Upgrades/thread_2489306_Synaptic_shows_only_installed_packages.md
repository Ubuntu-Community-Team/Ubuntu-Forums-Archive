---
title: "Synaptic shows only installed packages"
date: 2023-07-25
forum: Installation &amp; Upgrades
---

### Post by John Jason Jordan on 2023-07-25
I've been using Ubuntu for 15 years, nowadays Xubuntu. This morning I have a brand new fresh install of 22.04, and I can't install anything because Synaptic shows only installed packages. I've never seen that before. Why? I've looked all over for a setting, but I can't find it. Help!

---

### Post by bobunderwood99 on 2023-07-25
Select "All" at the top of any Category list.

[IMG]https://ubuntuforums.org/attachment.php?attachmentid=292512&stc=1[/IMG]

---

### Post by guiverc on 2023-07-25
I don't usually use *front-ends* like `synaptic`, but have you updated your software lists?

A *freshly* installed system only knows about packages that were on the installation media at install time, ie. already installed packages. When you update your software lists, its discovers what else exists that wasn't on installation media, plus the upgraded packages that have released since then.

ie. I'm suggesting `sudo apt update` 

Even if that's not your issue, reading that output for issues would be my next exploration step.

---

### Post by John Jason Jordan on 2023-07-25
I had already tried 'sudo apt update,' with no luck. I also tried rebooting, but nothing helped. Eventually it got to be time for news to be on, for which I wanted to see it on the HDHomeRun on my network. The news started, then the picture broke up a little, then cleared up, then broke up some more. Eventually I found that the network connection was sort of working, but not well. The house is wired for gigabit ethernet, but that doesn't mean you can't have a wonky patch cable. And apparently Synaptic is super fussy, so on the slightest hiccup it decided to list only installed applications.

Oh, and the installer did get to the internet; it got my location, figured out which language I would probably want, and several other things. In fact, I even installed several things from the command line before I ever launched Synaptic. It would have been helpful if Synaptic had said something about its net connection to give me at least a clue.

---

