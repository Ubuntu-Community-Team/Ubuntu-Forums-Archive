---
title: "mounting ext3 drives in 10.10"
date: 2010-11-18
forum: Installation &amp; Upgrades
---

### Post by browolf on 2010-11-18
It seems to be (we have experienced) that 10.10 can't handle having an older ext3 drive mounted to a folder on the 1010 ext4 drive. 
The files get "corrupted", but afterwards,  putting the drive back into the original older 9.04 system, the files are perfectly fine again. 


not sure if this is a bug, a limitation, something we ought to know better not to do, or something else?

---

### Post by psusi on 2010-11-18
What?

---

### Post by sikander3786 on 2010-11-19
> The files get "corrupted", but afterwards, putting the drive back into the original older 9.04 system, the files are perfectly fine again. 

That sounds weird to me.

Only one thing I can suggest is to run a disc scan.

And what type of files are those? Should they be supported under 10.10?

---

### Post by browolf on 2010-11-19
> **sikander3786 said:**
> 
And what type of files are those? Should they be supported under 10.10?

should be. they're image files created by [http://www.fogproject.org/](http://www.fogproject.org/). they're sort of gzip tar files, can be extracted with 7zip in windows.

The whole problem doesn't really matter now. we abandoned the new server we were making and just updated the fog pxe boot kernel in the old server instead.

---

