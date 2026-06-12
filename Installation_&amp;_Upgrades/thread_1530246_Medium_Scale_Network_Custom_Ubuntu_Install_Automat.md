---
title: "Medium Scale Network Custom Ubuntu Install Automation?"
date: 2010-07-13
forum: Installation &amp; Upgrades
---

### Post by tk2k on 2010-07-13
Hey Everybody,

I'm part of a theater group, and a few of our programers are building a piece of linux based musical cueing software that will run arcross 30+ computers, those details arnt' super important, but what we're trying to figure out how to do is an automated update/install of a customized linux image across these computers.

The idea is, as we make changes to the program and the program's audio files, we need to mirror those changes across the 30+ other computers. If it was just a question of file syncing, I would use rsync, but seeing as there are program support files, etc, involved I'm not sure if that is really a viable option.

The idea was to build a custom install image every night and just 'reimage' the network, the problem is we do not have identical hardware configurations, all will be standard x86 computers, but processor, ram and motherboard will varry between computers, and I really don't want to have to run around to each computer everyday and run a setup (even thought I could keep the image on the network, the idea is this could be entirely automated with just someone hitting GO and waiting a few hours)

Any advice? 

Thanks

---

