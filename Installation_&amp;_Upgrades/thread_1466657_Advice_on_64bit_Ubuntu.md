---
title: "Advice on 64bit Ubuntu?"
date: 2010-04-30
forum: Installation &amp; Upgrades
---

### Post by fallenshadow on 2010-04-30
Hi guys,

I have downloaded the 64bit version of Ubuntu 10.04. I am currently using 8.10 32bit and I want to clean install 10.04 64bit version.

However the one thing that is putting me off is that I have heard if your PC has 1GB of RAM or less then 64bit won't run very good because it uses more RAM than 32bit. (my PC has 1GB)

So the question is: Does 64bit use more RAM than 32bit?

---

### Post by TyLLy_4 on 2010-04-30
Im not 100% sure of this but i don't think so. 

64bit only means that the information channels are wider. think of your computer system as a river. RAM memory would be like a dam where the watter is stored until it can flow downstream. In a 64 bit system everything is the same except the river is twice as wide. It will be faster because being wider it can carry more water (information) but you have to make sure that everything in your system absolutely positively is 64 bit compatible. Otherwise you will cause a bottle neck. 

This is my first reply so please don't flame me. 
Correct me if i said incorrect information. I love to learn.

---

### Post by fallenshadow on 2010-04-30
> This is my first reply so please don't flame me. 
Correct me if i said incorrect information. I love to learn.

Of course I would not flame you, I have no reason to! :)

I can't correct you because I don't know if this is true or not myself... thats why I asked here.

Ok I think I will mark this as solved unless anyone else has an answer to offer.

---

### Post by wbar2 on 2010-04-30
According to this, 1GB RAM is probably not enough to effectively run 64-bit. You should get at least 4GB:

[http://www.pcmag.com/article2/0,2817,2164442,00.asp](http://www.pcmag.com/article2/0,2817,2164442,00.asp)

---

### Post by fallenshadow on 2010-04-30
I found this on the net which seems to confirm that 64bit does in fact use more RAM.

> The main disadvantage of 64-bit architectures is that relative to 32-bit architectures, the same data occupies more space in memory (due to swollen pointers and possibly other types and alignment padding). This increases the memory requirements of a given process and can have implications for efficient processor cache utilization.

However I think I will still go ahead with the installation as it mentions you don't need 4GB or RAM but 64bit may use a small bit more than a 32bit OS.

---

### Post by odinb on 2010-04-30
For normal use, I see less than 1GB RAM allocated on my 64-bit Karmic and Lucid installs. Usually it sits at 0.7-0.8GiB used.

If you start more apps, or start image or video editing, you will need more RAM, but for everyday browsing and Office-use, it will work.

---

### Post by saini7002 on 2010-04-30
Yes,64-bit uses more RAM than 32-bit...for installing 64-bit you should have at least 2 GB RAM..if you go with 64-bit with 1 GB RAM it can give problems in future..better play safe..

---

### Post by oldos2er on 2010-04-30
> **wbar2 said:**
> According to this, 1GB RAM is probably not enough to effectively run 64-bit. You should get at least 4GB:

[http://www.pcmag.com/article2/0,2817,2164442,00.asp](http://www.pcmag.com/article2/0,2817,2164442,00.asp)

That article's for Win*, not Linux.

64-bit Ubuntu runs just fine with 2GB RAM. I don't have experience running it on less RAM, but in my opinion it's worth a try.

---

### Post by Icarus315 on 2010-04-30
I run 64-bit on an Intel system with 3GB RAM and it runs fine.  I also run it on two AMD systems both with 1GB RAM and again, it works fine.  Accessing memory above 4GB (including the video RAM on your graphics card in the total) is the primary reason for 64-bit.  However the way I look at it is that the processors are 64-bit capable so that is what I put on them.

---

### Post by fallenshadow on 2010-04-30
Thanks for the replies folks!

I will install 64bit but I may upgrade my RAM to 2GB in the summer. (thats the most my motherboard can handle)

I might report some feedback here of how im getting on.

---

### Post by dino99 on 2010-04-30
> **fallenshadow said:**
> Thanks for the replies folks!

I will install 64bit but I may upgrade my RAM to 2GB in the summer. (thats the most my motherboard can handle)

I might report some feedback here of how im getting on.

64 bits ? why you want it, that brink nothing real but slowness, at least 4 go are required to not continously overused the hdd. On the other hand, gnome, firefox and openoffice are very heavy and swallow ram.

so you can have the same ease by installing 32 bits an xfce desktop for example, better for your pc.

---

### Post by oldos2er on 2010-04-30
> **dino99 said:**
> 64 bits ? why you want it, that brink nothing real but slowness, at least 4 go are required to not continously overused the hdd. 

That's the exact opposite of my experience of 64-bit Ubuntu with 2GB RAM.

---

### Post by fallenshadow on 2010-05-03
Hi guys I installed 10.04 64bit today.

All is well but I can't play videos for some reason... even after installing codecs!

Any suggestions?

---

### Post by dino99 on 2010-05-03
> **fallenshadow said:**
> Hi guys I installed 10.04 64bit today.

All is well but I can't play videos for some reason... even after installing codecs!

Any suggestions?

here is one of the 64 issues  :P

---

### Post by fallenshadow on 2010-05-03
Ah... its ok now... seems to have sorted itself after logging out and back in.

However it takes a long time to actually start playing the video...its quite slow. Might be some issues with Totem.

---

### Post by cascade9 on 2010-05-03
> **dino99 said:**
> 64 bits ? why you want it, that brink nothing real but slowness, at least 4 go are required to not continously overused the hdd. 

Umm..no, not in my experince...or according any of the new (post 2008) 32bit vs 64bit benchmarks I've ever seen. 

Like oldos2er, I've found 64bit runs very well on 2GB (never tired it with 1GB, my 64bit capable machine has 2GB installed and I'm removing 1GB just for testing).

---

### Post by dino99 on 2010-05-03
> **fallenshadow said:**
> Ah... its ok now... seems to have sorted itself after logging out and back in.

However it takes a long time to actually start playing the video...its quite slow. Might be some issues with Totem.

issues are with flash, java, sound, ...

---

### Post by dino99 on 2010-05-03
> **cascade9 said:**
> Umm..no, not in my experince...or according any of the new (post 2008) 32bit vs 64bit benchmarks I've ever seen. 

Like oldos2er, I've found 64bit runs very well on 2GB (never tired it with 1GB, my 64bit capable machine has 2GB installed and I'm removing 1GB just for testing).

why not removing the last one  :P

---

### Post by cascade9 on 2010-05-03
> **dino99 said:**
> issues are with flash, java, sound, ...

On 64bit? *scoffs* I install the 64bit flash manually, and it works 100% on every site I've used. Java? No idea, I dont use java, but I havent heard of any major issues on recent 64bit releases. Sound? No issues here, and I've used several different sound cards on 64bit....

---

### Post by oldos2er on 2010-05-03
> **dino99 said:**
> issues are with flash, java, sound, ...

I install 64-bit flash and java. Haven't experienced any sound problems.

---

### Post by fallenshadow on 2010-05-03
Ok its weird but rebooting a couple of times seems to have sorted all the issues I was having. 

Now I just need to install proper Java. :)

---

