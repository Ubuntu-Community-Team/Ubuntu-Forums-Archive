---
title: "I cant install yelp-dbgsym because of dependencies"
date: 2008-10-22
forum: Installation &amp; Upgrades
---

### Post by madsc89 on 2008-10-22
I am trying to perform a backtrace, but I can't install yelp-dbgsym!

When I try to mark it for installation in synaptic, I get this message: "The following packages have unresolvable dependencies. Make sure that all the required repositories are added and enabled in the preferences.
yelp-dbgsym:
  Depends: yelp (=2.22.1-0ubuntu2) but 2.22.1-0ubuntu2.8.04.3 is to be installed"

All repos are enabled.

When I then try to force yelp (=2.22.1-0ubuntu2), I have to mark the following for removal:

firefox, firefox-3.0, firefox-3.0-gnome-support, firefox-gnome-support, gnome-user-guide, sun-java6-plugin, ubufox, ubuntu-docs, xulrunner-1.9, xulrunner-1.9-gnome-support.

It is obvious I don't want to remove those. So then I'm stuck.

How can I install yelp-dbgsym or something equal?

Thank you.


EDIT: I followed this guide: [https://wiki.ubuntu.com/DebuggingProgramCrash](https://wiki.ubuntu.com/DebuggingProgramCrash)

---

### Post by Acetylene30 on 2008-10-22
I am also having this exact problem, i just want to make sure i can run valgrind without a SIGSEGV happening on valgrind itself.

---

