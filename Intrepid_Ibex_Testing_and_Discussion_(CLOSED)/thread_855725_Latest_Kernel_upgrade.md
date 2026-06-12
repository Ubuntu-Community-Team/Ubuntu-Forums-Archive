---
title: "Latest Kernel upgrade"
date: 2008-07-10
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by a1234 on 2008-07-10
I have been using Heron as Persistence on one of my MacBook Pro partition and is working great. However I am thinking about upgrading the kernel 2.6.24.26 to 2.6.24.xx. Every time I use the synaptic upgrade and install it will get stuck @ "upgrading sudo @#$$$" ends up corrupting the whole Persistence installation. Any advice on how I can upgrade the kernel? 
Will love to be just incorporate a compiled one to the distro. any tutorial will help.

Thanks in advance

---

### Post by Archmage on 2008-07-11
Are you really trying to mix Hardy and Ibex?

---

### Post by Gina on 2008-07-11
AFAIK many apps are written/updated to work with a specific kernel.  Changing to a newer kernel not supported by these apps is likely to cause breakage.  I would NOT recommend trying to "mix & match" you're asking for trouble and what you are trying to do is not supported - so you're on your own.  Why not have Hardy in one partition for dialy use and install Intrepid in another for testing and playing with?  That is the recommended practice.  (As long as you're up to fixing things if they go wrong - otherwise stick to Hardy)

---

### Post by xebian on 2008-07-11
> **a1234 said:**
> I have been using Heron as Persistence on one of my MacBook Pro partition and is working great. However I am thinking about upgrading the kernel 2.6.24.26 to 2.6.24.xx. Every time I use the synaptic upgrade and install it will get stuck @ "upgrading sudo @#$$$" ends up corrupting the whole Persistence installation. Any advice on how I can upgrade the kernel? 
Will love to be just incorporate a compiled one to the distro. any tutorial will help.

Thanks in advance

Search the forum for the 'Kernel Master', or 'kernel-check??'.  Basically, what you would do is change your sources.list from 'hardy' to 'intrepid', then do update, and then install the intrepid kernel you want.  When you are done, change back 'intrepid' to 'hardy' and do another update.  Good luck.:)

---

### Post by psyke83 on 2008-07-11
> **xebian said:**
> Search the forum for the 'Kernel Master', or 'kernel-check??'.  Basically, what you would do is change your sources.list from 'hardy' to 'intrepid', then do update, and then install the intrepid kernel you want.  When you are done, change back 'intrepid' to 'hardy' and do another update.  Good luck.:)

That's really not a good idea, especially considering that Intrepid's kernel is so immature at this point.

---

### Post by a1234 on 2008-08-03
> **Gina said:**
> AFAIK many apps are written/updated to work with a specific kernel.  Changing to a newer kernel not supported by these apps is likely to cause breakage.  I would NOT recommend trying to "mix & match" you're asking for trouble and what you are trying to do is not supported - so you're on your own.  Why not have Hardy in one partition for dialy use and install Intrepid in another for testing and playing with?  That is the recommended practice.  (As long as you're up to fixing things if they go wrong - otherwise stick to Hardy)

I did try that. Two Ubuntu installation necessitate me to choose which one every time I boot and I can only do it through the menulist. A kind of cumbersome. Therefore settle for the live.

---

### Post by sharks on 2008-08-03
if u want a new kernel, use this **KernelCheck**:
[http://kcheck.sourceforge.net/download.html](http://kcheck.sourceforge.net/download.html)

---

