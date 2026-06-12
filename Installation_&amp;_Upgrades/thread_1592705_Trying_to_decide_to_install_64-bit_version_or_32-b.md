---
title: "Trying to decide to install 64-bit version or 32-bit version with PAE"
date: 2010-10-10
forum: Installation &amp; Upgrades
---

### Post by yakinikku on 2010-10-10
what would you guys recommend? my laptop currently has 8GB of RAM and I wouldn't want that going to waste.  I have read about the issues with flash on the 64 bit versions of buntu.  Would you recommend going 64-bit or 32-bit with PAE? also, does the 10.10 kernel have PAE enabled by default?

TIA guys

:guitar:

---

### Post by 73ckn797 on 2010-10-10
I have had good success running 32 bit in a 64 bit machine. The PAE kernel shows 5.9 Gib of 6 Gib. I notice no big difference in speed with what my requirements have been.

I have no problems with Flash or Java, except since using 10.04, there are minor issues with several Java photo upload programs but those are not keeping them from working. I just installed 10.10 and flash and Java are working great. The 10.10 install gives the option to install Flash and other stuff. It also gives the option to install any updates that are already available.

I do not think you will be disappointed running the 32bit unless you are stuck with the idea that the 64 is an advantage over the 32. It has performed well for me and my system.

I have not installed 10.10 on the 64 bit machine yet, but it seems to be fine on my 32bit laptop.

---

### Post by peakpc on 2010-10-10
Go 64bit, I did back in 9.04 with my wimpy old laptop. Now I have an I5 and 4GB with 10.10 (today) and it's going strong. I don't think that there is a speed difference unless you doing intense stuff like video rendering (which I do occasionally) but it is the wave of the future (now).

---

### Post by 73ckn797 on 2010-10-10
> **peakpc said:**
> Go 64bit, I did back in 9.04 with my wimpy old laptop. Now I have an I5 and 4GB with 10.10 (today) and it's going strong. I don't think that there is a speed difference unless you doing intense stuff like video rendering (which I do occasionally) but it is the wave of the future (now).

I agree with what you are saying. Eventually 64bit will be the standard and I will go there. For now 32bit does the job for my needs.

---

### Post by yakinikku on 2010-10-11
> **peakpc said:**
> Go 64bit, I did back in 9.04 with my wimpy old laptop. Now I have an I5 and 4GB with 10.10 (today) and it's going strong. I don't think that there is a speed difference unless you doing intense stuff like video rendering (which I do occasionally) but it is the wave of the future (now).

thanks for the reply, its not about a speed difference, more about stability.  do you have any issues with flash?

my specs are an i7-720, 8GB of ram.

---

### Post by yakinikku on 2010-10-11
> **73ckn797 said:**
> I have had good success running 32 bit in a 64 bit machine. The PAE kernel shows 5.9 Gib of 6 Gib. I notice no big difference in speed with what my requirements have been.

I have no problems with Flash or Java, except since using 10.04, there are minor issues with several Java photo upload programs but those are not keeping them from working. I just installed 10.10 and flash and Java are working great. The 10.10 install gives the option to install Flash and other stuff. It also gives the option to install any updates that are already available.

I do not think you will be disappointed running the 32bit unless you are stuck with the idea that the 64 is an advantage over the 32. It has performed well for me and my system.

I have not installed 10.10 on the 64 bit machine yet, but it seems to be fine on my 32bit laptop.

its not so much as a speed advantage that I am thinking about, more like future proofing.  and considering i have the hardware i figure why not, but after reading a few threads about people having the system crash due to flash i am asking.  i noticed that flash with native 64 bit support is still in beta, i am just trying to avoid having a mess on my hands.

---

### Post by dino99 on 2010-10-11
less trouble with pae kernel

---

### Post by yakinikku on 2010-10-11
> **dino99 said:**
> less trouble with pae kernel

so far thats 2 votes for the 32 bit version and 1 for the 64 bit.  anyone else care to chime in?

---

### Post by BaffledMollusc on 2010-10-11
I've been running the 64-bit version for about a year on both my home computer and my work computer. Never had any problems - perfectly stable, all software seems to work fine.

---

