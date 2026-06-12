---
title: "Can't install 10.10 on Dell GX240"
date: 2010-10-14
forum: Installation &amp; Upgrades
---

### Post by Konstanty on 2010-10-14
Help, please!  I've been trying for three days to install Ubuntu 10.10 on a Dell GX240, with no luck.

Each and every time, I boot from the Live CD and get as far as the language selection screen.  I click "Forward," and the little gearwheel spins...

...and spins...

...and spins...forever.  Or until I power the machine down, whichever comes first.

The BIOS is at its latest level (A05), and it's in original factory configuration -- I haven't made any modifications to it.  I've also tried booting into "Try Ubuntu without installing," and running "Install Ubuntu" from within that environment, with the same non-results.  After a minute or so, the machine becomes completely unresponsive and I have to power down and start all over again.

I've done a lot of prowling the web to find answers, most of which recommend adding "acpi=force" to the boot options.  Unfortunately, that doesn't work for me.  Nor have any of the various acpi/apic options.

I don't think this is a hardware problem, since I am able to install and run XP on this machine without any problems whatever.

Specs for the machine are:

256M memory, at 133Mhz

CPU speed 1.7 GHz, Pentium 4

I'd much prefer running Ubuntu on this machine than anything from Microsoft, but unless I can find a workaround, I'll have no choice.  Ideas, anyone?

Thanx in advance.

---

### Post by PRC09 on 2010-10-14
I believe the minimum requirements for most of Ubuntu versions is at least 512mb ram or else you will have problems...I have that machine running 10.04 with 512mb but not well enough to use it for most applications.....


[https://help.ubuntu.com/community/Installation/SystemRequirements](https://help.ubuntu.com/community/Installation/SystemRequirements)

---

### Post by Konstanty on 2010-10-14
> **PRC09 said:**
> I believe the minimum requirements for most of Ubuntu versions is at least 512mb ram or else you will have problems.[]("https://help.ubuntu.com/community/Installation/SystemRequirements")

Problems with running, or problems with installation?  I'm reluctant to upgrade the memory until I can actually get an OS installed on it.

---

### Post by PRC09 on 2010-10-15
Sorry for the delay in response...My experience has been that trying to install with 256mb is virtually impossible,I have tried on a few machines but just gave up.I wasnt that ambitious and it was mostly for testing.Also running with 256 I dont think you would be very happy with the performance thats for sure.....Just my thoughts.......

---

### Post by Konstanty on 2010-10-15
Well, I installed 10.04 on an IBM A22 with only 256M.  After installation it was slow, but I was surprised at just how well it worked on such little memory.  It really flies now that it's upgraded to 512.  Point is, prior to the upgrade I *could* install Ubuntu on it, and with no problems at all.

Not trying to argumentative about this, I just don't want someone reading this thread to see the "It can't be done" and think "Problem solved; I guess I don't have to look any further into this one." In my searching around the net, I've found too many other people who've had strange problems installing various versions of Ubuntu on a GX240, and they weren't related to memory.

If a memory upgrade will really do the trick, I'm more than willing to do it.  But I'm leery of spending the bucks (of which I don't have very many to spare) only to find that some other mysterious factor is what's keeping the install from working.

Thanks for replying, though.

---

