---
title: "Fiesty LiveCD won't start - read for error issues"
date: 2007-06-10
forum: Installation &amp; Upgrades
---

### Post by samadams on 2007-06-10
I upgraded from Dapper to Edgy then Fiesty using the update manager.  However I only get about 15 minutes of uptime until my hardrive spins faster than a weathervane in a hurricane and X grinds to a halt.  My only solution so far is to restart X which buys me 15 more minutes.  I'd like to do a fresh Fiesty install but my cd won't boot. (it is a good one - I used it on another machine - and I downloaded another .iso just to be sure but although I  just burned 10 CDs it won't let me burn this one!?)

I could download and reburn in XP but how do I know I just won't have the same problem?

When I start the liveCD I get the main menu and choose to Install.  I get a progress bar that tells me it's loading the kernel (there are some video display problems here I never had before - random pixles in a line through the middle of the screen in various colors)

The screen then goes blank and then proceeds to echo the following after about 2-3 minutes:

[FONT=Courier New][COLOR=Blue]BusyBox v1.1.3 ( Debian 1:1.1.3 3ubuntu3) Buil-in shell (ash)
Enter 'help' for a list of built-in commands.

/bin/sh: can't access tty: job control turned off
(initramfs) [  113.821376] ata2.01: exception Emask 0x0 SAct 0x0 Serr 0x0 action 0x2 frozen
[  113.821456] ata2.01: cmd a0/01:00:00:00:00/00:00:00:00:00/b0 tag 0 cdb 0x12 data 36 in
[  114.141355] ata2.01: revalidation failed (errno=-2)
[  125.440655] [/COLOR][/FONT][FONT=Courier New][COLOR=Blue]ata2.01: exception Emask 0x0 SAct 0x0 Serr 0x0 action 0x2 frozen
[  125.440722] [/COLOR][/FONT][FONT=Courier New][COLOR=Blue]ata2.01: cmd a0/01:00:00:00:00/00:00:00:00:00/b0 tag 0 cdb 0x12 data 36 in
[  125.760629] [/COLOR][/FONT][FONT=Courier New][COLOR=Blue]ata2.01: revalidation failed (errno=-2)
[  137.608758] sdb: assuming drive cache: write through
[  137.620751] [/COLOR][/FONT][FONT=Courier New][COLOR=Blue]sdb: assuming drive cache: write through
[FONT=Tahoma][COLOR=DimGray]I then get a cursor that whatever commands I type, the ENTER key acts as a carriage return and not an execute key.

Any ideas?
[/COLOR][/FONT] [/COLOR][/FONT]

---

### Post by hobs0n on 2007-06-10
same problem for me..

---

### Post by samadams on 2007-06-11
Man if anyone can take a look at this I'd really appreciate it.
Thanks

---

### Post by merlinus on 2007-06-11
Maybe this will help:

[http://ubuntuforums.org/showthread.php?t=421588&highlight=can%27t+access+tty](http://ubuntuforums.org/showthread.php?t=421588&highlight=can%27t+access+tty)

-merlin

---

### Post by hobs0n on 2007-06-12
Yeah I read that thread too and got it working :happypanda:

---

### Post by samadams on 2007-06-15
Thanks a million!  The first method in that thread did the trick.  Though I had to try it twice. (it locked up on formatting the root partition the first time)  I had to go about it around about though.  After it locked up, I decided to try a fresh Edgy install and then upgrade to Fiesty.  When that locked up 87% of the way through (on the clock synchronization) I gave Fiesty another try.  I guess since Edgy had successfully repartitioned everything it worked easier this time.

Thanks again!

---

