---
title: "Trying to install gnome-shell on 10.04 beta inside virtualbox"
date: 2010-04-12
forum: Installation &amp; Upgrades
---

### Post by SnickerSnack on 2010-04-12
Hi all,

I have installed VirtualBox because I want to test out things like 10.04 and gnome-shell.  So, I have downloaded an Ubuntu 10.04 32-bit .vdi from mininova (and so far I'm assuming that the downloaded file is good), and I've been tooling around with it a bit.

It was a bit choppy at times, but that was probably because I was running several other things at the same time.  My comp's stats are in my sig (only addressing 2.9 gigs of ram due to the 32-bit kernel), and I think that any choppiness was due to overloading the computer with other things.  The proc temp also went to record highs, ~75 Celsius, iirc.  The vm has been alloted 1 proc (out of 2) 512 ram.

The problem I am having is that I wanted to install gnome-shell to try it out, but I get an error,

```
adminuser@adminuser-desktop:~$ sudo apt-get install gnome-shell
[sudo] password for adminuser: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  gnome-shell: Depends: libgjs0 but it is not going to be installed
E: Broken packages
```

So I tried to install libgjs0 manually:

```
adminuser@adminuser-desktop:~$ sudo apt-get install libgjs0
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  libgjs0: Depends: xulrunner-1.9.1 (<= 1.9.1.9~) but 1.9.1.9+nobinonly-0ubuntu1 is to be installed
E: Broken packages
```

So, I have xulrunner-1.9.2 already, so I tried to install 1.9.1 anyway, and it appeared to install, and I now have 1.9.1.9 and 1.9.2.3 installed, but trying to install libgsj0 results in the same error as above.

Ideas?

---

### Post by jastonas on 2010-04-13
best solution i came across:

[http://www.webmaster-forums.net/computer-help/gnome-shell-depends-libgjs0-it-not-going-be-installed](http://www.webmaster-forums.net/computer-help/gnome-shell-depends-libgjs0-it-not-going-be-installed)

Dont think will bother trying...
Waiting for something easier :)

I -by accident- found an easier way!
Just add the ricotz ppa and it will install the proper libgjs0.

---

### Post by SnickerSnack on 2010-04-13
> **jastonas said:**
> best solution i came across:

[http://www.webmaster-forums.net/computer-help/gnome-shell-depends-libgjs0-it-not-going-be-installed](http://www.webmaster-forums.net/computer-help/gnome-shell-depends-libgjs0-it-not-going-be-installed)

Dont think will bother trying...
Waiting for something easier :)

I -by accident- found an easier way!
Just add the ricotz ppa and it will install the proper libgjs0.

Thanks!  That seemed to work fine.  gnome-shell is installed, and now I'm about to log back in to see if it works out of the box, or if I need to do anything else.

edit: "gnome-shell --replace" works to get it to run, but boy does it look terrible on my system.  I'm running it in vm, so that may be why.

Attached is a picture of what the vm looks like when running gnome-shell.  I tried increasing the vm's video memory to 36 megs, and I enabled 3d acceleration, such as it is on my hardware.  I guess I'll try more video ram?

If I'm really set on trying gnome shell, and I only have one computer, will I be able to try it using a live cd?  Can temporary changes be made?

---

### Post by soro2005 on 2010-04-15
As far as I understand, there are no deep changes to your system if you install gnome-shell. It's an alternative to Compiz and Metacity. Even if you start it with the session, you can go back to compiz any time you want. You could also create an additional test user if you want to keep your main account clean.

I've just installed gnome-shell and used it for a couple of hours. I didn't expect much, but am thoroughly impressed. It's very well thought through, visually pleasant, and makes it very easy to find your programs and files. A little like the old integrated Do/Docky, but full screen. Pretty choppy, though, and no wobbly windows.

---

### Post by SnickerSnack on 2010-04-16
> **soro2005 said:**
> As far as I understand, there are no deep changes to your system if you install gnome-shell. It's an alternative to Compiz and Metacity. Even if you start it with the session, you can go back to compiz any time you want. You could also create an additional test user if you want to keep your main account clean.

I've just installed gnome-shell and used it for a couple of hours. I didn't expect much, but am thoroughly impressed. It's very well thought through, visually pleasant, and makes it very easy to find your programs and files. A little like the old integrated Do/Docky, but full screen. Pretty choppy, though, and no wobbly windows.

Okay, I'll just try it out.  I mainly was using a vm for 10.04 beta2.

But, given my video hardware, I also don't expect much (I don't use wobbly windows, though).

---

### Post by jastonas on 2010-04-17
> **jastonas said:**
> best solution i came across:

I -by accident- found an easier way!
Just add the ricotz ppa and it will install the proper libgjs0.

This apparently was a mistake. Something else made it work. I found on launchpad an easy solution. Just install the older libgjs from [https://launchpad.net/ubuntu/lucid/i386/libgjs0/0.4-3ubuntu4](https://launchpad.net/ubuntu/lucid/i386/libgjs0/0.4-3ubuntu4)
or [https://launchpad.net/ubuntu/lucid/amd64/libgjs0/0.4-3ubuntu4](https://launchpad.net/ubuntu/lucid/amd64/libgjs0/0.4-3ubuntu4)
depending the architecture

---

### Post by SnickerSnack on 2010-04-17
Installing through apt on 9.10 worked fine and did not need a special repository.

Gnome-shell looks pretty nice, but it was a little bit choppy at times on my hardware, so I doubt that I'll use it much.  (edit: also, it has some bugs and some programs won't run while it's running)  When I build a new desktop with decent-to-nice video hardware, I'll give it another go.

Thanks for your input.

---

