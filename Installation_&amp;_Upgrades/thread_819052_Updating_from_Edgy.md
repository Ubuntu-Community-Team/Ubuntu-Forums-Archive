---
title: "Updating from Edgy"
date: 2008-06-05
forum: Installation &amp; Upgrades
---

### Post by bjcosta on 2008-06-05
Hi all,

I have an Edgy system that i need to install postgres and some associated tools on. It seems that the edgy repositories have disappeared...

so: apt-get update fails and i also cant install the packages i want to. So i figured, i guess that means they want me to upgrade my system.

I looked at the repository sites in my browser and the newer dists exist there but not the edgy ones anymore.

It seems that without the old repositories the upgrade also fails. If i run the upgrade tool from the GUI (or from the command line), it gets to the preparing to update stage, but because the sources in my sources.list file no longer exist (I think they were removed a few months ago) it doesn't get any further.

Failed to fetch [http://security.ubuntu.com/ubuntu/dists/edgy-security/main/binary-i386/Packages.gz](http://security.ubuntu.com/ubuntu/dists/edgy-security/main/binary-i386/Packages.gz) 404 Not Found
Failed to fetch 
..... more similar errors ......

and the update bombs out.

Is there somewhere i can point my sources.list that still has the packages and will continue to keep them, or if not how can i go about updating to fiesty, or gusty with this now broken system?

Also as a side note. I use this system for development at work. I need to keep a relatively stable system and not have to keep upgrading packages to new versions when they just come out. If i want to keep an old system is there any way of doing that short of mirroring all the packages locally or bypassing apt-get for that software/libraries altogether?

Thanks,
Brendon.

---

### Post by Bubba64 on 2008-06-05
You probably can install Feisty, Gutsy, or Hardy, your best bet is to back up whatever you need, and do a fresh install using a daily ISO, I found a Feisty ISO I assume that it is still accessible but I am not sure of the length of support on this distribution or Gutsy, but Hardy is a long term support release. If it was me I would be concerned that whatever I save can be opened in the new program, I have on occasion seen posts regarding this but I think it is not common. You should get more posts that will be more helpful.

---

### Post by bjcosta on 2008-06-06
Yes. I am trying to avoid having to do a fresh install. It may be my only option in the end, but for the moment i have downloaded the source code for the items i need and built + installed them manually. So they are in /usr/local I would prefer to find a way of properly upgrading my system using apt-get or similar though.

If that is not possible then i guess i will start a fresh install in a month when i have finished this new project.

Thanks for the quick reply. 

What is interesting though is that the dapper distribution seems to be available but edgy is not. Was edgy a non-supported/non-stable release?

---

