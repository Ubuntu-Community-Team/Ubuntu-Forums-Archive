---
title: "dbus/karmic/konqueror bug?"
date: 2009-10-12
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by chitowner2 on 2009-10-12
Hello All;

I am not sure what prefix to use for this, so I will just describe...

SYSTEM
AMD2, dual core, 8Gb RAM, recent upgrade to karmic-beta over jaunty. Other details if asked.

PROBLEM
dbus-daemon as seen in "top" from shell goes to 100% CPU and stays there; over 40 minutes as of now. GKRELLM confirms this for core-0. Activity on core-1 is minimal, but system is essentially locked up. 

BACKGROUND
I think this *may* be due to an overload (?!) of system resources due to too many instances of konqueror, which I use as both a file browser and web browser. 

At any given time I normally have about ten konq windows open with several tabs in each. When I get to about 10 tabs, I usually open a new window, but I try to keep a "thread" restricted to a single window. I also typically have a number of FireFox windows open at the same time. All this is in addition to a variety of other apps that may be concurrently running, although that can be set aside for the current problem since I have done a hard reboot twice and no other apps besides a couple of kterminal windows and gkrellm are running.

What precipitated the hang on dbus *may* have been a bad web page, although at this time I have no way of confirming that.

Note to any **developers** viewing this: Could we please have a way to step through individual konqueror window logs instead of them ALL trying to load at once when doing a recovery?

When I allow the recovery to start, it initially loaded twelve konq windows and dbus pegged the CPU. Now on the third attempt, recovery is trying to load thirty six windows!!! :-\"  ](*,)

I have copied the /tmp/kde-user folder to another location, so that data has been be preserved. There is a zip file in there (!) which I have never observed occur before. 

Any suggestions on how to deal with this? Is this a bug or am I just overtaxing the system?

Go ahead; jump in folks.
CT
:confused:

---

### Post by chitowner2 on 2009-10-15
Bump!

---

