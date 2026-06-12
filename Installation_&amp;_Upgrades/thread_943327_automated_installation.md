---
title: "automated installation"
date: 2008-10-10
forum: Installation &amp; Upgrades
---

### Post by ikke13 on 2008-10-10
Good day 

me and a classmate or working on a project too have a linux server deploy different operating systems using netboot.
Now we have managed too use it too install other ubuntu versions and debian however these where not fully automatic.
But the bigger problem we're facing is the fact that we can't manage too deploy xp and vista clients and since our teachers are very microsoft dependent it is a must.

After searching for quite some time we can't manage too find anything of use so we would like too know is is possible too install windows clients with added software fully automated using a linux server.

We also have images made using nlite with several free programs intergrated these are in an iso file format so perhaps there is a way too use a linux server too start iso's over netboot.

Thanks in advance

---

### Post by cilkay on 2008-10-10
Take a look at [ANI]("http://ani.sourceforge.net"). I haven't used it myself but it looks interesting.

---

### Post by ikke13 on 2008-10-13
Thanks i will have a look

---

### Post by bbmak on 2008-11-24
I am doing the opposite. I am using windows server to deploy all types of OS.

From Vista, XP, Linux, to Mac OS

---

### Post by bbmak on 2011-10-22
> **ikke13 said:**
> Good day 

me and a classmate or working on a project too have a linux server deploy different operating systems using netboot.
Now we have managed too use it too install other ubuntu versions and debian however these where not fully automatic.
But the bigger problem we're facing is the fact that we can't manage too deploy xp and vista clients and since our teachers are very microsoft dependent it is a must.

After searching for quite some time we can't manage too find anything of use so we would like too know is is possible too install windows clients with added software fully automated using a linux server.

We also have images made using nlite with several free programs intergrated these are in an iso file format so perhaps there is a way too use a linux server too start iso's over netboot.

Thanks in advance

I am using the Microsoft WDS(Mixed Mode) to deploy both XP, Vista, 7, and Linux unattendedly, even 95/98, but bootdisk required.
For Windows, it is easy, and I not talk about it. For linux(debian/redhat based), you need a kickstart file. which you have to modify the .cfg file to point to the .ks file in the server.

---

