---
title: "Netatalk broken in Intrepid?"
date: 2008-10-23
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by hizzk on 2008-10-23
Since doing a fresh install from Gutsy to Intrepid, my Leopard-based Macs can no longer connect to netatalk shares hosted on my Ubuntu box.

Some details:
I had been using Gutsy (I had the infamous random freeze issue with Hardy so never upgraded) and netatalk networking worked fine between my macs and my Ubuntu box. When Intrepid hit the first beta at the beginning of the month, I wiped my / partition and did a fresh install. Now, after reinstalling netatalk, I can't connect with my macs anymore. Instead, it fails with this error:

"A volume failed to mount.
The volume "Home Directory" could not be mounted."

Other than the new version of Ubuntu, nothing has changed on my end. Has the netatalk package started using a more finicky version? Is this problem affecting/not affecting anyone else? :confused:

I tried purging the package and installing a deb from Gutsy (since it had worked fine), but the db4.*-util version was apparently incompatible.

Update: I downloaded a deb for the Gutsy version of db4.2 and downgraded to it, then the Gutsy netatalk deb installed just fine. This fixed my issue. I'm now able to connect without any problems. This is probably something that should be examined by the netatalk package maintainer(s).

---

