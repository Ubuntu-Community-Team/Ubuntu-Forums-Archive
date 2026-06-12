---
title: "K3B - Verify Written Data... locking up??"
date: 2008-10-29
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by Roasted on 2008-10-29
Every time I try to verify written data on K3B, it locks up K3B all together. I'm running Intrepid Beta 64 bit. I'm not sure if this is related to the OS or not, but I remember running the verify written data before without any issues on Hardy, but that may have been 32 bit Hardy.

Anybody else run into this?

---

### Post by 4Orbs on 2008-10-29
I had that problem on my 32 bit install, plus a few other issues with K3B. Re-installing K3B seems to have fixed everything except the auto-eject / auto-close race.

---

### Post by Roasted on 2008-10-29
> **4Orbs said:**
> I had that problem on my 32 bit install, plus a few other issues with K3B. Re-installing K3B seems to have fixed everything except the auto-eject / auto-close race.

Hahaha, I noticed that too. Is there no fix for the auto-close thing? 

I wonder what happens to it exactly that would cause a reinstall to fix the issues... considering I only installed it about 3 days ago and all.

---

### Post by 4Orbs on 2008-10-29
I can only guess as to why the reinstall fixed mine. I think that K3B didn't correctly recognize my 2 optical drives, and after I burnt a cd on the slave drive, it would try to verify the write from the master drive which was empty. Now it works ok. First it hashes out the md5sum, then burns, then verifies. All very smoothly.

---

### Post by alienexplorers on 2008-10-29
I have the same problem with verify in K3B.  I also have the problem with the door closing by itself.  If anyone has a fix please let us know.

---

### Post by Roasted on 2008-10-29
> **alienexplorers said:**
> I have the same problem with verify in K3B.  I also have the problem with the door closing by itself.  If anyone has a fix please let us know.

Have you reinstalled? I haven't tried it yet, but I'm curious if reinstalling for you fixes it.

---

