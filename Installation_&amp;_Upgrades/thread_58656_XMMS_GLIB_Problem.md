---
title: "XMMS GLIB Problem"
date: 2005-08-21
forum: Installation &amp; Upgrades
---

### Post by tehsyco on 2005-08-21
*** The glib-config script installed by GLIB could not be found
*** If GLIB was installed in PREFIX, make sure PREFIX/bin is in
*** your path, or set the GLIB_CONFIG environment variable to the
*** full path to glib-config.
configure: error: *** GLIB >= 1.2.2 not installed - please install first ***

I've read some various things on this but was not able to find anything that worked/was helpful. Please advise, thanks!!!

Jordan

---

### Post by BigDeal on 2006-03-18
I have the same problem with GLIB ang XMMS. Is there a link to explain why ?

---

### Post by steve196 on 2006-03-28
I just had the same problem.
It wants the libglib dev package. It will want the xmms dev package too

---

### Post by blissfulpenguin on 2006-04-02
Well, I'm having a similar problem.  I am trying to compile glib 2.6.5 and I take the tarball, -xzzvf it and configure it, make and make install it.  Everything goes off without a hitch.  Then I go to configure the gtk source code, and it says the current version of glib is 2.6.3, but the header refers to 2.6.5, and I'm completely stumped!

I've tried downloading other source codes for glib, but I am getting the same error message.  Using the output, I ran ldconfig, to no effect as far as I know.  Honestly, I don't know what I'm doing.  I'm just being pragmatic.  Could somebody throw me a line here?

---

### Post by www-empty on 2006-11-25
I'm having the same happen. I believe we need to download the development packages for glib. If you use synaptic package manager, they're marked with a -dev after them. Give that a try. It's what I'm going to do.

---

