---
title: "Partitioning problems on Toshiba Tecra M4"
date: 2007-03-02
forum: Installation &amp; Upgrades
---

### Post by narutomonkeyfreak on 2007-03-02
Help! I'm a total Linux noob (may I soon learn the awesomeness that is Linux), and I tried to install Ubuntu 6.10 on my computer 5 times now, and my computer acts oddly every time I get to partitioning my hard drive. I ran it for about 4 hours the first time, 5 hours the second, 3 the third, and an hour the last two times. My friend installed it on his computer, which is identical to mine and it took 45 minutes for him, I figured it might be the CD, so I used his on the last two tries, and the same problem occured. Anyone have any idea what might have went wrong??

---

### Post by floke on 2007-03-02
You'll have to be slightly more specific about what you actually did and what actually happened before anyone can help you. How did you partition the HDD for instance? What installation method did you use etc.?

---

### Post by narutomonkeyfreak on 2007-03-02
I burned the ISO from this webstie, and tried to install from there, I'm trying install Ubuntu 6.10. My computer is fine until the partitioning part. While its partitioning, the first time I went on the internet and everything just fine, the last four times I didn't attempt to. How long does  partitioning it normally take? Should I try to partition my drive some other program then install?

---

### Post by floke on 2007-03-02
Right, before partitioning there are some important things you need to do.

(a) Defragment windows;
(b) Run a Scandisc in windows to sort out any disc errors 
(c) Check the burned disc for errors (select from opening menu - if you get a message indicating that any checksums failed then you need to burn it again - I had a few problems from bad burns early on - do it at a low speed).

Also - what version of ubuntu are you using??

---

### Post by narutomonkeyfreak on 2007-03-02
I'm using Windows currently, and I'm trying to set upa double boot (Windows for school programs, Linux for everything else). I will try what you suggested.

---

### Post by floke on 2007-03-02
And what version of Ubuntu are you trying??

---

### Post by narutomonkeyfreak on 2007-03-02
6.10 Edgy

---

### Post by floke on 2007-03-02
Ok, so that should be fine (I was worried you might have been trying the 7.04, which has a flaky partitioner). So how are you going about the partitioning. Using Gparted (system/admin/gparted) you first need to shrink the Windows partition - then you need to install via clicking on the desktop icon, and select the 'install using largest available space option' - is this what you have been doing?

---

