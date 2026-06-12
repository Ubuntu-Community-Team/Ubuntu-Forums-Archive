---
title: "gfortran missing some libraries in Karmic"
date: 2010-01-25
forum: Installation &amp; Upgrades
---

### Post by TideMan on 2010-01-25
I've recently upgraded from 8.04 to 9.10 and in the process, I've lost access to gfortran.  I'm using the gfortran that came with Karmic, but when I execute the make file I get this:
```
	
ld GetNextPerigee.o -o GetNextPerigee  
ld: warning: cannot find entry symbol _start; defaulting to 0000000008048094
GetNextPerigee.o: In function `MAIN__':
GetNextPerigee.f90:(.text+0x26): undefined reference to `_gfortran_set_options'
GetNextPerigee.f90:(.text+0x2b): undefined reference to `_gfortran_iargc'
GetNextPerigee.f90:(.text+0x60): undefined reference to `_gfortran_getarg_i4'
GetNextPerigee.f90:(.text+0x7c): undefined reference to `_gfortran_stop_string'
GetNextPerigee.f90:(.text+0xa2): undefined reference to `_gfortran_select_string
etc
etc

```

I seem to be missing some libraries but I'm not sure which ones and where I get them from.  Can someone help, please?

---

### Post by TideMan on 2010-01-26
I've solved the problem.
It wasn't that I was missing libraries at all.
What I needed to do was to re-compile all the .f90 files using the new gfortran.
gfortran was getting screwed up trying to link .o files that had been compiled by the old version.

---

### Post by Ephrem on 2012-02-28
How exactly did you do that, I am kind of new to this stuff.
Thanks.

---

### Post by oldos2er on 2012-02-28
Closed. Please start a new thread for your question.

---

