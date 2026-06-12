---
title: "Since partial upgrade - No GUI, no nvidia drivers, no xserver"
date: 2009-09-02
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by bumanie on 2009-09-02
Since a partial upgrade to karmic (64 bit) earlier in the week, I am stuck in a tty1 shell and get the following messages
> xinit: No such file or directory (errno2): unable to connect to X server
> xinit: No such file (errno3): unexpected signal 2.
> xauth: error in locking authority file /home/'username'/Xauthority
Also tail /var/log/Xorg.0.log gives message: "Fatal server error" no screens found
Anyone have any idea how to fix this, anything I have tried makes no difference. I have put in a bug report to launchpad, but at this stage it has not been triaged for attention.

I tried sudo aptitude install make gcc pkg-config x-server-xorg-dev build essential line-headers-2.6.31-6-generic linux-libc-dev : followed by installing the latest stable nvidia drivers via wget
Have also tried startx ; sudo /etc/init.d/gdm start etc. with no luck
Any help most appreciated - Wonder whether this is specific to my computer as there doesn't seem to be anyone reporting the same problem to launchpad, but my hardware is fairly stock-standard stuff and has worked with all ubuntu distro's since 7.04 :confused:.
System: Gigabyte ga-ma770-ds3 motherboard; CPU amd 4800+ ; GPU nvidia 8600gt ; 2gb 800MHz ram

---

### Post by tawmas on 2009-09-02
I had something similar, and found out that the xorg driver had been uninstalled, so I solved that with

```
sudo apt-get install nvidia-glx-185
```

Be sure to match the number to the version of your installed nvidia kernel driver (guessing from you card, you should be using the 185).

After doing that, I still have a problem with Desktop Effects. I posted a [thread about that]("http://ubuntuforums.org/showthread.php?t=1255964"), if you can get your xserver back but no Desktop Effects I suggest you look at that other thread.

---

### Post by bumanie on 2009-09-02
Thank you tawmas, that worked very well. Such a simple fix. Don't why I could not find that on the internet anywhere - must have chosen the wrong group of errors to look up. Thanks again. 
PS: Your suspicion about which nvidia driver version was spot on.

---

### Post by tawmas on 2009-09-02
You're welcome, bumanie. I myself took a little bit to figure it out, until I noticed in /var/log/Xorg.0.log that the X server couldn't find a module named "nvidia"... ;-)

---

