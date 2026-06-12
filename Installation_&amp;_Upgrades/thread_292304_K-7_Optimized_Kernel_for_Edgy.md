---
title: "K-7 Optimized Kernel for Edgy?"
date: 2006-11-03
forum: Installation &amp; Upgrades
---

### Post by doobit on 2006-11-03
Any chance of getting a K-7 optimized kernel for Edgy?

I know I was able to tell the difference in speed and stability with the optimized kernel in Dapper. 

Also, since Edgy is Edgy, maybe it could be a K-7 optimized 2.6.18.1 kernel?

---

### Post by digimars on 2006-11-03
I hope so, my games stutter a bit too much under this i386 kernel on my laptop.

---

### Post by bulldogsay on 2006-11-03
I am also wondering whether there will be an i686 option aswell for the kernel, as edgy is a bit slower than dapper, but I have waited at least since it came out for an option to become available?

What are they playing at?

---

### Post by dcstar on 2006-11-04
> **bulldogsay said:**
> I am also wondering whether there will be an i686 option aswell for the kernel, as edgy is a bit slower than dapper, but I have waited at least since it came out for an option to become available?

What are they playing at?

Why not download the source and configure and build your own kernel?

There are many HOWTOs on this site to do this (I build my own K7 optimised 2.6.17 kernel: [http://iphitus.loudas.com/beyond.html](http://iphitus.loudas.com/beyond.html) )

---

### Post by doobit on 2006-11-06
> **dcstar said:**
> Why not download the source and configure and build your own kernel?

There are many HOWTOs on this site to do this (I build my own K7 optimised 2.6.17 kernel: [http://iphitus.loudas.com/beyond.html](http://iphitus.loudas.com/beyond.html) )

I did that and it works great with a new 2.6.18.1 kernel!

---

### Post by angkor on 2006-11-06
> **doobit said:**
> Any chance of getting a K-7 optimized kernel for Edgy?

I know I was able to tell the difference in speed and stability with the optimized kernel in Dapper. 

Also, since Edgy is Edgy, maybe it could be a K-7 optimized 2.6.18.1 kernel?

A k7 specific kernel is no longer necessary in edgy. You can install the -generic kernel in stead of the default -i386:

```
 apt-cache search linux-image | grep k7
linux-image-k7 - Obsoleted by: linux-image-generic
```

---

### Post by doobit on 2006-11-06
> **angkor said:**
> A k7 specific kernel is no longer necessary in edgy. You can install the -generic kernel in stead of the default -i386:

```
 apt-cache search linux-image | grep k7
linux-image-k7 - Obsoleted by: linux-image-generic
```

When I was compiling the 2.6.8.1 kernel I was given the option of what type of processor I would be using. Maybe the i386 kernel now includes the same code for multimedia that was different in the K7 CPU. All I can say for sure is, it works very well.
I also noticed it compiled a pile of wireless drivers into the kernel as it was compiling.

---

