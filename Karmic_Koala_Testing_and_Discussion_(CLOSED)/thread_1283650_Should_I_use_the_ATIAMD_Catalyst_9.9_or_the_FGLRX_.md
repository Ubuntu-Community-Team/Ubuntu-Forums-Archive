---
title: "Should I use the ATI/AMD Catalyst 9.9 or the FGLRX 9.10??"
date: 2009-10-05
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by emarkay on 2009-10-05
Everything I have seen online relates to Jaunty in regards to 9.9, and I have not really heard of anyone lately indicate any issues with the new "Restricted Driver" 9.10 for the (Radeon type) ATI Cards.

If you have an ATI/AMD card, ina desktop preferably, what are you using for the Graphics Driver, were there any issues in installing it, and has it been stable and acceptable?

Thanks!

---

### Post by emarkay on 2009-10-05
I presume someone will soon be looking over these files to update them to Karmic Standards?

[https://help.ubuntu.com/community/BinaryDriverHowto/ATI](https://help.ubuntu.com/community/BinaryDriverHowto/ATI)

[https://help.ubuntu.com/community/RadeonDriver](https://help.ubuntu.com/community/RadeonDriver)

---

### Post by Longinus00 on 2009-10-06
I have a 4850 and use the opensource radeon driver. The binary drivers have terrible support for dual monitors compared to xrandr so I avoid them. Everything works great except for the no 3D part but I don't miss it all that much.

I don't see why you'd install the 9.9 drivers in karmic considering the 9.10 drivers are released early just for ubuntu.

---

### Post by ELD on 2009-10-06
> **Longinus00 said:**
> 
I don't see why you'd install the 9.9 drivers in karmic considering the 9.10 drivers are released early just for ubuntu.

+1 to this, and the fact that old drivers do not support new kernels, i'm pretty sure that is plastered everywhere across the net.

---

### Post by emarkay on 2009-10-06
> **ELD said:**
> +1 to this, and the fact that old drivers do not support new kernels, i'm pretty sure that is plastered everywhere across the net.

Yea, I noticed this...  :) Thanks!

---

### Post by markbuntu on 2009-10-07
I am using the 9.10 driver with karmic and it resolved a lot of issues I had configuring my 3 monitors and 2 gpus. This is impossible without the ati driver because the current x-server does not support multi-gpus.

The newest X release has returned support for multi gpus but it will probably not make it into Karmic.

---

### Post by ELD on 2009-10-07
It would be useful if the drivers app actually told us what driver version it installs, such a stupid thing to leave out!

---

### Post by Ellipsis on 2009-10-07
> **ELD said:**
> It would be useful if the drivers app actually told us what driver version it installs, such a stupid thing to leave out!

Perhaps we should file a bug report?

jockey-gtk <-- package in question

---

### Post by ELD on 2009-10-08
Honestly i have no idea how to actual do a bug report from scratch :(, someone else will need to do it and link it so i can add my thoughts to it.

---

### Post by taavikko on 2009-10-08
> **Ellipsis said:**
> Perhaps we should file a bug report?

jockey-gtk <-- package in question

> **ELD said:**
> Honestly i have no idea how to actual do a bug report from scratch :(, someone else will need to do it and link it so i can add my thoughts to it.

Actually it's "jockey-common" 
Which affects both frontends... 

With the next command you can report the problem.
```
ubuntu-bug jockey-common
```
Just add the summary and little description...

---

### Post by ELD on 2009-10-08
Thanks buddy have been able to do it now!

If you think this should be in there too then please make a comment and note that it affects you too on my report:
[https://bugs.launchpad.net/ubuntu/+source/jockey/+bug/446252](https://bugs.launchpad.net/ubuntu/+source/jockey/+bug/446252)

It is a case of ATi users being left out in the cold since Nvidia see what version they are getting!

---

