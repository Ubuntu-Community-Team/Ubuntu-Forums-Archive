---
title: "Metisse WM: Success!"
date: 2010-05-23
forum: Installation &amp; Upgrades
---

### Post by arevirlegna on 2010-05-23
Hi everyone,

I was very curious about Metisse ever since it started to come standard in Mandriva, but I never had the time to try to install it on Ubuntu. [Here are some videos so you see what this is about]("http://www.youtube.com/watch?v=P09WLS2a1H0").
Today, I had a some time to kill while watching reruns of House...back to the topic.

I found a couple of .deb files for *nucleo* (Xserver needed for metisse) and *metisse* itself in this archive thread: [URL="http://georgia.ubuntuforums.org/showthread.php?t=58604&page=9"]http://georgia.ubuntuforums.org/showthread.php?t=58604&page=9
[/URL]The .deb files were provided by [cniesel]("http://georgia.ubuntuforums.org/member.php?u=369262")

I just downloaded the .deb files, and double-clicked on them to do the installation (nucleo first, then metisse)

I ran into two problems:
- librplay.so was not found by Metisse...I found it and install it using Synaptic --no problem.
- libdns_sd.so was also not found...I DID NOT find it with Synaptic. But, after some tinkering I realized the interface is equivalent to libdns.so, which I had already installed (it is used by BIND..//..you can find this library with Synaptic) under the name libdns.so.22.1. Solution, I just made the following symlink (make sure you are in /usr/lib)
```
sudo ln -s /usr/lib/libdns.so.22.1.0 libdns_sd.so.1
```That's it!

Start nucleo by executing (I have an old latitude d505 with 1024x768 resolution --use the resolution appropriate to your system) :
```
Xmetisse -ac -depth 24 -geometry 1024x768 :1 &
```Start Metisse by executing:
```
metisse-start-fvwm &
```Metisse is based on FVM, so it will look a little spartan to you if you are used to compiz-fusion. However, I am having fun playing with the rotation and scaling of windows --I particularly like the fact that you can scale and resize firefox to see an entire web page!
 
Cheers!

---

### Post by davec64 on 2010-05-30
Cracking stuff!
Now to get someone to continue development!! :)

---

### Post by joedulin on 2010-06-01
From what I can tell it is still being developed -- 
[http://insitu.lri.fr/metisse/](http://insitu.lri.fr/metisse/)
With source code available at --
[http://insitu.lri.fr/metisse/docs/building.html](http://insitu.lri.fr/metisse/docs/building.html)

But I'm lazy and like my deb packages. So thanks arevirlegna!

---

