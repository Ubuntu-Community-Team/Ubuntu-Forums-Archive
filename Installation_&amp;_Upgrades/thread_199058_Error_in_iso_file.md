---
title: "Error in iso file ?"
date: 2006-06-18
forum: Installation &amp; Upgrades
---

### Post by mattiashem on 2006-06-18
I have downloaded now 3 different iso files to try to install Xubuntu but every disk that i burn have errors.
The installitions stops after 6 % and then complain that a file i missing.

And a get the same error om every computer a tried it on.

I you run a check of the cd rom when you boot from it a also get an error.

So are the Iso bad and are here a new one on the way ??


// matte

---

### Post by TLE on 2006-06-18
It is possible. But perhaps you could first check that your downloads aren't corrupted (I had a network card at some point that did that). You can check it by doing a md5sum like this:
```
md5sum ubuntu-6.06-desktop-i386.iso
```
This will return a code that is unique to this particular iso file, in the case above:
```
e2e5e0bfb2edffd2ce02dd77bda4558e
```
On the site you downloaded there should be a list of md5sums to compare with, e.g. on the danish mirror there is one at [http://www.klid.dk/homeftp/ubuntu-cd/6.06/MD5SUMS]("http://www.klid.dk/homeftp/ubuntu-cd/6.06/MD5SUMS")

I'm am by no means certain that it is due to faulty downloads, but since this would be a pretty significant error it would perhaps be better to check first.
[EDIT]
Any errors during burning ?

---

### Post by mips on 2006-06-18
Lower the speed at which you burn the ISO to x4-x8 or something like that. Sometimes the cd-writer is to blame & not the actual ISO but as suggested above do a md5sum on the ISO to verify it's integrity.

---

### Post by mattiashem on 2006-06-18
Im trying now to burn the iso with 4 X speed

But a have downloaded Edubuntu 6 and burn that iso and it works perfect.
And a tried to downloded the iso down from several mirrors but get the same error.



// matte

---

### Post by aysiu on 2006-06-18
Follow these instructions to make sure you don't have a corrupt ISO. If your ISO is corrupt, it won't matter what speed you burn it at.

[http://www.psychocats.net/ubuntu/iso.html](http://www.psychocats.net/ubuntu/iso.html)

---

### Post by mattiashem on 2006-06-18
Now when a burn the disc in 4X it&#347; look like it&#347; working :-)

time to get a new burner maybe ??
// matte

---

### Post by TLE on 2006-06-18
Probably. I'm glad it's working for you. We can't keep anyone waiting to get their Ubuntu up and running ;)

---

