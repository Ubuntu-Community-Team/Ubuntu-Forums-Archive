---
title: "Installing ubuntu on new build - does it take long?"
date: 2009-12-10
forum: Installation &amp; Upgrades
---

### Post by PaulStat on 2009-12-10
Hi Folks,

Right, I finally managed to assemble the computer and everything seems to be working. I've made a ubuntu boot CD (9.10), selected the CD drive to boot first (HD second) and then selected "Install ubuntu". What supposed to happen then? And how long does it take?

It goes to a screen with a ubuntu logo fading in and out, whilst the light on the cd drive flickers away for what seems like aaaaagggges.

So should it be going to an install screen pretty quickly after this?

Cheers,
Paul

---

### Post by PaulStat on 2009-12-10
Ok now it just keeps saying

"Buffer I/O error on device sr0"

What does that mean? It's a new HD so it hasn't been formatted or anything, but I thought that would be part of the installation process

---

### Post by QIII on 2009-12-10
It should go immediately to the installation.

Did you check the md5sum to be sure you got the .iso right?

On the start up screen did you try "Check disk for errors"?

Did you try "Run Ubuntu without making changes to your computer" to be sure all was compatible?

---

### Post by QIII on 2009-12-10
Your error appears to indicate a problem on the optical drive.

If the drive is new, it's probably not the drive itself.

Do the checks I suggested above.

If the original .iso you downloaded is good on the md5sum, you may need to burn your .iso to CD at a slower rate.

When you get it there, check the md5sum on the cd and do the rest of the checks again.

---

### Post by markbuntu on 2009-12-10
I had a similar problem with a samsung PATA (EIDE) DVD writer. The samsung SATA DVD drive worked fine though. They are basically the same cheap $25 drive just one is PATA and the other is SATA. I had no problems with previous releases in either drive so it was sort of weird.

But anyway, install should take about 20 minutes start to finish, maybe a little longer to format a large hard drive initially.

---

### Post by blur xc on 2009-12-10
I had issues w/ my disk as well.  After a couple of failed attempts, I finally burned a new cd w/the burner set on its slowest speed and it took.  Installing Ubuntu was WAY easier and faster than Vista.  Plus w/ windows, after the OS is installed, then comes all the cd's w/ drivers that came with all your hardware.  Ubuntu takes care of itself for the most part, as long as you picked good hardware compatible w/ Linux.

BM

---

