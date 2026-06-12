---
title: "How does one add programs from a usb stick?"
date: 2008-01-11
forum: Installation &amp; Upgrades
---

### Post by natehall on 2008-01-11
. Is there a way to get a package manager to grab a tarball off of a USB stick and then install it?

---

### Post by nikoPSK on 2008-01-12
Not really. There was a program I saw a while back but have since forgotten. All you really need to do is bring along the tar file or deb and install it as usual. That should be fine for you I hope. :KS

---

### Post by Herman on 2008-01-12
I like to copy all the .deb packages from the /var/cache/apt/archives directory in a computer I have installed and updated and added software to. I move all those .deb packages to the next computer and copy them into the /var/cache/apt/archives in that one. That way providing each computer all has the same Ubuntu, they don't need to re-download the same packages again for each computer I'm installing in. They just install them.

I'm talking about genuine Ubuntu .deb packages from the official Ubuntu repositories only, if your tarball if from some foreign source then I don't know. 
I wouldn't recommend installing any software that doesn;t come from the official Ubuntu repositories.
I suppose people have their certain special wants and needs, it's up to you.

You can also use dpkg, I have done that before, but again, only for official Ubuntu packages, here's a link, [Back-up and Restore Added Software]("http://users.bigpond.net.au/hermanzone/p13.htm#Back-up_and_Restore_Added_Software")

Regards, Herman :)

---

