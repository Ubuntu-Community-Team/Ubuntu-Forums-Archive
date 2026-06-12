---
title: "good mirror and vim update issue"
date: 2008-11-12
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by ShirishAg75 on 2008-11-12
Hi all, 
 I'm looking for a good mirror, something with a 6 hour delay or something like that delay for updates. So if some issue comes out and is on the forums then can avoid that (atleast from what is known)

The other thing is if somebody knows a workaround for [lpbug]296324[/lpbug] . The one suggested therein doesn't work (unfortunately for me)

---

### Post by plun on 2008-11-12
This is Ubuntus archive mirror list

[https://launchpad.net/ubuntu/+archivemirrors](https://launchpad.net/ubuntu/+archivemirrors)


India only have one mirror according to this in Madras....1 week behind.

---

### Post by ShirishAg75 on 2008-11-12
> **plun said:**
> This is Ubuntus archive mirror list

[https://launchpad.net/ubuntu/+archivemirrors](https://launchpad.net/ubuntu/+archivemirrors)


India only have one mirror according to this in Madras....1 week behind.

I know that's why I never use it. Thank you for your help.

---

### Post by Kevbert on 2008-11-12
Seeing as the bug is triaged, it means that the Ubuntu developers are waiting for Debian to fix the bug (as Ubuntu is based on Debian).  The best thing to do is probably use nano in the mean time.

---

### Post by ShirishAg75 on 2008-11-12
can somebody take a look at this mirror [http://mirror.internode.on.net](http://mirror.internode.on.net) 

on the webpage it says its a day behind, but here it seems its very much current, can somebody find out? 

And if you do, please share how you were u able to come to whatever conclusion you did.

---

### Post by dinxter on 2008-11-12
i'm afraid i cant give any advice on a good mirror, as for vim, vim seems to install now on amd64 from the main repository. if it isnt working for you, from the output you get from dpkg it seems the dpkg script for vim-runtime is having problems, try uninstalling all the vim packages before trying to install vim-tiny or vim (if that is possible now). note, you may need to reintall ubuntu-minimal after uninstalling all the vim packages

[edit] ps. i would say that the uk mirrors seem to have plenty of extra capacity if you are getting slow bandwidth from your local mirrors or from the main repository

---

### Post by ShirishAg75 on 2008-11-12
I actually am looking for a slower mirror, something which is 6 hours or 12 hours behind the curve simply for the fact that sometimes things break or ones runs into a situation where a ubuntu re-install is required. The idea is that strategically I will not end up in a situation where I need to re-install the OS.

---

