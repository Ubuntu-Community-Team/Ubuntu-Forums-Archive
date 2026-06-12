---
title: "Using Par2+tbb with SabNZBd"
date: 2012-04-06
forum: Installation &amp; Upgrades
---

### Post by mercury80 on 2012-04-06
I want to upgrade my par2 program to [par2+tbb]("http://www.chuchusoft.com/par2_tbb/"). It is a multithreaded version of par2. I have downloaded [par2cmdline 0.4 with Intel Threading Building Blocks 2.2]("http://www.chuchusoft.com/par2_tbb/par2cmdline-0.4-tbb-20100203-lin64.tar.gz") and it seems to be working fine. This contains par2, libtbb.so, libtbb.so.2.

Now the question is how do I get SabNZBd to use it? How should I go about upgrading this correctly? (I'm currently graduating from the n00b end of Ubuntu-skilz.) Is it enough to just replace /usr/bin/par2 and stick libtbb.so & libtbb.so.2 in the same folder?

---

### Post by mercury80 on 2012-04-06
I did a test:
If you install the package libtbb2 from the repository you don't need the two files libtbb.so & libtbb.so.2.

Only did one test so I don't know how reliable this information is... But it worked with both verification and repair.

---

### Post by mercury80 on 2012-04-06
<SmallTalk>Well... this is getting ridiculous isn't it?! Me talking to my self -)</SmallTalk>

I installed libtbb2 from the standard repository and replaced /usr/bin/par2 with the par2 I downloaded from [http://www.chuchusoft.com/par2_tbb/]("http://www.chuchusoft.com/par2_tbb/")

It works very well and speeds up par2 checks quite a bit!

---

