---
title: "Having issues updating"
date: 2012-10-28
forum: Installation &amp; Upgrades
---

### Post by unknown user on 2012-10-28
I have been able to receive updates as usual. They come up, tell me that I have updates and then I can download them as normal. 

However, when I try to go to the Update Manager and then click Check, I get the following error message - 

Failed to download repository information

Check your Internet connection.

Details:
[I][COLOR="Red"]W:Failed to fetch [http://ppa.launchpad.net/zedtux/rhythmbox-albumartsearch/ubuntu/dists/oneiric/main/source/Sources](http://ppa.launchpad.net/zedtux/rhythmbox-albumartsearch/ubuntu/dists/oneiric/main/source/Sources)  404  Not Found
, W:Failed to fetch [http://ppa.launchpad.net/zedtux/rhythmbox-albumartsearch/ubuntu/dists/oneiric/main/binary-amd64/Packages](http://ppa.launchpad.net/zedtux/rhythmbox-albumartsearch/ubuntu/dists/oneiric/main/binary-amd64/Packages)  404  Not Found
, W:Failed to fetch [http://ppa.launchpad.net/zedtux/rhythmbox-albumartsearch/ubuntu/dists/oneiric/main/binary-i386/Packages](http://ppa.launchpad.net/zedtux/rhythmbox-albumartsearch/ubuntu/dists/oneiric/main/binary-i386/Packages)  404  Not Found
, E:Some index files failed to download. They have been ignored, or old ones used instead.[/COLOR][/I]

Is this something to worry about, or is there a way of getting the message to go away?

---

### Post by Frogs Hair on 2012-10-28
It looks like there have been no builds for that PPA for 107 weeks . You can continue to use the application without the update error by opening software sources > other software and removing the source. There may be two lines to remove.

After removing the source run the update manager . I think it is safe to write the PPA    your using is dead or at least  on hold.

---

### Post by unknown user on 2012-10-30
Thanks for that. Oh gosh not Rhythmbox.. That is the one that I found was good for the ipod update.

---

