---
title: "How to fix crashed system after update &amp; upgrade?"
date: 2011-03-12
forum: Installation &amp; Upgrades
---

### Post by Marcelo Ruiz on 2011-03-12
Hi All,

I have this annoying problem in Ubuntu and I don't know how to solve it. 
I installed some updates suggested by the update manager and now I cannot use X anymore (it waits forever right after loading the wallpaper, so I end up having just the wallpaper and the mouse arrow). My computer can't even load X in safe mode, but I can go into recovery mode and type commands there.
I guess I am hoping for a command like: ```
sudo rollback-last-update
``` :P
I know I am a dreamer, but is there any way to uninstall the last update from the command line? I don't need to tell you that I have no idea which was the last package installed in my system, although that might make getting help easier...
I was wondering if the installed packages go to a specific folder, so I can see and delete the package with the closest date (surgeon style :D).
Anyway, any help will be really appreciated!

---

### Post by garvinrick4 on 2011-03-12
What version you using? Are you using wired or wireless? Have you got a install Cd of same architecture (32 or 64 bit)?
The code to look at upgrades
```
grep upgrade /var/log/dpkg.log
```

---

### Post by Marcelo Ruiz on 2011-03-12
Hi garvinrick4, thanks for your answer.
I am travelling with my laptop, so I don't have the install CD with me. I could burn a new one if I need to.
I am using Ubuntu 10.10 AMD64.
I can see the upgrades with the code you posted, but how do I downgrade a specific package from the command line. I know I can do that using Synaptics, but in this case that is not an option.

---

### Post by garvinrick4 on 2011-03-12
# Do not know code to downgrade a particular package:
# Would say code below would fix dependencies which is usually the package problem.
#To fix broken packages:
```
sudo apt-get -f install
``````
sudo dpkg --configure -a
```#If you need to run broken package fix or install packages on laptop in a Live CD because
you cannot boot into / let me know.
# To get new package from repositories run:
    ```
sudo apt-get clean
```
    ```
sudo apt-get purge "packagename" && sudo apt-get install "packagename"
```
without the cleaning you will get same package in cache in your system.

---

### Post by Marcelo Ruiz on 2011-03-14
Hi garvinrick4,

Thanks again for your help. Trying to hunt down the package that crashed my system was a nightmare, so I decided to do a fresh install (after which everything seems to work normally). I guess I had the problem cause I upgraded from Lucid... I don't know.
Anyway, thanks for your help.

---

