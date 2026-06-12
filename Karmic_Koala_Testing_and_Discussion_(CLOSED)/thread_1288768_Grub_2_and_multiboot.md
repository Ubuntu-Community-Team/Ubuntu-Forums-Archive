---
title: "Grub 2 and multiboot"
date: 2009-10-11
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by muadnu on 2009-10-11
I guess this has been answered somewhere already but I haven't found it...

I installed karmic beta on a multiboot setup. I chose to install the boot loader to my karmic root partition instead of the MBR, and then did the old trick of adding a section to my main grub menu to boot from that partition:```
title Ubuntu 9.10 Beta
        rootnoverify (hd0,5)
        chainloader +1

```
This has always worked for me until now, but seemingly not anymore with Grub 2, I get an error saying something like "cannot mount selected partition"...

---

### Post by VMC on 2009-10-11
> **muadnu said:**
> I guess this has been answered somewhere already but I haven't found it...

I installed karmic beta on a multiboot setup. I chose to install the boot loader to my karmic root partition instead of the MBR, and then did the old trick of adding a section to my main grub menu to boot from that partition:```
title Ubuntu 9.10 Beta
        rootnoverify (hd0,5)
        chainloader +1

```
This has always worked for me until now, but seemingly not anymore with Grub 2, I get an error saying something like "cannot mount selected partition"...

I think this [topic]("http://ubuntuforums.org/showthread.php?t=1284914&highlight=bad+idea") is exactly what your addressing.

---

### Post by muadnu on 2009-10-11
> **VMC said:**
> I think this [topic]("http://ubuntuforums.org/showthread.php?t=1284914&highlight=bad+idea") is exactly what your addressing.
I'm not sure what I'm supposed to do... Run update-grub2, but where? Should I boot off a karmic live cd and do it on the corresponding pbr? I'm not sure I can do it from a different distro since it's not running grub 2.

---

### Post by VMC on 2009-10-11
> **muadnu said:**
> I'm not sure what I'm supposed to do... Run update-grub2, but where? Should I boot off a karmic live cd and do it on the corresponding pbr? I'm not sure I can do it from a different distro since it's not running grub 2.

You installed karmic's grub2 into its partition. Then your trying to use grub-legacy from mbr to chainload that partition,correct?

Not sure, but I think that's where the problem is.

---

### Post by muadnu on 2009-10-11
> **VMC said:**
> You installed karmic's grub2 into its partition. Then your trying to use grub-legacy from mbr to chainload that partition,correct?

Not sure, but I think that's where the problem is.

Yes to your question. And yes, I guess that's where the problem is. I thought (erroneously, seemingly) that as long as one chainloads and tries start from the other partition things would work, as when people chainload to boot Windows. But I guess grub knows how to handle that, but not how to handle grub 2...

---

### Post by oldfred on 2009-10-11
This is my entry in old grub and it works just fine. I installed grub2 to the partition with alpha5 (I think). Every update to Karmic gives lots of warning messages but everything works.

title       Ubuntu 9.10 Karmic 64 bit @ sdc7
root        (hd2,6)
chainloader +1

added:
I have only used rootnoverify with windows?

---

### Post by kansasnoob on 2009-10-11
Well, first of all, calm down. Grub 2 is new to all of us. If you can boot everything but Karmic on your multi-boot we have time, right?

I had a similar problem where I couldn't chainload into grub2 from legacy grub and I started writing this:

[http://ubuntuforums.org/showthread.php?t=1247994](http://ubuntuforums.org/showthread.php?t=1247994)

But still even this is far from "how to" stage:

[http://ubuntuforums.org/showpost.php?p=8071880&postcount=18](http://ubuntuforums.org/showpost.php?p=8071880&postcount=18)

So take a breath! Take some time and you'll sort it out!

---

### Post by markbuntu on 2009-10-11
+1 what oldfred did, worked for me with karmic beta.

---

### Post by muadnu on 2009-10-12
First, thanks for your help!

> **oldfred said:**
> This is my entry in old grub and it works just fine. I installed grub2 to the partition with alpha5 (I think). Every update to Karmic gives lots of warning messages but everything works.

title       Ubuntu 9.10 Karmic 64 bit @ sdc7
root        (hd2,6)
chainloader +1

added:
I have only used rootnoverify with windows?
I tried this (that is, I changed rootnoverify to root) but still get the same error, which, by the way, is
```
Error 13: invalid or unsupported executable filesystem
```


> **kansasnoob said:**
> Well, first of all, calm down. Grub 2 is new to all of us. If you can boot everything but Karmic on your multi-boot we have time, right?

I had a similar problem where I couldn't chainload into grub2 from legacy grub and I started writing this:

[http://ubuntuforums.org/showthread.php?t=1247994](http://ubuntuforums.org/showthread.php?t=1247994)

But still even this is far from "how to" stage:

[http://ubuntuforums.org/showpost.php?p=8071880&postcount=18](http://ubuntuforums.org/showpost.php?p=8071880&postcount=18)

So take a breath! Take some time and you'll sort it out!
Yes, there's no real hurry. I'll try your suggested posts when I have time and report back here.

---

### Post by markbuntu on 2009-10-12
Hate to ask but are you absolutely sure you are aimed at the proper partition???

---

### Post by muadnu on 2009-10-12
Yes, I am sure.

---

### Post by oldfred on 2009-10-12
I was just at the supergrub site and he issued an update for chainbooting from a logical to a logical. 

My boot that works is from a primary to a logical. I did find some info where they said grub2 was also to be updated.

---

### Post by markbuntu on 2009-10-12
Hmmm... logical to logical is a problem with grub???
I never considered that...I never did it either...
I am also booting without problems from a primary (grub1) to a logical (grub2)

---

### Post by ranch hand on 2009-10-12
I do not chainload but all my partitions are logical and I have no problem booting from grub2 to any of my OS'.

I have one 320Gb drive for 32bit testing and it is one extended partition.  I have two 320Gb drives for 64bit testing (root on one drive, home on the other) they are both one extended partition apiece.

I have one 64bit 9.10 version on my internal (32bit drive) that is a special case and I run 64bit when fooling with it.  It boots all my test drives (32 and 64bit) very well.

I am booting Hardy, Jaunty, Karmic and Mandriva on those drives, several flavors of all but Hardy (only 1).

---

### Post by muadnu on 2009-10-12
I thought I was chainloading primary to logical, but now I remembered I'm not... My main OS at the moment is Fedora 11 which, for some reason, required a separate boot partition if the root partition was ext4. And the extra boot partition I created is a logical partition. So I guess I'll have to wait until the updates to grub 2 go upstream and maybe install a karmic snapshot or the release candidate. Or could I try something like Super Grub Disk to reinstall grub 2 in my karmic partition, assuming grub is fixed?

Of course, I could just install the karmic grub to the mbr, but I've read about people having issues recoginizing other OSs and I don't want to risk this on my work laptop.

---

