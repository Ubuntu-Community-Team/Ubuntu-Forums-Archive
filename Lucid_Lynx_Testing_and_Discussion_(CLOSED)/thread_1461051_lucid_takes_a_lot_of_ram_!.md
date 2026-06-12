---
title: "lucid takes a lot of ram !?"
date: 2010-04-23
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by lucasart on 2010-04-23
hello everyone

on a freshly installed lucid x64, i have 587 MB used after starting the computer. didn't add any startup application or anything. it seems a lot: it's getting comparable to windows 7, which is really not a compliment...

is it normal / intended by the developers /

---

### Post by Longinus00 on 2010-04-23
See if a reboot fixes it. If the reboot does then it's because of a bug in ureadahead.

---

### Post by BwackNinja on 2010-04-23
There is a bug in Xorg that is a kinda bad memory leak and it needs testing. [https://wiki.ubuntu.com/X/Testing/GEMLeak](https://wiki.ubuntu.com/X/Testing/GEMLeak)

---

### Post by cariboo on 2010-04-23
Windows 7 & Vista attempt to use ram the same way Linux does, all three cache programs in ram until they are needed, as is often said when this question comes up, "empty ram is wasted ram"

Currenty the output of free -m on this system looks like this:

```
free -m
             total       used       free     shared    buffers     cached
Mem:          2009       1993         15          0        950        206
-/+ buffers/cache:        837       1172
Swap:         2000         24       1976
```

As you can see from the above, used memory including cached is 1993Mb, actual usage is 837Mb. Higher ram usage is more than likely because I am running gnome-shell, nautilus, chrome and have a terminal open, plus I'm transcoding a dvd at the moment.

---

### Post by Sylslay on 2010-04-23
In windows like usualy when You see the proces manager , it dysplay PAGE FILE OF RAM. 
I have uesed from 175-300+ MB (with firefox nad 4 tabs open), whan I change hdd for faster , system 9.10 x32bit use less memory than before on old hdd (twice slower than now)/

---

### Post by jeffreyvergara.NET on 2010-04-24
yes, same here... normally I only use 200-300mb RAM in ubuntu 9.10 but in ubuntu 10.4 RC normally it spike to 400-600mb RAM even if i close applications such as firefox and evolution RAM does not decrease.

I also tried xubuntu 10.4 RC but got the same result

---

### Post by mmalone21 on 2010-04-24
Mine is 419mb with 7 Firefox Windows open (call me old-fashioned but I don't use tabs). I just opened the same amount of window on anther machine with windows 7 (all of the eye candy turned of and multiple registry tweaks so it looks like Windows 98, again I am old-fashioned) and it is using 972mb of ram. I will stick will Ubuntu for web browsing.

---

### Post by tokyobadger on 2010-04-24
```
free -m
             total       used       free     shared    buffers     cached
Mem:          5974       2824       3149          0        183        968
-/+ buffers/cache:       1672       4301
Swap:          972          0        972

```
Currently open on the standard Gnome DE are:
Chromium 12 tabs open
2 Terminals
Update Manager
1 IM Conversation Window
Gwibber
Evolution
Rhythmbox (paused)
System Monitor
The load is heavier than my Arch install (same box) which is also amd64, also Gnome, also using compiz. Gwibber I know is 'heavy'.

But as cariboo907 states it's not a problem. On another box I have 4G of DDR2, no swap partition, running Gentoo-amd64 (Funtoo repos) and also Gnome, Chromium etc - yesterday's updates included GCC and Glibc, 2 pretty beefy packages when you compile from source. Memory usage peaked at about 2.6G.

Memory leaks are a valid concern - one app server at work went down last week due to a memory leak - when you're a global organization with 50K; employees, that's a problem.

---

### Post by mörgæs on 2010-04-25
On a freshly booted machine, free -m gives a pleasant surprise:
```

             total       used       free     shared    buffers     cached
Mem:          2011        306       1705          0         60        116
-/+ buffers/cache:        130       1881
Swap:         6675          0       6675

```Only 130 MB used, and this is a standard 10.04 installation where I have not done anything special in order to speed up the system.

On two other machines, a full 8.10 installation takes 235 MB, and a minimal 9.04 takes 82.

In a world of bloated operative systems, I think we can be proud of this.

EDIT: The 8.10 runs Apache and PHP.

---

### Post by xir_ on 2010-04-26
try "df -h" and see if ureadahead is there. If it is then you've likely been hit buy a bug where it doesn't unload from ram once its finished.

---

### Post by Kenda on 2010-04-26
@desktop:~$ free -m
                         used      cache        
-/+ buffers/cache:       1004       4971
Swap:          627          0        627



The above is on a fresh install with just Google chrome open. Uptime is about 12 hours. One other user open.  FGLRX on ATI 4850. Basically Cache is using nearly 5 Gib of Ram.

This doesn't look or feel right to me? does it look problematic?

---

### Post by lean on 2010-04-26
> **Kenda said:**
> @desktop:~$ free -m
                         used      cache        
-/+ buffers/cache:       1004       4971
Swap:          627          0        627



The above is on a fresh install with just Google chrome open. Uptime is about 12 hours. One other user open.  FGLRX on ATI 4850. Basically Cache is using nearly 5 Gib of Ram.

This doesn't look or feel right to me? does it look problematic?

That looks very fine. The only ram usage is 1004MB. buffers/cache just means that some files are loaded into ram, but they are discarded if a program needs the memory. You are not using any swap, which is also as it should be.

---

### Post by mörgæs on 2010-04-26
[http://www.linuxatemyram.com/](http://www.linuxatemyram.com/)

---

### Post by frncz on 2010-04-26
Im using lucid 10.04 on an old laptop with only 384Mb RAM, with no problem. Do Lucid obviously does not need more RAM. However it would be faster with more.

---

### Post by Kenda on 2010-04-26
> **lean said:**
> That looks very fine. The only ram usage is 1004MB. buffers/cache just means that some files are loaded into ram, but they are discarded if a program needs the memory. You are not using any swap, which is also as it should be.

Many thanks for that reply, Lean.

---

