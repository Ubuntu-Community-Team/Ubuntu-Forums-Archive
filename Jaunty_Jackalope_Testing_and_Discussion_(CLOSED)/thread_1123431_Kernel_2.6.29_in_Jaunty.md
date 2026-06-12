---
title: "Kernel 2.6.29 in Jaunty?"
date: 2009-04-12
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by shark1997 on 2009-04-12
I was wondering if you could use the 2.6.29 kernel in jaunty. I am already using it, but does it have any bugs i should know about?

---

### Post by zika on 2009-04-12
> **shark1997 said:**
> I was wondering if you could use the 2.6.29 kernel in jaunty. I am already using it, but does it have any bugs i should know about?
You could, even (much) better, use 2.6.30-rc1 ... :)

---

### Post by shark1997 on 2009-04-12
Where do you get it? is it a .deb package?

---

### Post by zika on 2009-04-12
> **shark1997 said:**
> Where do you get it? is it a .deb package?
[http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.30-rc1/](http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.30-rc1/)
install (in this order) ...all...deb, headers ...deb, image...deb.

---

### Post by jfernyhough on 2009-04-12
Meh... I just open a terminal, cd to where I saved the debs (a dir by themselves) and

$ sudo dpkg -i *.deb

Of course, this works when ONLY THE KERNEL DEBS ARE PRESENT. It's not a good idea to do this in a dir with a load of other debs. :wink:

---

### Post by zika on 2009-04-12
> **jfernyhough said:**
> Meh... I just open a terminal, cd to where I saved the debs (a dir by themselves) and

$ sudo dpkg -i *.deb

Of course, this works when ONLY THE KERNEL DEBS ARE PRESENT. It's not a good idea to do this in a dir with a load of other debs. :wink:
why not, the more the merrier  ... :)
(I was under the impression that the order could be important ... but I've known to be wrong ...)

---

### Post by Zorael on 2009-04-12
I couldn't get .30rc1 to compile, so I'm running .29.1, compiled using kernelcheck. Though I had to manually force video dithering to get my KMS to display colors properly; see [http://bugs.freedesktop.org/show_bug.cgi?id=20997](http://bugs.freedesktop.org/show_bug.cgi?id=20997).

---

