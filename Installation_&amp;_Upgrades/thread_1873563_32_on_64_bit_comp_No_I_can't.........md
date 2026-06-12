---
title: "32 on 64 bit comp? No I can't........"
date: 2011-11-01
forum: Installation &amp; Upgrades
---

### Post by dede468 on 2011-11-01
I have been running virtually all variants of Ubuntu on various computers for the past five years now but all my machines have been 32 bit.  Two days ago I bought a new computer with a 64 bit i5 Intel processor - my first 64 bit machine, so taking Ubuntu home page at it's word, set about installing Kubuntu 11.10 32 bit which I had been running on my old Intel machine. Before the cursor appeared I got a message on screen saying installation could not continue as the files were empty.  Curious....

I tried Ubuntu 10.10 32 bit with exactly the same result.  Then Xubuntu 32 bit and then Ubuntu 8.04 32 bit............

In the end I found a copy of 10.10 64 bit which I had downloaded by mistake last year.  

It worked. 

I then downloaded 11.10 64 bit Kubuntu which also worked.

Fact is that although Ubuntu assures us that 32 bit works on a 64 bit machine, I have been unable to find a single copy of 32 bit in any flavour which will run on my new 64 bit machine whereas ALL 64 bit versions I have now downloaded run perfectly.

I'd like to know if this is a new trend with 64 bit machines or is it just me???

---

### Post by Ricx94 on 2011-11-01
I've never heard of anything like this happening...i have installed 32-bit ubuntu on a few 64-bit capable machines, and had no problem.

I wonder what exactly happened...?

---

### Post by cbowman57 on 2011-11-01
Makes me wonder if there is some kind of 32-bit compatibility switch in the BIOS?

---

### Post by dede468 on 2011-11-02
Well I've had a good look at the bios and there's nothing glaringly obvious for compatibility but as I don't profess to understand the bios anyway, I could have missed something.  My first thought however is that although I don't know much, many users know even less and won't do any more than try a 32 bit disc and decide that Ubuntu doesn't work. I've now tried Fedora and Ubuntu Studio with similar results. Message is generally that it can't find the file system so is dropping me to a shell which will simply frighten many users into staying with Windows.

:confused:

---

### Post by cbowman57 on 2011-11-02
Might be a buggy bios.  Any updates on the motherboard support page?

It is puzzling.

---

### Post by dede468 on 2011-11-10
Been through everything I can find. No updates for bios, no problems reported with bios etc. Other than the aforementioned disregard for 32 bit OS, all 32 bit progs loaded into the 64 bit OS work perfectly. Very strange indeed.

---

### Post by lisati on 2011-11-10
Weird, possibly some kind of backwards-compatibility issue. I did notice [here]("http://ark.intel.com/products/42915/Intel-Core-i5-750-Processor-%288M-Cache-2_66-GHz%29") the following comment, which might be a clue of dubious relevance:
> 64-bit computing on Intel® architecture requires a computer system with a processor, chipset, BIOS, operating system, device drivers and applications enabled for Intel® 64 architecture. Processors will not operate (including 32-bit operation) without an Intel 64 architecture-enabled BIOS. Performance will vary depending on your hardware and software configurations. Consult with your system vendor for more information.

---

