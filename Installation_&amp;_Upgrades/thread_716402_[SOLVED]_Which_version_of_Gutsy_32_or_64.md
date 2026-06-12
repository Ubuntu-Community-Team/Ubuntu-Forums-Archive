---
title: "[SOLVED] Which version of Gutsy? 32 or 64?"
date: 2008-03-05
forum: Installation &amp; Upgrades
---

### Post by Steve Angelidis on 2008-03-05
Hello all from a total Linux rookie.

I have been running the 64 bit version of Gutsy for the last week or so. I botched an attempt at a dual boot install and now have an Ubuntu only machine. Oh well, nothing like learning to swim by falling overboard in deep water.

I have read since that the 32 bit version of Gutsy is better behaved than the 64 bit.

Overall, 64 bit Ubuntu has worked well for me except:
a) I can't change my password (little circle just keeps on turning and turning)
b) I can't write data DVDs (goes through the motions but the disk produced is undetectable in any machine.OTOH I can make a data CD! Go figure.)
c) Webcam doesn't work
d) Who knows what I haven't discovered yet

Today I bought the latest issue of Linux Magazine and it included a CD of 32 bit Gutsy. Do you think its worth trying it out? Or am I likely to have the same or similar little annoyances? Should I stay with 64 bit and try to iron things out bit by bit?

Machine is Toshiba A200 laptop, Core 2 Duo T5300, 2 G ram, 200 G HD.

Thanks for any advice.(Sorry to be so longwinded.)

stevea

---

### Post by Rohan sehgal on 2008-03-06
Dear sir,
You have a great question there:KS:KS But you have system hardware that might not be compatible with 64-bit OS. Go for 32-bit it's fast and much more reliable. Also many of the applications might not support a 
64-bit system.

Anything more?
please contact me:-
[email]rohan.upclose@gmail.com[/email]

---

### Post by Kerin on 2008-03-06
64's only a great idea if you do a lot of video encoding, I hear.

---

### Post by Meatshield on 2008-03-06
Just like with Windows, x64 Ubuntu hasn't really matured. It has to use it's own deb packages, and x64 doesn't work really anyways if the programs don't support parallel processing (a fancy term for "a program advanced enough to use multiple cores of a processor to run a program instead of just one"). If you're not a programmer, parallel processing is a real pain in the butt to do, so not a lot of people do it, despite the fact there are a TON of computers out there that have multiple cores in them.

So for that reason alone, stick with x86*. I have a quad core for my desktop and I still use x86

*While it's kind of odd if you don't know PC architectures well and their history, the technical terms for a single core processor are it's a 32 bit processor, but it's of the architecture type x86, where as multi-core are 64 bit processors and x64 architecture. Little lesson in terminology there but it never hurts to learn! :)

---

### Post by jimv on 2008-03-06
A 64bit OS isn't really meant to be faster.  It's meant to be able to address more than 4 GB of RAM, which is the limit of a 32 bit OS.

---

### Post by Kerin on 2008-03-06
32-bit Linux can address 32GB, if memory serves.  The limits in Windows are purely by Microsoft's machination.

---

### Post by NightwishFan on 2008-03-06
64-bit is faster than 32-bit in my experience. There are about as many bugs for 64bit as 32-bit. If you have a processor for it use 64-bit for the added punch.

---

### Post by Steve Angelidis on 2008-03-06
Thanks all.

I've gone with the majority and installed the i386 Gutsy.

Went smooth. Seem to be fewer issues so far.

I'll bring those up later after I study them a little more.

stevea

---

