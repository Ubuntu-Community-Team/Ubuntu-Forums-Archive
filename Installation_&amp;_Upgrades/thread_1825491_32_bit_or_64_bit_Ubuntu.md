---
title: "32 bit or 64 bit Ubuntu"
date: 2011-08-15
forum: Installation &amp; Upgrades
---

### Post by Phil Binner on 2011-08-15
I installed Ubuntu 11.04 on my Aspire 7520 laptop. Very successful after a few glitches, thanks to all concerned on this forum for sorting that.  I am now installing more Ram. The system will take 4gb, which I understand will be recognised by a 32 bit system.

I can't actually remember whether I originally installed the 32 or 64 bit system, and I don't know what the system requirements for 64 bit are. The processor is an AMD Athlon 64 Dual Core.

So mu questions are:

1. How do I find out which version I have.
2. Is there an easy upgrade path from 32 bit to 64 bit that won't involve re-installing everything.
3. Given that the max ram for this machine is 4gb, it there any point in going to 64 bit if I'm not already there.

Thanks in advance.

Phil Binner

---

### Post by jerrrys on 2011-08-15
number #1

open a terminal and enter:

**uname -a **

number #3

[http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=32+vs+64+bit&sa=Search&cof=FORID:9#971](http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=32+vs+64+bit&sa=Search&cof=FORID:9#971)

---

### Post by haqking on 2011-08-15
> **jerrrys said:**
> number #1

open a terminal and enter:

**uname -a **

number #3

[http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=32+vs+64+bit&sa=Search&cof=FORID:9#971](http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=32+vs+64+bit&sa=Search&cof=FORID:9#971)

+1

except **uname -m** is more specific and shows just architecture.

2. no not really

3. there is no point not to go to x64 IMO, though people debate it, there is the option of PAE, and some support issues for 32 bit apps.  However in my experience and i run $gb x64 is very stable, and everything i do is supported with issue.

---

### Post by Phil Binner on 2011-08-15
The answer to uname -m was "i686".

The answer to uname -a was

Linux Middlebin-Ubuntu 2.6.38-10-generic #46-Ubuntu SMP Tue Jun 28 15:05:41 UTC 2011 i686 athlon i386 GNU/Linux


Is that telling me I already have 64 bit.

---

### Post by haqking on 2011-08-15
> **Phil Binner said:**
> The answer to uname -m was "i686".

The answer to uname -a was

Linux Middlebin-Ubuntu 2.6.38-10-generic #46-Ubuntu SMP Tue Jun 28 15:05:41 UTC 2011 i686 athlon i386 GNU/Linux


Is that telling me I already have 64 bit.

no you dont. the uname -m extracts the architecture part from the uname -a result.

i686 etc.

you are looking for x86_64 for 64 bit or amd64

---

### Post by jerrrys on 2011-08-15
to remove any doubt, in terminal enter **lshw**

go to cpu>width

it will say either 32 or 64

you have 32B installed, this is just another way to see your cpu

---

### Post by Phil Binner on 2011-08-15
Sorry, one more question, will my computer run 64 bit Ubuntu. It's an Acer Aspire 7520 with  an AMD Athlon 64 Dual-Core processor.

---

### Post by collisionystm on 2011-08-15
> **Phil Binner said:**
> Sorry, one more question, will my computer run 64 bit Ubuntu. It's an Acer Aspire 7520 with  an AMD Athlon 64 Dual-Core processor.

yes it will run 64 bit

---

### Post by oldos2er on 2011-08-15
> **Phil Binner said:**
> Sorry, one more question, will my computer run 64 bit Ubuntu. It's an Acer Aspire 7520 with  an AMD Athlon 64 Dual-Core processor.

**cat /proc/cpuinfo** will tell you; look for the lm flag.

---

### Post by Phil Binner on 2011-08-15
OK, thanks guys. I guess I'm going to go with it. I've not got too much invested in this system yet, so it's probably better to bite the bullet now and get the upgrade done.

I'll call this one solved then.

---

