---
title: "Can't install Hoary"
date: 2005-06-18
forum: Installation &amp; Upgrades
---

### Post by duffmckagan on 2005-06-18
I recently got my Hoary CDs, but i just can't seem to install the OS.

The install stops at a message similar to this: (i don't remember the exact message though)

fetching apt-get resources from the Internet.

I can't get a working Internet connection until and unless I sign in to my ISP account.
Moreover, I don't want to use the internet, just while setting Ubuntu up.
What is wrong?

---

### Post by defkewl on 2005-06-18
Ubuntu needs to configure apt and it needs to connect to internet.

---

### Post by duffmckagan on 2005-06-21
[QUOTE=defkewl]Ubuntu needs to configure apt and it needs to connect to internet.[/QUOTE]
 Does it mean that I can't install Ubuntu without a Live Internet connection?

Live in the sense that Is it required at the time of installation?

My Internet connection as already told before is such that I need to sign in to my ISP account to access the Internet, and that too by installing a software.

Can't I install Ubuntu anyway without a Internet Connection? This makes me real Unhappy.
I had installed Warty earlier before, without a problem.

---

### Post by mingus on 2005-06-22
[QUOTE=duffmckagan]Does it mean that I can't install Ubuntu without a Live Internet connection?

Live in the sense that Is it required at the time of installation?

My Internet connection as already told before is such that I need to sign in to my ISP account to access the Internet, and that too by installing a software.

Can't I install Ubuntu anyway without a Internet Connection? This makes me real Unhappy.
I had installed Warty earlier before, without a problem.[/QUOTE]

No, you should be able to install from the CD.  After rebooting into the 2nd stage of the installation, when you get to  apt-get setup . . . it's described at

[http://archive.ubuntulinux.org/ubuntu/dists/hoary/main/installer-i386/current/doc/manual/en/ch07s02.html](http://archive.ubuntulinux.org/ubuntu/dists/hoary/main/installer-i386/current/doc/manual/en/ch07s02.html)

---

### Post by duffmckagan on 2005-06-22
Seems like a lot to be read.

I will read that stuff, and then post my Luck with Installing Ubuntu on my comp.

Thanks for the link man.

---

### Post by musicman2059 on 2005-06-22
[QUOTE=duffmckagan]Seems like a lot to be read.

I will read that stuff, and then post my Luck with Installing Ubuntu on my comp.

Thanks for the link man.[/QUOTE]
 I was in the same situation while installing ubuntu one a connectionless computer.  After a while, the connection will just time out for each online repository and move on to the next step. ;)

---

### Post by mingus on 2005-06-22
[QUOTE=duffmckagan]Seems like a lot to be read.[/QUOTE]

Not really.  Just look for the section about apt-get setup.  During the install, it's just a question or two.

---

### Post by duffmckagan on 2005-06-28
I managed to install Hoary finally, by deciding to "Perform the Network Setup at a later time".

As a result, apt-get did not interfere with the install process saying fetching stuff from the Internet.

---

### Post by mingus on 2005-06-28
[QUOTE=duffmckagan]I managed to install Hoary finally, by deciding to "Perform the Network Setup at a later time".[/QUOTE]

Great . . . this is what I was referring to.

---

