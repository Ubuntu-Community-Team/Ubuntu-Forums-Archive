---
title: "[SOLVED] Missing package in synaptic - Jabbin"
date: 2008-11-01
forum: Installation &amp; Upgrades
---

### Post by realn on 2008-11-01
Hi,

In Kubuntu 8.04 the "jabbin" package is missing. A friend of mine just installed ubuntu 8.04 and this package is present in his synaptic. How come? I thought that repositories/packages are the same on any version of ubuntu. Or do I need to somehow refresh/update/etc. my repos in order to find it because maybe it's a recent package?

 Thanks alot

---

### Post by Partyboi2 on 2008-11-02
There doesn't seem to be a package called jabbin in the ubuntu repo's for any release are you sure your friend has not installed it from a 3rd party repo?

---

### Post by realn on 2008-11-02
Hi,
thanks for the reply, Partyboi2. I am not sure, but he is. Nevertheless, he's an ubuntu beginner.
 How can I tell if he has installed it from some main/3rd party repos and not manually?
 I took a look in his sources.list, only ubuntu repos are present.


Here's an output. Is it a proof that it is installed manually? 

apt-cache policy jabbin
jabbin:
  Installed: 2.0beta2a-1~baltix1
  Candidate: 2.0beta2a-1~baltix1
  Version table:
 *** 2.0beta2a-1~baltix1 0
        100 /var/lib/dpkg/status


What we can do is to have him uninstalled and then try to install it through synaptic, see if he can still fin the package. right?

thanks a lot

---

### Post by tommcd on 2008-11-02
Is Jabbin something he got from the Ubuntu "partner" repo perhaps. You can enable the partner repo through synaptic. I've never used it; but I know that it is for third party packages.

---

### Post by Partyboi2 on 2008-11-02
I would say he manually installed it, if you want to install it  you can go [[COLOR=Blue]here[/COLOR]]("http://sourceforge.net/project/showfiles.php?group_id=166861&package_id=199405&release_id=436700") and download the deb package then double click it to install.

Edit:
>   How can I tell if he has installed it from some main/3rd party repos and not manually?Have a look in Software Sources (System>Admin>Software Sources) for gnome, on the 3rd party tab see what 3rd party repos are listed. You can enter those addresses into your web browser and look for the package.

---

### Post by Kevbert on 2008-11-02
have a look at this [[COLOR="Red"]post.[/COLOR]]("http://ubuntuforums.org/showthread.php?t=617826")

---

### Post by realn on 2008-11-03
Thank you all, guys, for your reply.
We did just like I said: he uninstalled the package, then he couldn't find it anymore via synaptic.. He must have installed it manually without noticing. Anyway, we couldn't get any sound out of it. What's more saddening was that there was no audio wizard/configuration section. It's unbelievable that someone makes a software which uses audio with no audio settings options. Anyway, that's another story...we dropped it right away and we'll try gajim!

I think we can close this thread as solved.
Thanks again to all !

---

### Post by Partyboi2 on 2008-11-03
This will explain how to mark a thread solved
[https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)

---

### Post by realn on 2008-11-04
Thanks a lot, I didn't know how to do it.

---

