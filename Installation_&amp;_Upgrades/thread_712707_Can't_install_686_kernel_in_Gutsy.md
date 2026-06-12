---
title: "Can't install 686 kernel in Gutsy"
date: 2008-03-02
forum: Installation &amp; Upgrades
---

### Post by iThinkergoiMac on 2008-03-02
I'm trying to install the 686 kernel in Gutsy on my ThinkPad (Pentium M). But I can't seem to do it... this is what I get in the terminal:

```
myusername@Finite:~$ sudo apt-get install linux-686
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package linux-686

```

I've looked at guides on how to do this, and they all say to use the "sudo apt-get install linux 686" command. But I get that (above) whenever I try to do it.

So now the question is: is it even worth changing over to 686? Pentium M doesn't have hyperthreading, so if there won't be any kind of performance boost, then I won't bother. But if there's a chance I could get a boost, I'd go for it. I'd be willing to just install it and see, but of course that's not really an option.

---

### Post by vijaym on 2008-03-04
you might need to get the security and restricted packages enabled on your system. One way is by using synaptic - found at system - administration.
go to repositories and enable these.

---

### Post by iThinkergoiMac on 2008-03-04
That's not it... they're both already enabled (and I did just check).

---

### Post by dstew on 2008-03-04
There really is no such thing as an i386 or i686 kernel anymore with Ubuntu. The standard generic kernel detects your CPU architecture and configures itself to use i686 instructions if your CPU has that capability. The reason that apt-get install linux-686 fails is that that package is no longer available, or necessary. See [this thread]("http://ubuntuforums.org/showthread.php?t=711289&highlight=686+kernel"), especially the post by az on page 2.

That said, you can always compile your own custom kernel with the i686 extensions built in. There probably will not be any enhancement in performance, but it might be an interesting exercise.

---

### Post by iThinkergoiMac on 2008-03-04
Ah... I guess that makes sense. Since I'm at school right now, I don't really have a whole lot of time to learn how to compile a kernel, but I may have to try over the summer.

Thanks!

---

