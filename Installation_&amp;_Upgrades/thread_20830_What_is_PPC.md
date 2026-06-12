---
title: "What is PPC??"
date: 2005-03-18
forum: Installation &amp; Upgrades
---

### Post by bigblop on 2005-03-18
What does PPC stand for???

---

### Post by bored2k on 2005-03-18
[QUOTE=bigblop]What does PPC stand for???[/QUOTE]
 PowerPC (Macintosh processor)
[http://www.acronymfinder.com/af-query.asp?acronym=ppc&String=exact&page=3](http://www.acronymfinder.com/af-query.asp?acronym=ppc&String=exact&page=3)

---

### Post by DJ_Max on 2005-03-18
Not necessarily a macintosh, but any computer that uses the IBM's PowerPC core, such as Pegasos, Mac's, IBM eSeries. Apple(mac) uses a modified IBM PowerPC processor made by Motorola/Freescale.
[http://www-03.ibm.com/chips/products/powerpc/](http://www-03.ibm.com/chips/products/powerpc/)

PPC is an "Architecture". For example, your standard x86 would be an Intel or AMD processor.

---

### Post by bored2k on 2005-03-18
[QUOTE=DJ_Max]Not necessarily a macintosh, but any computer that uses the IBM's PowerPC core, such as Pegasos, Mac's, IBM eSeries. Apple(mac) uses a modified IBM PowerPC processor made by Motorola/Freescale.
[http://www-03.ibm.com/chips/products/powerpc/](http://www-03.ibm.com/chips/products/powerpc/)

PPC is an "Architecture". For example, your standard x86 would be an Intel or AMD processor.[/QUOTE]
 Also stands for Personal Pissing Contest and Pokémon Puzzle Challenge ^_^ , depends how you look at it ;) .

---

### Post by DJ_Max on 2005-03-18
[QUOTE=bored2k]Also stands for Personal Pissing Contest and Pokémon Puzzle Challenge ^_^ , depends how you look at it ;) .[/QUOTE]
ROFL, yeah I didn't think of those. I just thought he was talking about computers. :-o

---

### Post by bored2k on 2005-03-18
[QUOTE=DJ_Max]ROFL, yeah I didn't think of those. I just thought he was talking about computers. :-o[/QUOTE]
 acronymfinder.com ;)

---

### Post by az on 2005-03-18
Linux runs on more than 20 architectures.

Linus Torvalds uses PPC:

[http://www.zdnet.com.au/news/0,39023165,39183867,00.htm](http://www.zdnet.com.au/news/0,39023165,39183867,00.htm)

There are other Unix platforms that support many other more:
[http://www.netbsd.org/Ports/](http://www.netbsd.org/Ports/)

---

### Post by Jad on 2005-03-19
How good PPC arch compared to others? specially for home/office use?

---

### Post by std on 2005-03-19
I personally consider PPC architecture to be fairly superior to the x86 arch. Mainly because the current PowerPC architecture is not an 16-bit architecture that evolved into a 32-bit architecture that evolved into a 64-bit architecture. Among the PPC features that I liked there's a whooping number of registers and a wiser instruction set, although the last one is quite subjective. In fact, a 1.15 GHZ iMac is a good pretty close competitor for my 2.6 @ 2.87 GHZ Pentium 4.

---

### Post by DJ_Max on 2005-03-19
When comparing x86 to a PPC, you are comparing to really different processors. One is CISC(x86) based, while the other is RISC(PPC) based. Thats one reason why clock speeds are totally different.
CISC processors complete a task in as few lines of assembly as possible. It places emphasis on hardware. While RISC places it on software. RISC processors only use simple instructions that can be executed within one clock cycle. The RISC reduced instructions require less transistors of hardware space than the complex instructions, leaving more room for general purpose registers.

Also, RISC Register to register "LOAD" and "STORE" instructions allow it to reduce the amount of work that the computer must perform. On the other hand with CISC processors "Memory-to-memory", when something is done, the processor erases the registers. If something else needs to use it, it has to re-load it.

This is why you see clocl speeds vary, ie my iMac is at 400MHZ, but runs a lot faster, then say a Celeron at 1024MHZ(1GHZ).

I also forgot to mention, you'll notice longer compile times due to GCC. RISC processors take more machine-code instructions to complete certain tasks. It takes GCC longer to determine the instructions that need to be issued and to order them for best performance. It has to issue separate instructions for loading the contents of the first into a register, doing the same for the second, issuing the add instruction, and copying the result back to memory.

---

