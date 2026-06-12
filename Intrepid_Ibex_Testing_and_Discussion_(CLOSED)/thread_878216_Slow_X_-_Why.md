---
title: "Slow X - Why?"
date: 2008-08-02
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by xlnt01 on 2008-08-02
This is something that I never been able to understand.
I really like Ubuntu/Kubuntu and use it every day but there is one thing that I just can't understand. Why is X in Ubuntu (and all other buntu's) slower than others?
Installing a pure debian desktop and you will see a difference in performance. Also with opensuse and fedora you will see that they perform better that Ubuntu. This is specially noticed now that KDE4.1 has been released. It just runs so much better/faster on other dists than Ubuntu/Kubuntu. This is something I noticed about 2 or 3 years ago when I started using Ubuntu but as I said I never understood why and still don't.
Does anyone have a good explanation for this?

---

### Post by jualin on 2008-08-02
I happen to disagree, I feel that Ubuntu runs faster than OpenSuse and most Gnome distros. Again, it depends on your system. My system runs better Ubuntu than OpenSuse, however one of my laptops runs better PCLinux than Ubuntu. Just a matter of preference I believe.

---

### Post by jualin on 2008-08-02
BTW this thread should be moved to some other place such as "Recurring Discussions"

---

### Post by amano on 2008-08-02
> **xlnt01 said:**
> Why is X in Ubuntu (and all other buntu's) slower than others?
Installing a pure debian desktop and you will see a difference in performance. Also with opensuse and fedora you will see that they perform better that Ubuntu. This is specially noticed now that KDE4.1 has been released.

Errm. How do you measure the performance of X? Just ranting that others are "more performant" doesn't help here. Set up a testcase or something. And KDE 4.1 is rather early in its development cycle and problems with the official nVidia drivers are well known: [http://www.phoronix.com/scan.php?page=article&item=nvidia_173_14_12&num=1](http://www.phoronix.com/scan.php?page=article&item=nvidia_173_14_12&num=1)

---

### Post by Peaceable Frood on 2008-08-03
I find the Gnome's performance to be comparable to XP. YMMV, but since the open source ati driver now supports 3D, I'm good.

---

### Post by shad0w_walker on 2008-08-03
If you have a solid metric to prove it's slower, please show us. If not, it's in your head.

---

### Post by jualin on 2008-08-03
> **shad0w_walker said:**
> If you have a solid metric to prove it's slower, please show us. If not, it's in your head.

:lol: :lol: :lol:

---

### Post by ronacc on 2008-08-03
an "objective" comparison of the "performance " of a single piece of software between distros is virtualy impossible , software does not run in a vaccum it interacts with the whole system and trying to sort out where any differences arise is not an easy thing . Think different kernels ,libraries , daemons , etc,etc .

---

### Post by aamukahvi on 2008-08-03
> **ronacc said:**
> an "objective" comparison of the "performance " of a single piece of software between distros is virtualy impossible , software does not run in a vaccum it interacts with the whole system and trying to sort out where any differences arise is not an easy thing . Think different kernels ,libraries , daemons , etc,etc .
You can still compare "X speed in Ubuntu" vs. "X speed in Fedora" and that's the whole point, right? You're not using only X, but the whole software stack provided by the distributor.

---

### Post by ronacc on 2008-08-03
from the original post 
 " Why is X in Ubuntu (and all other buntu's) slower than others? 
you can certaily compare the subjective "feel" of speed in Ubuntu  and Fedora  and you can objectvely compare the speed with which certain tasks are performed "it takes 2 seconds to do something in Fedora and 3 seconds to do the same thing in Ubuntu " but to objectively say X ( by which I assume the OP means  Xorg) is slower in one than the other would require a very specilised test under conditions that would be difficult to standardize.
I have Opensuse 11.0 (kde 4.0)  and 3 Ubuntu's (all gnome) gutsy ,hardy and Intrepid all on the same box and there is no speed difference so great that it forces me to pay attention and say "damn thats slow" .

---

### Post by plun on 2008-08-03
> **ronacc said:**
> 
I have Opensuse 11.0 (kde 4.0)  and 3 Ubuntu's (all gnome) gutsy ,hardy and Intrepid all on the same box and there is no speed difference so great that it forces me to pay attention and say "damn thats slow" .

Just for fun....
[http://gtkperf.sourceforge.net/](http://gtkperf.sourceforge.net/)

Within Ubuntus repo.

There is also a new PerfKit from nVidia
[http://developer.nvidia.com/object/nvperfkit_home.html](http://developer.nvidia.com/object/nvperfkit_home.html)

But its including a driver and its 173.14, Albertos solution
works just great so I dont want to test....:)

---

### Post by xlnt01 on 2008-08-03
I'm not saying, damn thats slow. Just pointing out that there is a noticeable difference in performance running for instance kde4.1 in Ubuntu compared to running it in Debian Lenny on the same  machine. Also The latest build of opensuse with kde4.1 runs better than it does on ubuntu (but of course there are a lot of other bugs with it).
Measure it, as some of you say, that is not easy but if you are interested in seeing it for your self simply install Debian Lenny. Base install and then add the debian experimental repo and install kde4. I think that you will se what I mean then. Menu's are drawn instant, no 0.1 seconds slowness and no strange gfx artifacts.

Although running intrepid Kubuntu (daily updated) witch performs better than 8.04.1 it still does not feel as quick and slick as running it on Debian Lenny.
Simply just wondering why...

---

### Post by plun on 2008-08-03
Well, I switched to KDE4 and I have excellent performance.

nvidia-glx-177 installed


I also noticed earlier that some new packages was included
```

sudo apt-get install kubuntu-desktop
```

for a check.

Just great !!! :)

---

### Post by jualin on 2008-08-03
> **plun said:**
> Well, I switched to KDE4 and I have excellent performance.

nvidia-glx-177 installed


I also noticed earlier that some new packages was included
```

sudo apt-get install kubuntu-desktop
```

for a check.

Just great !!! :)

Usually is the other way around but if it works for you we are happy about it. ;)

---

### Post by ronacc on 2008-08-03
> **xlnt01 said:**
> I'm not saying, damn thats slow. Just pointing out that there is a noticeable difference in performance running for instance kde4.1 in Ubuntu compared to running it in Debian Lenny on the same  machine. Also The latest build of opensuse with kde4.1 runs better than it does on ubuntu (but of course there are a lot of other bugs with it).
Measure it, as some of you say, that is not easy but if you are interested in seeing it for your self simply install Debian Lenny. Base install and then add the debian experimental repo and install kde4. I think that you will se what I mean then. Menu's are drawn instant, no 0.1 seconds slowness and no strange gfx artifacts.

Although running intrepid Kubuntu (daily updated) witch performs better than 8.04.1 it still does not feel as quick and slick as running it on Debian Lenny.
Simply just wondering why...
 
I have no doubt that you are seeing differences . my comment about "damn thats slow " merely ment that any differences I am seeing are not enough to be annoying, to me subjectively . also note that I have KDE4.0 under opensuse and gnome under the 3 butnus so thats apples and oranges anyway .

---

