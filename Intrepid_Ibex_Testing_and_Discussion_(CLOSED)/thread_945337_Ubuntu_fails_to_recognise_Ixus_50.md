---
title: "Ubuntu fails to recognise Ixus 50"
date: 2008-10-12
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by bash on 2008-10-12
When I try to plug in my Canon Ixus 50 camera I just recieve an error:

"Error while initialising camera: -1: unspecified error"

Any ideas? Don't even know what package I should file the bug against.

---

### Post by bash on 2008-10-12
No one else has any issues connecting their cameras?

---

### Post by Jove on 2008-10-12
I had a wee problem with my Ixus 70 and this fixed it:

[https://bugs.launchpad.net/ubuntu/+source/libgphoto2/+bug/267238](https://bugs.launchpad.net/ubuntu/+source/libgphoto2/+bug/267238)

Dunno if it's the same issue as you're having, but worth a bash (excuse pun)

---

### Post by bash on 2008-10-15
Thanks for the link. I'll give it a try when I'm get to my other machine. I have the hope that the latest F-Spot might might solve the issue. 

From the change notes it sounds like that might have caused the isseu:

> f-spot (0.5.0.2-0ubuntu2) intrepid; urgency=low

[list][*]Drop ubuntu_import_fuse.dpatch again, it was a quick fix for beta. It causes f-spot to be utterly slow due to now really knowing that the fuse directory is actually a slow libgphoto link. gvfs was changed to not automount the camera any more, thus F-spot, gthumb, and friends will just continue to directly talk to the camera.[/list]

 -- Martin Pitt <email address hidden>   Wed, 15 Oct 2008 13:06:34 +0200

---

