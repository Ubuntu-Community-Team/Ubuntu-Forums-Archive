---
title: "natty -&gt; oneirc, firefox+thunderbird broken after upgrade"
date: 2011-11-16
forum: Installation &amp; Upgrades
---

### Post by jafox on 2011-11-16
After doing an upgrade from natty to oneirc, firefox+thunderbird have issues crashing on start, display random asian characters, and generally aren't happy.

Things tried:
1. upgrading to firefox-next, thunderbird-next (nope)
2. moving the old profile dirs and starting with blank (nope)
4. running env -i and then starting ff/tb from that shell (nope)
5. ran locale-gen / etc
6. removed any exotic ttf packages i found (long shot, and nope)
7. searching the internets (nope)

What does work
Trying a firefox 3 binary build from mozilla.org (this works)
Chrome from google's repo

I've downgraded back to oneiric versions of both, and tried all test cases (moved .moz* etc, started clean, cleaned env).

Attached is a screen of the fail. Notice the small issues with the decorations on the tab and in the navbar as well.

---

### Post by jafox on 2011-11-17
Fun finding. I ssh'd in from a natty machine and launched thunderbird/firefox. They seem to run fine and display property on the natty machine.


This issue is officially mind-bottling.

---

### Post by jafox on 2011-11-17
Okay, tunneling X through ssh was not working. It just took longer to see the bug.

Also, pidgin seems to be sending people blank lines often instead of my messages.... possibly related in some weird way?

---

### Post by jafox on 2011-11-17
I added natty repos to my sources, apt-get purged tbird, apt-get -t natty install --no-install-recommends thunderbird, now tbird works.

Le sigh. My problem is "fixed" but I haven't really fixed the problem.

---

### Post by jafox on 2011-12-05
Just did a Natty clean install. And get the same problem out of the box with a clean home dir and Firefox 8 (ubuntu security). I am starting to think my computer is cursed. Ran memtest and it came back clean.

---

