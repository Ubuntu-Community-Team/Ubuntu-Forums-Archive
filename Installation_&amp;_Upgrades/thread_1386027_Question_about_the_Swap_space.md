---
title: "Question about the Swap space"
date: 2010-01-20
forum: Installation &amp; Upgrades
---

### Post by AmrH on 2010-01-20
Now if I have 6 GB of RAM on Ubuntu 32bit, do I still need to create a swap space? What if I have 4GB of RAM? Shouldn't both RAM and Swap never exceed 4 GB on a 32bit system?

---

### Post by mikewhatever on 2010-01-20
It depends on your usage, but, most often then not, with 4GB of RAM you'll only need swap for suspense to disk, aka hibernation. I only have 1GB of RAM and swap is only rarely used.

---

### Post by AmrH on 2010-01-20
I'm asking about whether the combo of RAM and swap can exceed 4Gb!

---

### Post by oldfred on 2010-01-20
The server install of Ubuntu is the only way to use more than about 3GB of memory with the 32 bit version. You need the 64 bit version to utilize more memory with the standard desktop installs.

Swap is for overflow but is just where memory is copied. It also is used for hibernation. With the standard 32 bit version having swap over 3GB is also probably a waste.

---

### Post by mk1w86 on 2010-01-20
Do you have any particular problems with the 64bit version of Ubuntu? :-s

---

### Post by AmrH on 2010-01-20
I've heard that Java and flash have problems with the 64 bit version; however, as a Java developer I can't afford having problems with Java

---

### Post by mk1w86 on 2010-01-20
I run Ubuntu 64bit and I think most flash problems have been sorted out now and it is no worse that the 32bit version.  I am not as sure about java but as far as I know it is fine, you might want someone else's input on this. :D

It is probably worth trying the 64bit version first because it might work fine for you.  If it doesn't and you have to use the 32bit version you can use PAE to address more than 4GB of RAM, but I would only recommend you use PAE if you absolutely need to see all the RAM because it can introduce other problems. ;)

---

### Post by AmrH on 2010-01-20
It'd be awesome if someone can tell me what isn't gonna work on the 64 bit version, because I'll lose about 2GB of memory if I stick with the 32bit version.

---

### Post by wojox on 2010-01-20
Look at the PAE Kernel [PAE]("http://ubuntuforums.org/showthread.php?t=855511")

---

### Post by AmrH on 2010-01-20
I guess I'll move to the 64bit edition. Hope no software breaks!

Edit: Unfortunately, there are no Canon printer drivers for the x64!

---

### Post by oldfred on 2010-01-20
There are at least some Canon drivers. My i850 worked without any effort. And at home my mp160, which when new required all sorts of install effort, now worked without any effort. They just appeared when I turned the printer on and have printed without any issue.

---

### Post by Jimmyfj on 2010-01-20
On my 64 bit Ubuntu 9.10 install I have no issues with neither Java nor Flash. As for the swap space, in a modern 64 bit system you rarely need any swap space at all. In general if you have a 64 bit system you should make your swap partition no bigger half the size of your physical RAM. If you have 6 GB RAM installed you will be okay with 2.5 - 3 GB on your swap partition. 

Swapping slows down your system performance due to a lot of unnecessary read/write. Things do work a lot faster in memory than on disk.

Same thing about Java and Flash holds true on my Lucid Lynx Alpha 2 installation which I'm running right now.

---

### Post by AmrH on 2010-01-21
> **Jimmyfj said:**
> On my 64 bit Ubuntu 9.10 install I have no issues with neither Java nor Flash. As for the swap space, in a modern 64 bit system you rarely need any swap space at all. In general if you have a 64 bit system you should make your swap partition no bigger half the size of your physical RAM. If you have 6 GB RAM installed you will be okay with 2.5 - 3 GB on your swap partition. 

Swapping slows down your system performance due to a lot of unnecessary read/write. Things do work a lot faster in memory than on disk.

Same thing about Java and Flash holds true on my Lucid Lynx Alpha 2 installation which I'm running right now.
Thanks a lot for that, just hope my Canon LBP3010 works fine!

---

