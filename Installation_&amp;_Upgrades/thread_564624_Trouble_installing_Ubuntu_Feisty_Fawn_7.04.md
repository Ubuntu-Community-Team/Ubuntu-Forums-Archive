---
title: "Trouble installing Ubuntu Feisty Fawn 7.04"
date: 2007-10-01
forum: Installation &amp; Upgrades
---

### Post by Casper001 on 2007-10-01
[]I am new to Linux and have followed the instructions to install Ubuntu to the letter. Once I have started the process it will continue for a short while and then the following message appears:

[124.537179] BUFFER I/O ERROR ON DEVICE FD0 LOGICAL BLOCK 0

This continue indefinitely but the number in the square brackets increase at random. I can't see a pattern here. 

The computer I want to install Ubuntu on is a Pentium 4 with 2gig ram (three hard discs of 112 gig each). This computer will serve as a server for at least four other desktop computers.

Can anybody please advise me what to do?

Casper001

---

### Post by Yoooder on 2007-10-01
I'm not familiar with that specific message, but it looks that your floppy drive is the source of the issue.

I'd recommend shutting down your machine and unplugging your floppy drive and retrying the installation.  After installation is complete you can shutdown the machine again, plug the drive back in, and see if Ubuntu will boot from your hard drive with the floppy connected.

If it continues to cause problems, you may want to either remove the floppy drive from your setup permanently (if you don't need it) or replace the drive.

Let me know how it goes

---

