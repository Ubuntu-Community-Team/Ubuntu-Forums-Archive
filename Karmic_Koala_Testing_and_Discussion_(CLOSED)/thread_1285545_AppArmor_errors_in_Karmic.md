---
title: "AppArmor errors in Karmic"
date: 2009-10-07
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by rookcifer on 2009-10-07
I am attempting to profile a few apps in Karmic and I am running into some difficulty.  Perhaps something has changed with AppArmor since Jaunty?

At any rate, I typically use the "genprof" command to begin profiling an app and then use aa-logprof to edit the profile to my liking.  This doesn't seem to be working with Karmic.  After generating a profile and editing it, I get the following error if I try to put it into enforce mode:

> /sbin/apparmor_parser: cannot use or update cache, disable, or force-complain via stdin
Found reference to variable HOME, but is never declared

I noticed that the abstraction #include <tunables/global> was not appended automatically to my generated profiles, so I added the line and it then allows me to put the profile into enforce mode with no errors.  However, if I try to run aa-logprof again, it provides me the same log file complaints that it did previously. If I go through and select the options I want, I notice that it removes the "tunables/global" abstraction and I get the above quoted error again.  This happens even if I reboot.  It's like a cycle that can't be broken.

So, I wonder is there something I should be aware of that changed since Jaunty?  Anyone else having these errors?  I wanted to check here before I filed a bug -- just to make sure I wasn't doing something wrong.

---

### Post by rookcifer on 2009-10-15
Bump.  

Anyone else having issues with creating AppArmor profiles in Karmic?  No matter what I do, I cannot create a profile using aa-genprof.  The profile itself will create but I cannot modify it by using "aa-logprof."  Nothing will stick no matter what I do.

---

