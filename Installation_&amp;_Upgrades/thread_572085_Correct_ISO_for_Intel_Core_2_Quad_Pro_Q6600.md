---
title: "Correct ISO for Intel Core 2 Quad Pro Q6600?"
date: 2007-10-10
forum: Installation &amp; Upgrades
---

### Post by heavyDave on 2007-10-10
Hi.

I just want to make sure that I'm downloading the correct ISO to install on a new Intel Core 2 Quad Pro Q6600. Am I correct in understanding that the ubuntu-7.04-desktop-amd64.iso will work? Or should I be downloading the ubuntu-7.04-desktop-i386.iso?

Thanks in advance.

---

### Post by chewearn on 2007-10-10
Both iso should work.

Though, if this is the first time you are trying ubuntu, and linux in general, I suggest to try the i386.

As I understand it, with the amd64 (64-bit version) you might have to make some extra (possibly frustrating) effort to get everything working.

---

### Post by heavyDave on 2007-10-10
Thanks for the reply. After doing some scouring of the forum here I found a few other posts that pointed out that both versions will work and that suggested that there are some possible difficulties with the 64bit version. I don't have time available to play around on unexpected problems, so I'll be going with the easier solution :)

*proceeds to download i386 version*

---

### Post by sebastjanp on 2008-01-25
With 32 version you will only acces 3,5 GB of your RAM

---

### Post by chewearn on 2008-01-25
That last post from the OP "heavyDave" was more than three months ago, and he hasn't been posting since.  Wonder how the ubuntu experience has been for him?

Anyway, I have (since gutsy release) been moving my installations from 32-bit to 64-bit, and I have to say, it has been great.

---

### Post by houdodu on 2008-05-13
AstalaVista, how many difficulties have you had?

Are the advantages in the 64bit version big enough to warrant the difficulties? Is it primarily just extra ram available? Will some programs just not run at all?

I'm going to build a system today with that processor, but I haven't decided which version of ubuntu to get yet.

---

### Post by chewearn on 2008-05-13
> **houdodu said:**
> AstalaVista, how many difficulties have you had?

Are the advantages in the 64bit version big enough to warrant the difficulties? Is it primarily just extra ram available? Will some programs just not run at all?

I'm going to build a system today with that processor, but I haven't decided which version of ubuntu to get yet.


The remaining difficulty I have is sun-java.  I need to access banking website, which uses Java encryption.  There is simply no 64-bit version of sun-java mozilla plug-in (it's a six year old problem).  Fortunately, I have an old PC, which I keep a 32-bit install just for this purpose.

I still use 64-bit (now with Hardy) because:
1. it support Folding@Home SMP.
2. I occasionally encode video, and the extra boost is worth it.
3. I just can't stand wasting all that processing capability :mrgreen:

.

---

### Post by Sef on 2008-05-13
> The remaining difficulty I have is sun-java. I need to access banking website, which uses Java encryption. There is simply no 64-bit version of sun-java mozilla plug-in....

That is the biggest problem with amd64-bit.  [OpenJDK]("http://ubuntuforums.org/showthread.php?t=774956") works well, but there are a few sites that it don't work well with.

---

### Post by chewearn on 2008-05-14
> **Sef said:**
> That is the biggest problem with amd64-bit.  [OpenJDK]("http://ubuntuforums.org/showthread.php?t=774956") works well, but there are a few sites that it don't work well with.

Yeah, I have been reading about the OpenJDK last week hoping it will finally work in the banking site.

Unfortunately, the one thing required for banking, the encryption component, is not open sourced by Sun when they free sun-java to become OpenJDK.  The reason being, encryption part is licensed from third party, and do not have the right to open source it.

However, the FOSS community is working hard to build these from scratch and I think/hope by the end of the year, it will be fully available in OpenJDK.

---

