---
title: "/bin/sh: can't access tty; job control off"
date: 2007-04-02
forum: Installation &amp; Upgrades
---

### Post by UbunduNoob on 2007-04-02
Hello.  This morning I ran the automatic updates in Ubuntu 6.10 (Which I got from the website 2 days ago)

After completion it indicated that a restart was required.  I complied.

At the splash screen the progress bar halts and after a moment I get the following:

---------------------------------------------------------
modprobe: FATAL: Could not load /lib/modules/2.6.17-11-generic/modules.dep:  No such file or directory


BusyBox v1.1.3 (Debian 1:1.1.3-2ubuntu3) Built-in shell (ash)
Enter 'help' for a list of built-in commands.


/bin/sh: can't access tty; job control turned off
(initramfs)
-----------------------------------------------------------

I've been scouring the forums now for an hour and it seems that many people are having similar problems.  All the suggestions for fixing this are basically links to other forums.  I've tried to follow what they've prescribed but most of them are filled with snippets of code that are germain only to that particular incidence and none of them are creating a resolution for my problem.  Or they are so full of lingo that I have no clue how to proceed.

I'm asking for some of you to please "dumb down" the instructions so I could follow.  I am brand-spankin new to Linux in general, so all jargon is way over my head.

My intuition is telling me that during boot it is trying to load a file that should be present (/lib/modules/2.6.17-11-generic/modules.dep) but for some reason is not there.

If I had to guess a solution would be to either 1) make that file available or 2) remove the desire to load that program. 

The problem is, I just don't know how.  I also don't know if that is correct.

I don't mean to be a burden to anyone, but all help in its most elementary form would most certainly be appreciated.

Thank you.

---

### Post by pradeepadapa on 2007-04-02
why dont u try to enter through rescue mode ,what are the options u get in GRUB menu after boot...

---

