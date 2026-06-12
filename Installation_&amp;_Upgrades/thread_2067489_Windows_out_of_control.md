---
title: "Windows out of control"
date: 2012-10-06
forum: Installation &amp; Upgrades
---

### Post by joelgsf on 2012-10-06
I'm using Ubuntu 12.04 for a month or so. Probabbly due to the last system update, I am having the following problems:

1. I have lost control over all apps windows. I had configured them to show up the control buttons (minimise,maximise,close) on the left upper corner, now they only show them when the window is maximised.
2. I am not able to resise a window, when not maximised.
3. The window which has the focus mixes up with any other window behind it, no matter what style I choose for them.
4. The terminal window does not show up. Only its header shows up in the "menu bar". I know it is active, as I check it in a standard terminal (Ctr+Alt+F1) using ps, and can close it using Kill or going into GUI mode and choosing "file/close window" (I am not sure what are the menu reading in english as I am using a portuguese version).

What can I do to get my windows under control again.
My system is as below:

Ubuntu 12.04 LTS (precise pangolin)
Kernel 3.2.0-31-generic
Xorg version 1.11.3
Video: NVIDIA UNIX x86_64 Kernel Module 295.40
Compiz 1:0.9.7.8-ubuntu1

Many thanks for any help.

---

### Post by joelgsf on 2012-10-07
Well, for your knowledge, I have tried to login into the option "Ubuntu 2D" and all came back into control, terminal shows up, and everything else. All that is missing is the "3D decorations". Is it a problem with compiz?

---

### Post by akoskm on 2012-10-07
> **joelgsf said:**
> Well, for your knowledge, I have tried to login into the option "Ubuntu 2D" and all came back into control, terminal shows up, and everything else. All that is missing is the "3D decorations". Is it a problem with compiz?

There are no 3D decorations in Ubuntu 2D mode.

---

### Post by joelgsf on 2012-10-07
Sorry, I thought that the concatenation of my first and second posts in this thread were obvious. What I meant in the second is that all that I was complainning in the first post disapeared when in 2D mode and asking if this was an indication for a Compiz problem.
No matter what the problem is I am asking the help of anyone who may know what the problem is or, at least, may give me a hint for finding a solution. And obviously, I am not happy with beeing forced to use Ubuntu 2D.
Can anyone help me?

---

### Post by critin on 2012-10-07
I would check my drivers in Additional Drivers or whatever it's called in your version.   It may have been updated so you'll need to revert back to the one that worked.

---

### Post by joelgsf on 2012-10-08
Hello Critin,

I did that but I'm using "nvidia-current", which doesn'say much. I've tried other drivers available to synaptic, compatibles with my GEFORCE 8400 GS, without success. I really don't know what do. For the time beeing I just removed Compiz, which, at least, lets me work confortably, everything working fine, but without the possibilities that Compiz offers, which is a pity, considering the resources of my machine (Core Quad 2.7GHz + 4GiB RAM).
If you can think of anything else I will appreciate.

---

### Post by joelgsf on 2012-10-09
Finaly! I've wiped out nvidia from my system
```

~ sudo apt-get remove --purge nvidia*

```
I had to clean up some directories by hand and repeat the "remove". Then I installed a fresh new driver (nvidia-304.51) downloaded from nvidia's site.
Now everything is working again! :-)

---

