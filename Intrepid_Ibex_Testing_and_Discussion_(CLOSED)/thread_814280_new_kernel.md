---
title: "new kernel?"
date: 2008-05-31
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by scradock on 2008-05-31
Is there a new kernel available? I've seen a comment or two about people using 2.6.25, and here I am stuck on 2.6.24.17. Nothing in the Synaptic list that I can see - is .25 strictly for compile-it-yourselfers?

---

### Post by 23meg on 2008-05-31
You can always find out by checking [http://packages.ubuntu.com](http://packages.ubuntu.com) and/or [https://launchpad.net/ubuntu/+search](https://launchpad.net/ubuntu/+search).

---

### Post by gnomeuser on 2008-05-31
> **scradock said:**
> Is there a new kernel available? I've seen a comment or two about people using 2.6.25, and here I am stuck on 2.6.24.17. Nothing in the Synaptic list that I can see - is .25 strictly for compile-it-yourselfers?

You should be a little careful with .25 - there are some scheduler issues which might lead to an atrocious experience (depends on configuration). I know they are fixed in .26 just so you are warned

---

### Post by plun on 2008-05-31
> **scradock said:**
> Is there a new kernel available? I've seen a comment or two about people using 2.6.25, and here I am stuck on 2.6.24.17. Nothing in the Synaptic list that I can see - is .25 strictly for compile-it-yourselfers?

You can follow Ubuntus kernel team here

[http://kernel.ubuntu.com/git?p=ubuntu/ubuntu-intrepid.git;a=summary](http://kernel.ubuntu.com/git?p=ubuntu/ubuntu-intrepid.git;a=summary)

[http://kernel.ubuntu.com/git?o=age](http://kernel.ubuntu.com/git?o=age)

Linux-ports was also accepted...
[https://lists.ubuntu.com/archives/intrepid-changes/2008-May/000940.h](https://lists.ubuntu.com/archives/intrepid-changes/2008-May/000940.h)

------
Its also easy to build your own kernel

[http://ubuntuforums.org/showthread.php?t=311158](http://ubuntuforums.org/showthread.php?t=311158)

3 gig free and dont forget to check audio and wireless drivers...

Manual procedure for 3D graphic drivers including patch for nVidias (2.6.26)

---

### Post by Cront on 2008-06-02
I'm also interested in installing the .25 kernel.

I've followed the instructions here: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/200142/comments/6](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/200142/comments/6)

But after running apt-get update I still can't see any reference to .25 in Synaptic.  What am I doing wrong?

When I run apt-get update I can see it hitting the launchpad servers but still nothing in Synaptic.

---

### Post by ShirishAg75 on 2008-06-02
2.6.26-rc3 has been released on May  18, 2008so its just a matter of time that the build happens and we get it to test stuff. It would take whatever time it has to take , we just have to be patient. I'm looking forward as some point after that there would be possibility to go to ext4, much improvement over existing things.

---

### Post by plun on 2008-06-02
> **Cront said:**
> 
But after running apt-get update I still can't see any reference to .25 in Synaptic.  What am I doing wrong?



Nothing wrong...it seems to be building failures for the moment

[https://edge.launchpad.net/~kernel-ppa/+archive](https://edge.launchpad.net/~kernel-ppa/+archive)

You have a little arrow besides the source package, click on
it and you can see details.

---