### Post by cascade9 on 2010-10-11
I've been using 64-bit for a few years now, no major issues. BTW, one system had 2GB or RAM, you dont 'need' 4GB+ for 64bit to work well. Flash has been fine, before I was using the 64bit preview (or whatever they called it) now on flash 'square' 64bit. 

> **peakpc said:**
> Go 64bit, I did back in 9.04 with my wimpy old laptop. Now I have an I5 and 4GB with 10.10 (today) and it's going strong. I don't think that there is a speed difference unless you doing intense stuff like video rendering (which I do occasionally) but it is the wave of the future (now).

It is on audio encoding, video encoding, etc where 64bit has the most improvement over 32bit. But even on 'normal' tasks 64bit can be 5-10% faster- 

[http://www.tuxradar.com/content/ubuntu-904-32-bit-vs-64-bit-benchmarks](http://www.tuxradar.com/content/ubuntu-904-32-bit-vs-64-bit-benchmarks)

---

### Post by yakinikku on 2010-10-12
> **cascade9 said:**
> I've been using 64-bit for a few years now, no major issues. BTW, one system had 2GB or RAM, you dont 'need' 4GB+ for 64bit to work well. Flash has been fine, before I was using the 64bit preview (or whatever they called it) now on flash 'square' 64bit. 



It is on audio encoding, video encoding, etc where 64bit has the most improvement over 32bit. But even on 'normal' tasks 64bit can be 5-10% faster- 

[http://www.tuxradar.com/content/ubuntu-904-32-bit-vs-64-bit-benchmarks](http://www.tuxradar.com/content/ubuntu-904-32-bit-vs-64-bit-benchmarks)

so i think i am going to go ahead with the 64 bit install, seeing that flash seems to be ok.

one last question, can you install 32 bit applications on the 64 bit version without issue?  what i really mean by that is does the software have to be redesigned just to run on the 64 bit version (not to necessarily make use of the benefits of 64 bit), or can it just run without issue?

---

### Post by cascade9 on 2010-10-12
Yes, you can run 32bit software on 64bit without problems. Some people dont like the using the "dkpg -i --force-architechture" option, and there are sometimes more elegant solutions, like this- 

[http://2dboy.com/forum/index.php?topic=1464.0](http://2dboy.com/forum/index.php?topic=1464.0)

---

### Post by yakinikku on 2010-10-12
> **cascade9 said:**
> Yes, you can run 32bit software on 64bit without problems. Some people dont like the using the "dkpg -i --force-architechture" option, and there are sometimes more elegant solutions, like this- 

[http://2dboy.com/forum/index.php?topic=1464.0](http://2dboy.com/forum/index.php?topic=1464.0)

ok, so its the same process as was for the LPIA architecture that dell was using with their branded 8.04 on the mini 9.  thanks guys!

---

### Post by BigCajun on 2010-10-12
You can take this as another vote for 64-bit. If you go 32-bit with PAE, understand that you will only be able to access the extra RAM within an application if the application is compiled to make use of the PAE enabled in the kernel.

I don't know of any specific examples where this is the case under Linux (not saying there aren't), but I do know that the Sun/Oracle 32-bit Java VM is NOT compiled with the PAE extensions on Windows 32-bit platforms. This means that even if you run Windows 32-bit systems with PAE enabled, a single Java application still won't be able to access more than 1536MB of RAM, no matter how much you have on that system.

I realize this is a very specialized and isolated instance, just something to think about. Again, I don't know of any Linux apps that are specifically not capable of making use of PAE.

---

### Post by yakinikku on 2010-10-12
> **BigCajun said:**
> You can take this as another vote for 64-bit. If you go 32-bit with PAE, understand that you will only be able to access the extra RAM within an application if the application is compiled to make use of the PAE enabled in the kernel.

I don't know of any specific examples where this is the case under Linux (not saying there aren't), but I do know that the Sun/Oracle 32-bit Java VM is NOT compiled with the PAE extensions on Windows 32-bit platforms. This means that even if you run Windows 32-bit systems with PAE enabled, a single Java application still won't be able to access more than 1536MB of RAM, no matter how much you have on that system.

I realize this is a very specialized and isolated instance, just something to think about. Again, I don't know of any Linux apps that are specifically not capable of making use of PAE.

now thats some good info.  :guitar:

---

