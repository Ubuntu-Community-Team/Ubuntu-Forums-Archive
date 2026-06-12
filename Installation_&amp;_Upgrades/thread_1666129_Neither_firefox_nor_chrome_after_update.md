---
title: "Neither firefox nor chrome after update"
date: 2011-01-13
forum: Installation &amp; Upgrades
---

### Post by arnaldo on 2011-01-13
I am using maverick.  Since yesterday update, I can't get either firefox (3 or 4) or google-chrome up.  All of them bail out with the same message:

Inconsistency detected by ld.so: dl-open.c: 583: _dl_open: Assertion `_dl_debug_initialize (0, args.nsid)->r_state == RT_CONSISTENT' failed!

Meanwhile, all other desktop applications seem to be working correctly.

What could be the cause?

---

### Post by tommcd on 2011-01-14
Rename ~/.mozilla to ~/.mozilla.bak, and then relaunch Firefox. It is possible that your FF profile has been corrupted by a rogue addon, or something else that you have done to your system.
This is likely due to something that you have done to cause this.

---

### Post by arnaldo on 2011-01-14
I had tried that already.  I even created a new account, end the problem persists.  Anyway, it happens both with firefox and chrome.

I also did a potentialy dangerous thing and ran each browser as root.  Both worked normally.  So, it looks like some kind of permission thing is behind the problem, but I still have no clue.

---

### Post by arnaldo on 2011-01-18
It turns out that there was a bad link for libGL.so.1; the misconfigurations was due to a hack that attempts to keep a dual graphics notebook working with either chip.  What threw me off base was the fact that no other applications seemed to be affected.

---

### Post by dino99 on 2011-01-18
remove/purge then reinstall the package (with synaptic)

---

### Post by arnaldo on 2011-01-18
pliiiiiiiiiiiiz!

I posted already a hard found but simple solution to the problem.

Reinstalling is what you do when you don't understand what is going on, but is the default mindless action, which I had already undertaken.  

It did not and certainly could not have solved my problem.

---

### Post by tommcd on 2011-01-19
> **arnaldo said:**
> It turns out that there was a bad link for libGL.so.1; the misconfigurations was due to a hack that attempts to keep a dual graphics notebook working with either chip.  
Glad you got this fixed!
I am curious though, how did you discover this?

---

### Post by arnaldo on 2011-01-19
I kept googling for information, and a discussion in some forum suggested it may have been a library not found problem.

So I went to /opt/google and executed

ldd chrome/* | grep found

and found nothing.  But then I noticed the talkplugin directory, so, what the heck

ldd talkplugin/* | grep found

and got

libGL.so.1  not found 

(or something similar).

My notebook has two video cards, and activates either when booting guided by a hardware switch; a script run on boot links /usr/lib/libGL.so.1 to the appropriate library.  I have all this process well in mind, so as soon as libGL was mentioned, it was clear what to look for and it was trivial to repair the botched link.

---

### Post by ganesh3 on 2012-04-07
> **arnaldo said:**
> It turns out that there was a bad link for libGL.so.1; the misconfigurations was due to a hack that attempts to keep a dual graphics notebook working with either chip.  What threw me off base was the fact that no other applications seemed to be affected.

What does this mean?

I too have the same problem with a bad link for libGL.so.1.

What do I have to do to rectify it?

Regards,

Ganesh Bhat

---

### Post by arnaldo on 2012-04-08
> **ganesh3 said:**
> What does this mean?

I too have the same problem with a bad link for libGL.so.1.

What do I have to do to rectify it?

Regards,

Ganesh Bhat

First, you need the actual lib file; this will likely depend on which version of the distribution you use.  Mine is /usr/lib/libGL.so.1.2 ; if you keep changing versions of this lib, say, to use an Nvidia driver, it is a good idea to keep a copy of this file elsewhere in the disk.

Under these conditions, I made this simple alias, which solves the problem, whenever it reappears:

alias glfix='pushd /usr/lib;sudo ln -sf libGL.so.1.2 libGL.so.1;popd'

Of course, it would be better to fix the script that is botching things...

---

### Post by ganesh3 on 2012-04-10
Hi,

Thanks for the reply.

Mine too is 1.2 but there are other versions as well available in /usr/lib/ like libGL.so.1 and libGL.so along with libGL.so.1.2

I am still not clear how to resolve the problem. Pardon my inability to understand.

I tried running the alias command on command line but it did not solve the problem.

Please help further.

Thanks,

Ganesh Bhat.

---

