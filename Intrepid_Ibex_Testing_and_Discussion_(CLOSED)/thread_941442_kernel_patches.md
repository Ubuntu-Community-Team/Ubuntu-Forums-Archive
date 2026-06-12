---
title: "kernel patches"
date: 2008-10-08
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by terry_gardener on 2008-10-08
hello i have a problem with my laptop in intrepid that the fan does start.

i have raised a bug in launchpad and they said it is kernel bug and i should raise it there instead which i did. 

the kernel bug team are asking me to patch the kernel and i have no idea what to do. 

kernel bug report.[http://bugzilla.kernel.org/show_bug.cgi?id=11691](http://bugzilla.kernel.org/show_bug.cgi?id=11691)

launchpad bug report: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/272537](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/272537)

i am currently doing a update at the moment which will make it kernel version 2.6.27.6-generic

any ideas, i would like to get this sorted.

---

### Post by plun on 2008-10-08
Well, this is a challenge and in this case its also about
not destroying hardware.

To build and patch a kernel is a rather long process.  I have done
it several timed following "[the master kernel thread]("http://ubuntuforums.org/showthread.php?t=311158")" NOTE, NOT UPDATED  against RC9!

Better idea maybe ...:)

Can you ping the kernel team on IRC ?

[https://help.ubuntu.com/community/InternetRelayChat](https://help.ubuntu.com/community/InternetRelayChat)

[B]
#ubuntu-kernel[/B]

.

---

### Post by terry_gardener on 2008-10-08
after checking out this master kernel thread. i like the idea of the kernelcheck app. if install and run this it should auto update the kernel to the latest then i have to do is patch it with the patch the kernel big people want.

---

### Post by Kow on 2008-10-08
> **terry_gardener said:**
> after checking out this master kernel thread. i like the idea of the kernelcheck app. if install and run this it should auto update the kernel to the latest then i have to do is patch it with the patch the kernel big people want.

Yea that's right. The kernel "big people" will be giving you test patches since they themselves cannot reproduce the issue you have. If it works on your end then they'll likely push the fix into the kernel trees. I'm not sure what base kernel version they want you to start with...perhaps a git snapshot.

---

