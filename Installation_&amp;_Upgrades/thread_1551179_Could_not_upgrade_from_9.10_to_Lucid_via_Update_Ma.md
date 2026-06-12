---
title: "Could not upgrade from 9.10 to Lucid via Update Manager"
date: 2010-08-12
forum: Installation &amp; Upgrades
---

### Post by oldpath on 2010-08-12
W:Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/lucid-backports/Release](http://us.archive.ubuntu.com/ubuntu/dists/lucid-backports/Release)  Unable to find expected entry  main/debian-installer/binary-i386/Packages in Meta-index file (malformed Release file?)
, E:Some index files failed to download, they have been ignored, or old ones used instead.

I recently upgraded from Jaunty to 9.10 Karmic Koala and there were no glitches.  I got brave and tried to upgrade via the Update Manager and got the above error msg.  I have read back 12 pages and saw several things that can go wrong by going this route.  
 
So, maybe, I am lucky the upgrade did not go.  Who knows.  Maybe I should be happy to have a working 9.10 system at this point and live with it until I am fully prepared to do a clean install.  Does that make more sense than what I tried to do?

If the above error msg is not an easy fix I will just live with Karmic for the time being.  I am glad I read back a ways to see what else has happened.  That is the reason I am not real motivated to do this upgrade now. 

Thanks for any advice in a general way.  I just wonder if this error msg might be a blessing at this point.

oldpath

---

### Post by dino99 on 2010-08-12
before updating/upgrading, clean your system:

- check synaptic repo tab: remove/deactivate all third party and ppa
- update all repo to "lucid"

into console: sudo apt-get clean ... autoclean ... autoremove

then you can update and safe-upgrade

---

### Post by oldpath on 2010-08-12
Thanks Dino99.
   I will try your suggestions and see if it works.  I have a few third party apps in there somewhere.

I would like to close this thread as solved.  How do I do that?

---

### Post by Frogs Hair on 2010-08-12
> **oldpath said:**
> Thanks Dino99.
   I will try your suggestions and see if it works.  I have a few third party apps in there somewhere.

I would like to close this thread as solved.  How do I do that?

Thread Tools  on the top right.

---

### Post by Annigma on 2010-08-19
> **oldpath said:**
> Thanks Dino99.
   I will try your suggestions and see if it works.  I have a few third party apps in there somewhere.

I would like to close this thread as solved.  How do I do that?

Did it work?
I'm tempted to use update manager to go from Karmic to 10.04.1 LTS, but having tried that route once before (from Feisty I think..) I'm wary..
I've waited till .1 came out as I read somewhere it's safer..

If it worked for you, I'll have a go at following dino's instructions.

Thanks

---

