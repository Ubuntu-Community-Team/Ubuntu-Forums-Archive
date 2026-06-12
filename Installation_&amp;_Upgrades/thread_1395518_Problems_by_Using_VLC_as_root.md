---
title: "Problems by Using VLC as root"
date: 2010-01-31
forum: Installation &amp; Upgrades
---

### Post by rashid-bhitai on 2010-01-31
Hi,
today I have installed VLC on my Ubuntu Karmic Koala, and when i want to run it i gets this error [U][I][B]vlc: error while loading shared libraries: libvlccore.so.0: cannot open shared object file: No such file or directory
[/B][/I][/U] how can I slove this Problem?

and I have some Audio problems with my user account how can I solve that one? should I start a new thread? or you can give me a solution here too ?

with best regards,
Shahzad

---

### Post by stoneage on 2010-02-01
Did you check to see whether libvlccore is installed? It is a vlc dependency, so it should be there.....


EDIT - I just tried > sudo vlc and got this:-
> VLC is not supposed to be run as root. Sorry.
If you need to use real-time priorities and/or privileged TCP ports
you can use vlc-wrapper (make sure it is Set-UID root and
cannot be run by non-trusted users first).

---

### Post by SuperSonic4 on 2010-02-01
What version of VLC do you have? I ask because your title mentions the root account but you only get root access if you enable it yourself. 

Perhaps uninstalling and reinstalling will pay off?

---

