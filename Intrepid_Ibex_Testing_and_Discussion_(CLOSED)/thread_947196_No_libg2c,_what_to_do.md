---
title: "No libg2c, what to do?"
date: 2008-10-14
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by ad_267 on 2008-10-14
I need to run a program that requires libg2c.so, however it is no longer available in Intrepid ([https://bugs.launchpad.net/ubuntu/+source/gcc-3.4/+bug/249991](https://bugs.launchpad.net/ubuntu/+source/gcc-3.4/+bug/249991)). No other debian package will work because they all depend on different versions of gcc-base. Is there any other way to run this program?

I've extracted the library from the hardy package and the program seems to be running ok, but it's a pretty ugly hack and I'm not that happy doing it this way.

---

### Post by Sef on 2008-10-14
What program are you trying to install?

> Is there any other way to run this program?

Have you tried Matthias Klose's suggestion: gfortran?

> No other debian package will work because they all depend on different versions of gcc-base

Ubuntu is not Debian.  Please do not expect its packages to work with Ubuntu.

---

### Post by ad_267 on 2008-10-14
It's [CMISS]("http://www.cmiss.org/"), a finite element modelling package developed at my university.

Well that's the problem, I don't understand his suggestion. I thought gfortran could only be used when compiling the program. How does that help when trying to run a binary linked with libg2c?

And yes of course I didn't expect them to work, but I tried just in case they would. I didn't think there were any other options except for going back to Hardy. By debian packages I also meant the Hardy package.

---

### Post by ssam on 2008-10-20
I have hit this too.

install gfortran does seem not help if you have a precomipled fortran binary.

---

### Post by ad_267 on 2008-10-20
> **ssam said:**
> I have hit this too.

install gfortran does seem not help if you have a precomipled fortran binary.

Yes exactly. I've filed a bug against the application I'm trying to use asking them to move to gfortran, but until then I'm stuck using the libg2c from Hardy, which obviously isn't that great a work around and I'm surprised it works at all.

---

