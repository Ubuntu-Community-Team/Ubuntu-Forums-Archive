---
title: "not using or seeing all memory (ram)"
date: 2008-10-06
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by lime4x4 on 2008-10-06
I have 4 gigs of memory installed. The bios shows 4 gigs bit intrepid 32 bit only c's 3 gigs

john@john-desktop:~$ free
             total       used       free     shared    buffers     cached
Mem:       3111072    2970196     140876          0      33596    2359064
-/+ buffers/cache:     577536    2533536
Swap:     10715312        260   10715052

---

### Post by bruce89 on 2008-10-06
That's a limitation of 32 bit software. You need to use the 64 bit version.

---

### Post by inportb on 2008-10-06
Interesting... I thought 4GB was the limitation? Unless Linux maps memory like Windows.

On the amd64 kernel, I'm seeing only 90% of my [poor 1GB] RAM XD

---

### Post by bruce89 on 2008-10-06
> **inportb said:**
> Interesting... I thought 4GB was the limitation? Unless Linux maps memory like Windows.

I thought that also.

---

### Post by psyke83 on 2008-10-06
> **lime4x4 said:**
> I have 4 gigs of memory installed. The bios shows 4 gigs bit intrepid 32 bit only c's 3 gigs

john@john-desktop:~$ free
             total       used       free     shared    buffers     cached
Mem:       3111072    2970196     140876          0      33596    2359064
-/+ buffers/cache:     577536    2533536
Swap:     10715312        260   10715052

If you're using the 32 bit version of Ubuntu, you need to use the -server kernel which supports [PAE]("http://en.wikipedia.org/wiki/Physical_Address_Extension"). 

However, even with PAE, your system memory available may still be calculated by the formula: 

> memory available = physical memory - memory reserved by hardware devices

---

### Post by inportb on 2008-10-06
Hm... that makes sense. Besides physical RAM, the system needs to deal with memory-mapped objects that use up address space.

---

