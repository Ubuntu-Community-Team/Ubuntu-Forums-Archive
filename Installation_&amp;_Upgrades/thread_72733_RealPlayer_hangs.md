---
title: "RealPlayer hangs"
date: 2005-10-07
forum: Installation &amp; Upgrades
---

### Post by sleightholme on 2005-10-07
I installed RealPlay 10 using the sudo option - no reported problems.
However, when I execute it from the menu it does not start, when I execute from command line it hangs, and when I try and play a radio show from Firefox or SeaMonkey it just goes very slow and I have to abort it.

To try and determine the issue, I installed Helix itself which starts up fine, I just can't use it to play radio files - won't allow me to.

The sound card / speaker works fine for CDs and event sounds.


Any ideas ?

---

### Post by Snocrash on 2005-10-07
Have the same issue with my Dell laptop. It seems to be an issue with the sound card module (i810audio) and esd. Try shutting off the sound server in Gnome. This did the trick for me.

Realplayer worked fine in my desktop with a SBLive and the sound server turned on.

-Sno

---

### Post by sleightholme on 2005-10-07
Excellent - oodles of thanks.

Disabled the Gnome sound serer at startup worked.


I can now listen to radio over the Internet.



Chris

---

