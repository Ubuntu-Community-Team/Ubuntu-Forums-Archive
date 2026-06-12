---
title: "KDE4 startup problems"
date: 2008-05-12
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by caryb on 2008-05-12
I have a KDE4 problem (3/4 of the forum members fade out at this point:lolflag:) before I can log on I have to delete this folder /home/cary/.kde4/share/ if I don't I get no title bar & windows open in 1/2 size & cant be resized. Is anyone else having this problem? Also my pc wont shut down without the magic power button.


Cary

---

### Post by ronacc on 2008-05-13
can't help with most of that because I don't have Kubuntu installed yet only gnome , but about the shutdown have you tried from the terminal ?

---

### Post by utUtu on 2008-05-13
> **caryb said:**
> I have a KDE4 problem (3/4 of the forum members fade out at this point:lolflag:) before I can log on I have to delete this folder /home/cary/.kde4/share/ if I don't I get no title bar & windows open in 1/2 size & cant be resized. Is anyone else having this problem? Also my pc wont shut down without the magic power button.


Cary

Same here.  It's now totally unuseable.  The 4.0.4 backports is a disaster - can't resize, no title bar, can't move them around.  All windows stuck on one corner, desktop workspace/pager messed up, showing just 1 & can't change.

---

### Post by caryb on 2008-05-13
If you boot to recovery mode by default & select root access & delete the file I put 2? posts up then go ctl D it will then normal boot to a good KDE4 minus any desktop changes (they get deleted)


Cary

---

### Post by disturbedite on 2008-05-14
i did a fresh install of kubuntu 8.04-kde4 x86, upgraded to intrepid, & updated kde to 4.0.4 via hardy-backports all without any problems.

# i still can't believe *hardy-backports* got kde 4.0.4 before intrepid!

---

### Post by caryb on 2008-05-14
Any chance of posting your sources.list ???


Cary

---

### Post by disturbedite on 2008-05-14
@ caryb
me?
here is the relevant portion:

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) intrepid main restricted 
# deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) intrepid main restricted 
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) intrepid-updates restricted main multiverse universe 
# deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) intrepid-updates main restricted 
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) intrepid universe multiverse 
# deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) intrepid universe multiverse 
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) intrepid-proposed restricted main multiverse universe 
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hardy-backports main restricted universe multiverse 
# deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hardy-backports main restricted universe multiverse 
deb [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) intrepid-security main restricted 
# deb-src [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) intrepid-security main restricted 
deb [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) intrepid-security universe multiverse 
# deb-src [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) intrepid-security universe multiverse

---

### Post by quickshade on 2008-05-14
> **disturbedite said:**
> i did a fresh install of kubuntu 8.04-kde4 x86, upgraded to intrepid, & updated kde to 4.0.4 via hardy-backports all without any problems.

# i still can't believe *hardy-backports* got kde 4.0.4 before intrepid!
Because 4.1 will be default in 8.10.

---

### Post by caryb on 2008-05-14
disturbedite, Thanks mate! Well thats no different to mine so I'm not missing any repo's so It must either be a architecture thing or hardware proplem:confused:


Cary

---

### Post by utUtu on 2008-05-14
caryb@
It's flaky, so I just went back to 4.0.3.  Will probably just wait for 4.0.5 or 4.1 beta around May 27.

disturbedite@
I might try your way too.  But could it be you have the 4.0.71 - 4.1 snapshot in ibex?

---

### Post by disturbedite on 2008-05-15
> **quickshade said:**
> Because 4.1 will be default in 8.10.
no.  pre-releases get updated all the time.  hardy-kde4 shipped with 4.0.3.  since pre-releases are constantly updated compared to a LTS release, intrepid should be getting 4.0.4.

---

### Post by quickshade on 2008-05-15
> **disturbedite said:**
> no.  pre-releases get updated all the time.  hardy-kde4 shipped with 4.0.3.  since pre-releases are constantly updated compared to a LTS release, intrepid should be getting 4.0.4.
I'm not understanding what your trying to say here. 4.1 will be out before feature freeze and will be in beta pretty soon. Why package 4.0.4 when it's a better move to package 4.1 and have more people beta testing it for bugs.

---

### Post by disturbedite on 2008-05-15
no offense, but you're right, you're not understanding what i mean.
in development pre-releases, the software is generally kept "up-to-date" compared to LTS release.  so intrepid should get every kde4 release up to kde 4.1.
i understand that the final version will have 4.1, but it is currently already at 4.0.3, so hence my point.

---

### Post by quickshade on 2008-05-15
I understand what your trying to say. But to me it makes more sense to package KDE 4.1 so that we can properly test it.

---

### Post by disturbedite on 2008-05-16
> **quickshade said:**
> I understand what your trying to say. But to me it makes more sense to package KDE 4.1 so that we can properly test it.
well, i don't know if they have a timetable for getting kde 4.1 into the repo for testing, but if they don't, it would make more sense to get 4.0.4 into intrepid already.

but i agree, i would like to see kde 4.1 alpha 1 in the repo already...
the Hard Feature Freeze is in three days.

---

### Post by sion65 on 2008-06-06
Back to the original question...

I have the same issue, but find that logging in, logging out, then back in again gets me to a state where the window decorations etc. are working as expected.

This means that any desktop changes that I have made are preserved.

When I have some time I'll try to work out what is different about the 2 logins (or maybe I'll just wait for 4.1 to come out).

I hope that this helps.

---

### Post by santius on 2008-08-10
I solved this removing compiz from kde and executin:

kwin --replace

This should work! It worked for me.

---

