---
title: "Upgrades for internal networked machines"
date: 2008-12-02
forum: Installation &amp; Upgrades
---

### Post by MaindotC on 2008-12-02
I have to set up some Linux machines (and I'm using Ubuntu) to form a closed network that will not be able to access Internet services, namely Ubuntu repositories.  Our instructor has made it very clear that he does not want our lab machines connected to the campus (production) network so I am not allowed to connect the machines to download updates, system patches, or packages.

I realize that I can set up my own repository and just direct all the Ubuntu machines on the closed network to search for packages at that repository's address.  I can download all the .deb's that are available in all repositories, and put them on the closed-network repository if I desire.  I get that.

But what about updates?  Are they just deb files and if so, how do I distinguish them from all other .deb's so I can download them onto a flash drive and move them to the closed-network repository?

---

### Post by wilbbe01 on 2008-12-02
apt-mirror might be of interest to you.  It could mirror the real repositories you wanted it to.  You could make that machine accessible to the internet, allowing other machines to access it, but not anything else on the local network.  Maybe, I don't know, just a thought.

---

### Post by MaindotC on 2008-12-02
Thanks for the suggestion.  The machine cannot in any way be physically connected to the production network so what I have to do is download the packages and then move them to the repo on a flash drive.

---

