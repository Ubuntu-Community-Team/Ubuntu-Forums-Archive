---
title: "Silc support in Ubuntu: From Bad to Worse"
date: 2006-10-26
forum: Installation &amp; Upgrades
---

### Post by agent8131 on 2006-10-26
Upgraded to Edgy this morning.  I'm mostly impressed with the changes but the real sore spot for me is silc support which I thought was supposed to be fixed in Edgy.  I rely on silc to communicate with work clients so an OS that does not have good silc clients is almost unusable for me.  And it's sad that Windows should be so much better in this regard.  Anyway, my experience:

Dapper:
Silky - worked
Gaim - silc support could be enabled by adding a library file

Edgy:
Silky - doesn't work
Gaim - silc support is totally compiled out, my silc accounts show up as Unknown protocol, I may be compiling gaim myself and if so I'll let others know how to get it working.

Here's what happens when I run silky:

# silky 
GTK Accessibility Module initialized

** ERROR **: Silky needs threads!

aborting...
Aborted (core dumped)

---

### Post by agent8131 on 2006-10-28
So I think all that is needed to fix gaim is to add libsilc-1.0-2-dev to the build dependencies.  Here's what I did to get it working.

Make source I had an apt-src line in my /etc/apt/sources.list

sudo apt-get source gaim
sudo apt-get build-dep gaim
sudo apt-get install libsilc-1.0-2-dev
cd gaim-2.0.0+beta3.1
./configure
make
sudo make install

Then run gaim from /usr/local/bin/gaim and silc support seems fine so far.

I also did some work on silky but nothing worked.  I used strace to try and find if there was a missing thread library but I didn't come across anything.  I'd suggest upgrading the package to 0.5.4 and testing.  I prefer gaim to silky but it's good to have a backup client that works.

---

### Post by jcsteele on 2006-11-04
I recently had this problem, but the SILC Project provides a deb package at 
[http://silcnet.org/download/client/deb/1.0.1/silc-client_1.0.1-1_i386.deb](http://silcnet.org/download/client/deb/1.0.1/silc-client_1.0.1-1_i386.deb)
that works with edgy with no problems.

---

### Post by mattshow on 2007-01-14
This thread is a bit old now, but just in case someone stumbles across it and is having this same problem:

The problem, at least with the GAIM plugin, seems to have something to do with Debian's libsilc package being "broken"
[https://launchpad.net/ubuntu/+source/gaim/+bug/44728](https://launchpad.net/ubuntu/+source/gaim/+bug/44728)

I would imagine Silky depends on those same libraries, although I don't know that that accounts for the problem you're having with it.

---

### Post by agent8131 on 2007-01-16
jcsteele: Sure I keep silc-client installed, but how many users are really going to choose a command line interface?

mattshow: Given my solution above which requires the libsilc-1.0-2-dev it stands to reason that the package works fine.

The bottom line is the gaim package is trivial to fix but no one has done so (despite it being listed, at one point, as a goal for edgy).  No one seems to care enough to investigate why silky is complaining about not having threads.  The solution to fixing gaim might require nothing more than adding libsilc-1.0-2-dev to the build-dependencies for the gaim package.  That's a 3 second change and probably 10 minutes of testing to give some sort of decent silc support to edgy.

Note that I came across this thread again when a friend of mine was asking about ubuntu silc support and I decided to search google to see if anyone had done anything yet.  Apparently not...

---

### Post by pss on 2007-03-17
> The bottom line is the gaim package is trivial to fix but no one has done so (despite it being listed, > at one point, as a goal for edgy).  

Your method of compiling from source worked for me, thanks.  Perhaps an update will have silc support built-in for gaim.

---

