---
title: "Trouble installing. Can't find answers in search.."
date: 2007-09-05
forum: Installation &amp; Upgrades
---

### Post by mindspin311 on 2007-09-05
Ok, I have a dimension 8100 P4  1.4GHz, 512MB RDRAM, GeForce3 64MB card, and a 80 gig HDD.

I plan on upgrading the graphics card to a radeon 9600 pro 256mb, but the one I have is compatible from what I've read and should do for now.

I dl'd the ico, checked it's integrity with winMD5SUM, and burned it to a cd (4x) to be safe like people told me.

I have vista beta 2 and a bunch of other junk on my hdd in just a single partition. I intend to do a clean install as I can no longer use vista beta and have backed up all my files.

I pop in the cd and boot.
Click the first install option.
It loads the kernal, and shows the ubuntu screen with a bar moving side to side.
After about 10 minutes, I get this:

warnings.pm did not return a true value at /usr/bin/ckbcomp line 20.
BEGIN failed--compilation aborted at /usr/bin/ckbcomp line 20.

then it shows things that passed ok (hardware/restricted dirivers, networking, event manager, modules)

When it get to checking the file system, I get

logsave: tzfile.c:344: __tzfile_rewad: Assertion 'num_types == 1' failed.
Aborted

* File system check failed
A log is sent to blah blah blah
Please repair manually

*A maintenance shell will not be started.
CONTROL-D will terminate this shell and resume system boot

ENTER for mainenance

I press enter, and get

bash: no job control in this shell
bash: groups: command not found

then a bunch of buffer i/o error on device sr0, logical block [hex-code]

and

SQUASHHFS error: unable to read block/page errors

all mixed together for awhile



I got this stuff the first time I installed, and redid it with a new disc burned at 4x.



Are these errors reading from the CD or my HDD? I assumed the initial setup didn't write anything.

I mean this all starts with an assertion error and I don't know what num_types refers too. I'm assuming it's supposed to be if (num_types == 1) { error; exit;} but it's not exiting and continuing to install with the assumption of num_types > 1 (even though it's not)

Anyone have this problem??

Should I just bleach and reformat the disk? or just clean it completely? What do I do?

---

### Post by merlinus on 2007-09-05
Did you check the cd for errors at the opening screen?

Did you try Safe Video Mode?

-merlin

---

### Post by mindspin311 on 2007-09-05
The CD does not have any errors. Neither did the last one, where I tried to do the same boot in the safe mode install (2nd option) and got a bunch of errors followed by a blank screen with a blinking underscore..

I think I'm gonna try to boot from my cd-r rather than my dvd drive after all of this.

If anyone has any suggestion, let me know in the meantime. :)

---

### Post by mindspin311 on 2007-09-05
Yatta! All it took was booting from cd-r rather than dvd rom.. Don't know why, but I'm at the desktop and about to click install. woo hoo.

---

