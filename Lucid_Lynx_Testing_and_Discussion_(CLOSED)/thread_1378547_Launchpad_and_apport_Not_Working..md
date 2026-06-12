---
title: "Launchpad and apport Not Working."
date: 2010-01-11
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by phillw on 2010-01-11
Hi to the wandering mods !!!

I don't get many crash reports, but the last three I've tried to register have come back with a LaunchPad error (Whoops, there's a problem - we're aware of it) - Is there another way, and, if so - where are the crash report files saved on my system ?
> 
**Oops!**

                        Sorry, something just went wrong in Launchpad.           
                        We’ve recorded what happened,             and we’ll fix it as soon as possible.             Apologies for the inconvenience.           
                        (Error ID:             OOPS-1472G2681)           
                                 
Regards,

Phill

---

### Post by ranch hand on 2010-01-11
It seems to work here.  I got some announcement that a crash had ocrured and sent it in.  This was after you posted.

---

### Post by phillw on 2010-01-11
> **ranch hand said:**
> It seems to work here.  I got some announcement that a crash had ocrured and sent it in.  This was after you posted.

Mebbie they've black-listed me ;)

It's an inconvenience to me, also I'll feel guilty as anything if the release goes out & people have a problem I couldn't report :(

Phill.

---

### Post by cariboo on 2010-01-11
Can you login to your Launchpad account? I was just looking at some of the unsolved bugs I've submitted, and had no problems. I saw that was an apport update today, so that may have fixed your problem.

---

### Post by castrojo on 2010-01-11
The crashes are kept in /var/crash btw.

---

### Post by phillw on 2010-01-11
> **cariboo907 said:**
> Can you login to your Launchpad account? I was just looking at some of the unsolved bugs I've submitted, and had no problems. I saw that was an apport update today, so that may have fixed your problem.

Yeah, i can get onto launchpad fine. Look at what's going on, pop over to [https://launchpad.net/ubuntu/lucid/+queue](https://launchpad.net/ubuntu/lucid/+queue)  no problems, system knows who I am etc.

Report the bug, check to see if duplicates, if there isn't - select report new bug and get the error message as per my 1st post :-\

I grabbed all the updates (grub v1.98 etc) - It was on re-booting after all of that, just as i was restarting pidjin, FF etc. that I got the crash report.

Phill.

---

### Post by ranch hand on 2010-01-11
That was probably the same thing that I got.  Some notice that X had crashed which I thought was funny as I was having no problem with the system.  I think it has to do with the mixups during boot up.

Pretty well reported.

---

### Post by phillw on 2010-01-12
Hmm, as feared -  .. It was 'first' reported 8 hours after it affected me & now has a count of 5 people plus myself :(

Still, at least it is now reported.

[https://bugs.launchpad.net/ubuntu/+source/hal/+bug/506260](https://bugs.launchpad.net/ubuntu/+source/hal/+bug/506260)

If the same thing happens in the future, is there a way to manually add the contents of /var/crash to a manually raised bug report ? I appreciate that a manual raising of a bug could lead to a duplicate - but I would have a good look round 1st.

Phill.

---

### Post by cariboo on 2010-01-12
I've been getting random Xorg crashes for a day or two, I reported it the first time it happened, and told apport to ignore it after the first time.

---

