---
title: "How do I MOVE /HOME dir to run it from USB instead of harddrive?"
date: 2007-05-16
forum: Installation &amp; Upgrades
---

### Post by trapix22 on 2007-05-16
Working on keeping data more secure. What I'd like to do is ...

...MOVE my /home dir and have it be on USB from now on and then I'll encrypt it. That way...
          a)  when I go, my data goes with me
          b)  if I lose it (stolen) it's encrypted and protected

QUESTIONS:
     1. If I move it... is there no more /home on harddrive so EVERYTHING that usually gets saved in /home ends up on USB or is there /home just not being used?
     2. After boot, how will linux know where home is? Does it ask for it or do I have to manually tell it each time I log in?
     3. How do I make sure Ubuntu (Edgy) doesn't litter the harddrive with temp/hidden/backup files like Windows does (the reason for my troubles to begin with)?

Thank you so much, in advance, for any advice you can provide.

---

### Post by kidders on 2007-05-17
Hi there,

> **trapix22 said:**
> 1. If I move it... is there no more /home on harddrive so EVERYTHING that usually gets saved in /home ends up on USB or is there /home just not being used?Your /home (or perhaps /home/username) would just be a mount point, perhaps with a skeleton configuration in it, depending on when & how your USB device gets mounted.

> **trapix22 said:**
> 2. After boot, how will linux know where home is?You would update your /etc/fstab to reflect your changes.

> **trapix22 said:**
> 3. How do I make sure Ubuntu (Edgy) doesn't litter the harddrive with temp/hidden/backup files like Windows does (the reason for my troubles to begin with)?Linux doesn't do any littering! Is there something in particular you're concerned about?

[COLOR=Silver][[SIZE=1]*[UAResolved]*[/SIZE]]("http://ubuntuforums.org/showthread.php?t=377083")[/COLOR]

---

### Post by trapix22 on 2007-05-17
Hi and thank you for the reply
what happened before is my database (MS Access) with client private info got broken into by ex-employee (noone had access but me). After that, I encrypted with PGP whole disk but THAT got hacked and I hired an expert and he showed me how it happened (he hacked my system right in front of me). He used all these files I had no idea existed and literally EVERYTHING I've ever done on that computer he showed me line by line... Anyway...THAT'S what I'm concerned with.

So I wanted to put the /home dir on USB, encrypt and then keep with me when I leave the office. I am a total noob so I need step-by-step if you could...

I found tutrial how to move /home. My questions is... when I encrypt USB (dm-crypt) and boot computer with USB in... It will load but /home is encrypted. Will it automatically ask for encrypt key?

Now you know more detail about my concers... I'm open to suggestions (pls keep in mind to talk in baby-linux language :). Thank you so much for the help.

---

### Post by kidders on 2007-05-17
Hey again,

This isn't an easy issue to deal with, in that appropriate use of encryption is really only half the story. It tends to be best suited to protection against malicious users with physical access to a box. For remote users, encryption normally doesn't prove much of an obstacle.

Here's one way of approaching your problem:

[B]- 1 -
[/B]You need to satisfy yourself that the applications you use are well-written, and adhere to the usual conventions, in terms of where they store data, and how they manipulate it. There are certain applications that it is simply *never* safe to run on a system that deals with sensitive information. MS Access is certainly a good example. Depending on the system, Xorg may be another.

**- 2 -**
You would generally expect applications to store data in a few different places. You need to identify what these are. Common examples are:[LIST]
[*]Swap
[*]Temporary storage
[*]Filesystem[/LIST]In high-security environments, each of these could be encrypted, but there are major drawbacks associated with doing so...[LIST]
[*]Encrypting virtual memory imposes a system-wide performance penalty.
[*]The best way to provide encrypted temporary storage is probably to mount it into encrypted swap space, but there is good potential there to introduce security problems related to DoS attacks.
[*]Something like a database will almost certainly be stored over RAID. Adding a layer of encryption on top of that poses a significant risk of serious data loss in the event of hardware failure.[/LIST]The thing that puzzles me slightly is that, as I mentioned, filesystem encryption really only guards against things like theft of a hard disk ... ie risks that require physical access to your computer, while it's turned off. Turning your machine on pretty much negates any protection it would offer. Basically, I would be happy to answer your question & type out a quick overview of setting up dmcrypt ... but I'm not completely sure you'd end up with a safer system.

It may be that more basic security issues would be worth investigating first. For instance, there is a 100% probability that you will expose sensitive data if you do any of the following:[LIST]
[*]Fail to properly secure your home directory.
[*]Give anyone your root password.
[*]Set account passwords that are easy to guess.[/LIST]As an example, it is perfectly conceivable that someone could acquire root privileges eg via Webmin, look through your ~/.bash_history for hints about your recent activity, and use it as a guide to where all the important stuff is stored. The point, I suppose, is that there is no point in trying to protect your data if you then decide to leave the front door open!

I'm not sure how much you know about security (so you may already know this), but the best place to start is with the cardinal rule:

[B][COLOR=DarkRed]Never grant anyone or any*thing* any more access to _anything_ than is absolutely necessary.[/COLOR]
[/B]
If you break that rule on a Linux system, you instantly neutralise all other security precautions you may be taking.

Anyhow, enough rambling! I'm happy to help in any way that I can. Some details of what your expert did to your system would be useful for identifying potential risk areas for you. Something else worth thinking about is the level of security your require. For instance, if you are storing commercially sensitive information en masse (eg in a large database), and depending on what kinds of services are being offered from your machine, it may be appropriate to look into hardened Linuxes. Then again, you may simply be looking for general consumer-oriented advice on good practice.

I hope at least *some* of this is helpful!

---

