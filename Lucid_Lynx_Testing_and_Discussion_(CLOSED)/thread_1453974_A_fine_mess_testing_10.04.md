---
title: "A fine mess testing 10.04"
date: 2010-04-14
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by A_Nonny_Moose on 2010-04-14
For the last two or three days I have been testing the new beta release.  I have now reached an impasse, and this is what happened:
[LIST=1]
[*]I installaed the CD and everything came up (sort of) :)
[*]I tried installing the extensions for my graphics card (nvidia-96) as per prompts.  Refused because it couldn't find /dev/null
[*]To my annoyance, /dev/null was right where it should be.  So I did a general update and then:
[*]I got the same warning, but the module **was** installed.:lolflag:
[*]Somewhere in there, there was a hiccup, because when I did a restart **gdm** got into a time-out loop and I couldn't log on to an X11 session. :rolleyes:
[*]So I got into the system by going to the command prompt and changed the root password so I could get things done without typing **sudo** all the time.:(
[*]I logged into root, and floundered around for a while.  Then:
[*]I tried running** Xorg -configure** which promptly told me I had too many screens, and failed.  This, of course, clobbered my configuration.:mad:
[*]When I looked at my 9.10 **Xorg** configuration file, which was OK, it seemed to me that I could copy this into the new instance, so I did.:eek:
[*]Now the system boots to the login screen in **gdm**, but this gets into some funny time-out and I can't log in, even when the account I want has _no password necessary_ permissions. :confused: **gdm** just loops on the login screen.
[*]Help!?
[/LIST]

P.S.  This even happens when I start **gdm** from the root terminal.  I am not good enough with this O/S to diagnose this further, mostly because there is either no or too much instrumentation and I have no tools to process the log files that I am aware of.

---

### Post by uRock on 2010-04-14
Hey Moose,
Thanx for testing it.

I hope you filed bug reports.

Did you MD5SUM and run check disk before installing?

Cheers,
Ronnie

---

### Post by Bobhuber on 2010-04-14
Don't feel lonely.I have spent hours trying to get Lucid working with Nvidia with a fresh install and (or) an upgrade on a 64bit system.I've filed a couple of bug reports and did research on several that had already been filed.Not happy at all with what I found in the status reports and comments from the developers themselves.

---

### Post by nss0000 on 2010-04-14
> **Bobhuber said:**
> Don't feel lonely.I have spent hours trying to get Lucid working with Nvidia with a fresh install and (or) an upgrade on a 64bit system.I've filed a couple of bug reports and did research on several that had already been filed.Not happy at all with what I found in the status reports and comments from the developers themselves.

Humm ... on a recent clean install x64-LL_10.04 automagically configured the "native" NV 195.xxx driver for my BFG.9800gtx+ vidcard & Hanns 28" monitor. Looks great.

It may have taken a couple of <juju> update" cycles after installing the "burned" beta_2 , but I'm sure I did nothing reasonable to help it along.

---

### Post by uRock on 2010-04-14
I use the Nouveau driver, works like a charm.

---

### Post by Mark Phelps on 2010-04-14
> **A_Nonny_Moose said:**
> For the last two or three days I have been testing the new beta release.  I have now reached an impasse, and this is what happened:

Have you checked in the beta testing forum to see if any of these issues were documented and/or corrected?  That's where such stuff will be posted, not here in the General forum.

The beta testing forum is Development & Programming, Lucid Lynx Testing.

---

### Post by jrothwell97 on 2010-04-14
The nvidia-96 driver crashing GDM is a [known bug (#553200)](https://bugs.launchpad.net/bugs/553200).

At present, there are three workarounds:

[list][*]Temporarily enable automatic login (you can do this by editing /etc/gdm/custom.conf)
[*]On boot, change to a tty, log in, stop GDM and then start X manually.
[*]Switch back to Nouveau.[/list]

It appears to be an upstream bug at present, so there's little we can do until it gets fixed :(

---

### Post by Half-Left on 2010-04-14
> **jrothwell97 said:**
> The nvidia-96 driver crashing GDM is a [known bug (#553200)](https://bugs.launchpad.net/bugs/553200).


It appears to be an upstream bug at present, so there's little we can do until it gets fixed :(

Other than send a patch or fix it yourself and then send it upstream.

---

### Post by jrothwell97 on 2010-04-14
> **Half-Left said:**
> Other than send a patch or fix it yourself and then send it upstream.

...except that it's in the binary (i.e. proprietary) driver, so we can't, even if we were suitably well-equipped and had the necessary programming skills (which I certainly don't.)

---

### Post by Half-Left on 2010-04-14
> **jrothwell97 said:**
> ...except that it's in the binary (i.e. proprietary) driver, so we can't, even if we were suitably well-equipped and had the necessary programming skills (which I certainly don't.)

I didn't look at the report so I assumed it was a GDM bug. IF it's a proprietary bug then fine, there is not much more you can do.

---

