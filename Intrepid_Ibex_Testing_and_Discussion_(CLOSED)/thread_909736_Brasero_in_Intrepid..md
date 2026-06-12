---
title: "Brasero in Intrepid."
date: 2008-09-03
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by exploder on 2008-09-03
In Ubuntu Hardy I can burn CD iso files with no problem but when I burn a DVD iso I get an error. The DVD iso I burn will still work but the error every time is real annoying.

How is Brasero working in Intrepid? Have the problems present in Hardy with Brasero been fixed in Intrepid?

---

### Post by Nullack on 2008-09-03
Why dont you have a look upstream to see the fixes between revisions and the bugs on the gnome bugzilla?

Also the packages search on launchpad will give you a changelog

---

### Post by exploder on 2008-09-03
I just wanted to know if anyone having the same problem in Hardy was not having this in Intrepid.

---

### Post by ronacc on 2008-09-03
the short answer to your question is yes . and an even worse behavior that was also present in hardy, brassero burns dvds "closed"  making it impossible to have a multisession dvd . the fix is easy install K3b it runs fine under gnome .

---

### Post by exploder on 2008-09-04
Just installed Intrepid and tested Brasero, still works like a piece of crap... All of the problems I had in Hardy are still present.It figures...

---

### Post by Nullack on 2008-09-04
So what have you done to improve the situation? Gone upstream and discussed new features? Reported any bugs?

---

### Post by tlayton_at_work on 2008-09-07
There appeared to be an issue with 7.1.2 of dvd+rw-tools. The binaries were core dumping, so I downgraded to 7.0.9 and it worked. But there was an update within the last day or so to 7.1.2-ubuntu1 which fixed the problem.

---

### Post by exploder on 2008-09-07
Thanks for the good news!

---

