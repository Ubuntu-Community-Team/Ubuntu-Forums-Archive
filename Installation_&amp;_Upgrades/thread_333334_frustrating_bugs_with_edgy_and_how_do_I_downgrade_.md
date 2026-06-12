---
title: "frustrating bugs with edgy and how do I downgrade back to dapper?"
date: 2007-01-07
forum: Installation &amp; Upgrades
---

### Post by levtar on 2007-01-07
After using Breezy for almost a year with no major hassles (having migrated from longtime use of redhat), I upgraded to Dapper and then Edgy (and am current with updates) using the update manager, and the upgrading process went smoothly.
I only used Dapper for a couple of days, but with no apparent problems. Edgy however has
been a major frustration:

Firefox crashes at many sites (eg Dell online store). On restore, it crashes right away again.
I even tried the latest snapshot from mozilla.org, and still get the same error:
Mozilla Firefox 3.0a2pre, Copyright (c) 1998 - 2007 mozilla.org
The program 'Gecko' received an X Window System error.
This probably reflects a bug in the program.
The error was 'BadMatch (invalid parameter attributes)'.
  (Details: serial 118 error_code 8 request_code 144 minor_code 3)
Epiphany however does not crash at these same sites.

media player doesn't work any more (at least I don't get any sound with firefox)

The date/time setting during bootup doesn't work any more (the boot up screen is almost
dark, so I can't see the actually command and I can't find any date call in
/var/log/messages)

The screen saver blanks out and freezes xwindows 

Can these problems be fixed? If so how? If not, how can I downgrade back to
dapper (ie hopefully without having to erase and do a clean install)

Specs:

firefox -v
Mozilla Firefox 2.0.0.1, Copyright (c) 1998 - 2006 mozilla.org

uname -a:
Linux stardust 2.6.17-10-generic #2 SMP Tue Dec 5 22:28:26 UTC 2006 i686 GNU/Linux
it seems that the recommended generic kernel has SMP even if you don't need it

My desktop is 2-3 years old, with name brand components: Asus A7V266-E mb, ....
Jan  6 22:58:36 localhost kernel: [17179570.984000] CPU0: AMD Athlon(TM) XP1700+
 stepping 02, 

With Breezy, I was hoping that Linux was finally at the point where I could recommend
it to my none computer geek friends. Edgy seems to be a major fall back. How can an
upgrade on an older mainstream machine cause so many problems?

In Frustration,

Lev

---

### Post by Gen2ly on 2007-01-07
something with firefox, I got the same error

---

### Post by sdowney717 on 2007-01-07
I find my Xwindows wont come up half the time. Just get a blank screen.

I have also been using Fedora Core 6, and I would reccomend it to all. So far no problems.

---

### Post by ag65151 on 2007-10-23
BUMP as I have just encountered this same problem with Gutsy (7.10)

Has anyone seen this before? I have been tweeking my xorg.conf all day and it has made absolutely no difference.

---

