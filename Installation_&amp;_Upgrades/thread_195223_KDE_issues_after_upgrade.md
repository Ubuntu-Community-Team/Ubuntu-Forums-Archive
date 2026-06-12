---
title: "KDE issues after upgrade"
date: 2006-06-12
forum: Installation &amp; Upgrades
---

### Post by nitro322 on 2006-06-12
I had significant issues with Kubuntu when upgrading from 5.10 to 6.0.6 (KDE and desktop apps completely removed, wrong kernel installed, X wouldn't start at all, etc.), but I have almost everything fixed now.  Clean upgrade it was not, so if anyone is counting you can add me to the list of people that have reported extreme difficulties during the upgrade process.  Note:  I'm not complaining, just want to be clear that I also encountered many of the issues that I've seen others report.

I'm also experiencing a separate issue that I haven't seen discussed yet.  After getting KDE reinstalled and my kernel and Xorg issues resolved, I'm still unable to login to KDE through KDM.  Immediately after authenticating, X will close altogether and KDM will be restarted.  I checked the logs and couldn't find any indication of errors.

I tried starting X using a few different methods, and here's my results:

KDM -> KDE - fails; KDM immediately restarts
KDM -> failsafe - succeeds; can then run startkde and load KDE
no KDM -> startx (no .xinitrc) - fails; X loads them immediately exits
no KDM -> startx (.xinitrc "exec startkde") - succeeds

None of the methods that work are convenient to use on a regular basis, and in addition none of the helper scripts in /etc/X11/Xsession.d/ are run with these methods (so, for example, mouse wheel scrolling doesn't work).

Can anyone offer suggestions to fix this?  Or has anyone else even heard of it?  I'm completely out of ideas at this point.  I can provide any additional information if requested.

Thanks.

---

