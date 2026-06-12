---
title: "It is not possible to use 4gig of ram in Beta version of Karmic"
date: 2009-10-10
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by legolas_w on 2009-10-10
Hi
I think it is not possible to use 4 gig of ram in Karmic Beta version.
I tried 

```
sudo apt-get install linux-server linux-headers-server
```


and it resulted in package not found. should I include specific repositories or I should wait for final version of Karmic to be able to install that kind of kernel?


Thanks

---

### Post by -grubby on 2009-10-10
... what does that have to do with having 4 GB of RAM?

---

### Post by Bölvaður on 2009-10-10
> **-grubby said:**
> ... what does that have to do with having 4 GB of RAM?

indeed. it doesnt look like it has anything to do with ram at all.

some confusion going on right here that needs to be cleared up.

---

### Post by JillSwift on 2009-10-10
The 32 bit server kernel can page through RAM, meaning it can use more than 3.5GB.

The alternative is to use he 64 bit Karmic.

---

### Post by legolas_w on 2009-10-13
I read in several blogs that using server kernel let a 32 bit linux to use all of my 4 gig ram. Isn't it true?
Some of places which I saw this solution are:

[http://samiux.wordpress.com/2008/01/10/how-to-use-4-gb-ram-on-a-32-bit-ubuntu/](http://samiux.wordpress.com/2008/01/10/how-to-use-4-gb-ram-on-a-32-bit-ubuntu/)

[http://www.cyberciti.biz/faq/ubuntu-linux-4gb-ram-limitation-solution/](http://www.cyberciti.biz/faq/ubuntu-linux-4gb-ram-limitation-solution/)

Thanks

---

### Post by itreius on 2009-10-13
> **legolas_w said:**
> I read in several blogs that using server kernel let a 32 bit linux to use all of my 4 gig ram. Isn't it true?
It is true. However, that's not the only way you can use 4&#8805; GB RAM on Linux, hence why the conclusion you came to is wrong.

---

### Post by mcduck on 2009-10-13
> **JillSwift said:**
> The 32 bit server kernel can page through RAM, meaning it can use more than 3.5GB.

The alternative is to use he 64 bit Karmic.

Or the PAE-enabled 32-bit kernel, which is also available in karmic... ;)

edit: Also, the commands OP tried failed because *there is no such kernel in karmic*. The 32-bit server kernel was dropped from 9.10. [https://wiki.ubuntu.com/KernelTeam/Specs/KarmicKernelFlavours]("https://wiki.ubuntu.com/KernelTeam/Specs/KarmicKernelFlavours")

---

### Post by JillSwift on 2009-10-13
> **mcduck said:**
> Or the PAE-enabled 32-bit kernel, which is also available in karmic... ;)Ooh. That's good to know.

---

### Post by 3rdalbum on 2009-10-13
I don't know about 4GiB of RAM, but I'm currently on 6GiB. 64-bit system.

---

### Post by Gourgi on 2009-10-13
i think this kernel is what you ask for
```
linux-image-generic-pae
```
look for it in synaptic

---

### Post by screaminj3sus on 2009-10-13
Why are you even using 32 bit, with 4 gigs you should just go 64 bit.

---

