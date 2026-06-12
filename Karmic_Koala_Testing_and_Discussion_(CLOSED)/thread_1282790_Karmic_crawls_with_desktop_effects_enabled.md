---
title: "Karmic crawls with desktop effects enabled"
date: 2009-10-04
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by ddarsow on 2009-10-04
I have been running Ubuntu for several years now with very little trouble. For some reason enabling desktop effects on 9.10 Beta (2.6.31-11 Kernel) results in the entire system being excruciatingly slow. I suspect it likely has something to do with the Nvidia driver, but it is only a guess. 

I am dual booting with 9.04 on the same machine and 9.04 is flawless and blazing fast. The computer is a DELL D620 with a 1.83 Ghz Centrino Duo and 2Gb of RAM.

Is anyone else experiencing this problem? Any ideas on the cause?

---

### Post by FuturePilot on 2009-10-04
Might be this bug.
[https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers-180/+bug/391461]("https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers-180/+bug/391461")

---

### Post by ddarsow on 2009-10-12
Even after numerous updates (including 2 kernel progressions) I am still having extreme performance issues with desktop effects enabled in 9.10

---

### Post by PRGUY85 on 2009-10-12
Been having same problem since the alphas.  Don't know if this will get fix for release time.

---

### Post by go7Ul1ai on 2009-10-12
quick fix: disable desktop effects

---

### Post by PRGUY85 on 2009-10-12
> **lee.jarratt said:**
> quick fix: disable desktop effects

Yes it is pal...yet we are assuming we want that functionality we had on all previous releases.

---

### Post by go7Ul1ai on 2009-10-12
> **PRGUY85 said:**
> Yes it is pal...yet we are assuming we want that functionality we had on all previous releases.

I was assuming you didn't want Karmic to "crawl"..

---

### Post by ddarsow on 2009-10-12
> **lee.jarratt said:**
> quick fix: disable desktop effects

That is not exactly what I would call a "fix" of any sort! Also, even that is easier said than done as performance and window drawing becomes so slow that selecting radio buttons, typing in text boxes, or even moving a window becomes next to impossible.

---

### Post by PRGUY85 on 2009-10-12
> **lee.jarratt said:**
> I was assuming you didn't want Karmic to "crawl"..

I was assuming we could get a better answer than sarcasm. But that's fine.

---

### Post by ronacc on 2009-10-12
must be specific to certain hardware , I have not seen this with any of the 2.6.31 kernels ( currently -13 ) and amd64 4600 with nvidia 7600gs and nvidia 185.18.36 driver .

---

### Post by ddarsow on 2009-10-12
> **ronacc said:**
> must be specific to certain hardware , I have not seen this with any of the 2.6.31 kernels ( currently -13 ) and amd64 4600 with nvidia 7600gs and nvidia 185.18.36 driver .

So, any thoughts on how to track down the culprit?

---

### Post by go7Ul1ai on 2009-10-12
My system works fine.

---

### Post by ronacc on 2009-10-12
> **ddarsow said:**
> So, any thoughts on how to track down the culprit?

those who are having problems should compare hdw and see if there are things that you all have in common , also try switching drivers , you can get other versions from [http://www.nvidia.com/Download/index.aspx?lang=en-us ](http://www.nvidia.com/Download/index.aspx?lang=en-us ) . note some may require patching for the .31 kernel , search this forum for hints . also check your /home/.xsession-errors for possible problems .

---

### Post by lovinglinux on 2009-10-13
For me version 185 is really fast, even faster then Jaunty with 180. But it has a bug that prevents Ubuntu from loading. It stalls before the gdm. So I'm using 173, which works, but is so slooooow.

---

