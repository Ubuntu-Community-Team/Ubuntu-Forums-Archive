---
title: "dependency problem after upgrading from 7.10 Gutsy to 8.04 LTS Hardy"
date: 2008-07-09
forum: Installation &amp; Upgrades
---

### Post by thunderbirdje on 2008-07-09
While upgrading form 7.10 to 8.04 (through the Update Manager)some  installation errors (Python) occured. 

The upgrade suggested to do a manually "dpkg --configure -a".

When I rebooted, the login windows appeared, but some parts of my UI changed, firefox won't start up, HAL error, ...

I switched to terminal window, did a "dpkg --confiugre -a" which displayed following dependency problem

```
Setting up python2.5-minimal (2.5.2-2ubuntu4)
      ... a whole lot of errors with always python in 
      (I couldn't copy paste the error because I was unable to            open firefox, etc to copy paste it to my email or some file, USB-stick also won't work, just like burning a cd-rom :o
...
dpkg: too many errors, stopping
spkg: ../../src/packages.C:252: process_queue: Assertion ´!queuelen' failed. Aborted (core dumped)

```

I did try

```
sudo apt-get update

Extraction (could'n copy paste again): Failed to fetch http://archive.ubuntu.com.....

W: some index files failed to download, they have been ignored, or old ones used instead.

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct this problem

```

Which again, brings me back to the first problem... :(

Thanks in advance!

---

### Post by mikewhatever on 2008-07-09
You have to run dpkg --confiugre -a with root privileges, namely, sudo dpkg --confiugre -a.

---

### Post by avtolle on 2008-07-09
From a terminal, do```
cat /etc/apt/sources.list
```and post the results, please?

---

### Post by thunderbirdje on 2008-07-09
> **mikewhatever said:**
> You have to run dpkg --confiugre -a with root privileges, namely, sudo dpkg --confiugre -a.

Hi Mike

I did use 'sudo' of course :)

Gave also te same problem.

Hi avtolle

sources.list:

(I'm sorry, because no USB-stick, nor CD-ROM, nor tcp/ip works, I had to take some pictures of my screen, hopefully enough readable)

---

### Post by avtolle on 2008-07-09
That sources.list looks a lot like the old PPC sources.list; are you by any chance using an older Mac (PPC)? If so, there's been a change to the PPC sources, which, if applicable, I'll find a link for you.

---

### Post by thunderbirdje on 2008-07-09
No, I'm using an HP portable (HPDV6000 series), intel processor Core 2 Duo.

If needed, I can give you the specs.

The strange thing is: everyting worked perfect in 7.10 Gutsy, just after the update to 8.04 Hardy, things like internet (tcp/ip), Cd-ROM mounting, USB didn't worked anymore (maybe due the error of Python?)...

---

### Post by avtolle on 2008-07-09
Well, taking another look at the sources.list you posted, I don't find any reference to Hardy at all. That tells me that something definitely went wrong during the update. Can you post the results of ```
uname -r
```?

---

### Post by thunderbirdje on 2008-07-09
Strange :o)

result of 'uname -r':

2.6.22-14-generic

---

### Post by avtolle on 2008-07-09
Looks like the kernel for 8.04 didn't install, either. So, it seems to me that you have maybe two options; one, to do a clean install of 8.04; or two, go to upgrade manager, select "Check" to see if there is anything else needed to totally update your 7.10, install anything that is provided, click on "Check" again to see if you are offered the ability to upgrade to 8.04. I think given the python problem, the second option will likely be fruitless, but one never knows.

---

### Post by thunderbirdje on 2008-07-09
Thanks avtolle, I'll try the 2nd solution first. If it don't work, I'll do a clean install. I'll keep you updated (will be tomorrow of the day after - busy schedule coming days ;))

Thanks for your time and help!

---

### Post by avtolle on 2008-07-09
No problem; good luck. I know what you mean by a busy schedule; my time on here the next few days will likely be extremely limited.

---

### Post by thunderbirdje on 2008-07-10
I did a clean install, everything works fine now :)

Thanks!

---

