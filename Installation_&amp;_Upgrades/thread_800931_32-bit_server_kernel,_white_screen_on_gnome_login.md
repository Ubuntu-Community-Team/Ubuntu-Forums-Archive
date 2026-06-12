---
title: "32-bit server kernel, white screen on gnome login"
date: 2008-05-20
forum: Installation &amp; Upgrades
---

### Post by wastedfluid on 2008-05-20
Hi guys.

Trying to run a 32-bit server kernel(-17) so I can access all 4gb of ram.

When I login, i just get a "WHITE" Screen.. but I CAN see the login manager.

If I login Gnome Troubleshoot(or whatever its called) - i can successfully login, though.

I'm thinking it's a firmware issue, or a video card issue.. so my question is, how do I link all of my firmware, and video drivers to the 32-bit -17 server kernel??

Thanks!!

*Edit*

Meant to put,  I have the -17 generic kernel, and it boots fine!!

Many thanks

---

### Post by wastedfluid on 2008-05-20
Hate to do it, but bump.

---

### Post by wastedfluid on 2008-05-21
Well, I have figured this out myself.

The problem was, fglrx was proprietary - and I didn't install the entire kernel package.  After uninstalling fglrx, I could boot to the -server kernel.. then I just installed the -17-server restricted headers package, and re-installed all proprietary drivers - and it wah-la.  It worked like a charm. 

Now I'm using all 4gb of my RAM on a 32-bit install.  Toodaloo.

---

