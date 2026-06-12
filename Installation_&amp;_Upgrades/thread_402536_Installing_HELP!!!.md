---
title: "Installing HELP!!!"
date: 2007-04-05
forum: Installation &amp; Upgrades
---

### Post by dragon52225 on 2007-04-05
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+bug/103435](https://bugs.launchpad.net/ubuntu/+bug/103435) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				Well, when I insert either the Alt/Regular CD, and choose any menu item that requires booting up the kernel, i get this error:

```

Int 14: CR2 f8000000 err 00000000 EIP c020bc34 CS 00000060 flags 00100007
Stack: c00f7c60 c03f12eb c0370be4 0000002 c00f7c69 000f7c60 00000000 00000000

```


Only thing that works in the menu is the memtest86+ because it doesn't depend on linux.  Any Idea?

Note: I am using a Compaq PC which has an AMD 3500+ (Venice). two sticks of 512 PC3200 DDR SDRAM (which passes memtest), an SATA hard drive, Realtek AC'97 Audio, and a Raedeon x1600.  The chipset of the motherboard is: ATI Radeon Xpress 200/1100/1150.  (Well thats what everest says under windows.

---

### Post by phidia on 2007-04-05
Myself I'd try another livecd knoppix, sabayon, dyne:bolic...and see if any of those get you to a desktop.

---

### Post by dragon52225 on 2007-04-05
Well...  I'm thinking if anyone can decipher the error message, because the only distro i'm intrested in is Ubuntu.  lol.

---

### Post by phidia on 2007-04-05
I googled the error you supplied before I posted my 1st response -0-hits.
That tells you something.
I wasn't suggesting flight from ubuntu but trying another livecd will provide more info
i.e either it will boot and run or it won't.

I should have asked this before but did you run md5sum on the iso before you burned it?

---

### Post by dragon52225 on 2007-04-06
Yes i did in fact, i checked the md5sum via digestIT2004 (on windows) for both normal and alternate install CDs.



Also, i just tried it on microsoft virtual PC 2007, and it works fine, so theres no issue with the CDs.

---

### Post by dragon52225 on 2007-04-06
from my bug report, if it helps anyone here, i just added:


> 

[http://lkml.org/lkml/2006/10/21/194](http://lkml.org/lkml/2006/10/21/194)

and maybe

[http://lkml.org/lkml/2006/9/21/104](http://lkml.org/lkml/2006/9/21/104)

Those sources might help (but all other people getting this error only occurs on ancient computers...)


[http://groups.google.com/group/fa.linux.kernel/browse_thread/thread/7126aa46fde16a9e/b5ba1bc1d5e0fe5a%23b5ba1bc1d5e0fe5a](http://groups.google.com/group/fa.linux.kernel/browse_thread/thread/7126aa46fde16a9e/b5ba1bc1d5e0fe5a%23b5ba1bc1d5e0fe5a)

[http://groups.google.com/group/linux.kernel/browse_thread/thread/e270d5b1a1974edc/d0f11e2e82370700%23d0f11e2e82370700](http://groups.google.com/group/linux.kernel/browse_thread/thread/e270d5b1a1974edc/d0f11e2e82370700%23d0f11e2e82370700)

Same things but with different responses...



> 

I don't know if this has anything to do with it:

[http://www.ravenbrook.com/project/mps/master/code/protlii3.c](http://www.ravenbrook.com/project/mps/master/code/protlii3.c)

[startcode]
/* Interrupt number 14 is Page Fault. */
#define TRAPNO_PAGE_FAULT 14
[endcode]

or maybe this?
[http://www.greenend.org.uk/rjk/2002/02/lostinterrupt.html](http://www.greenend.org.uk/rjk/2002/02/lostinterrupt.html)

[startquote]
Interrupts have numbers: on a normal PC, interrupt number 14 is used by the first IDE bus (/dev/hda and /dev/hdb) and interrupt 15 by the second IDE bus (/dev/hdc and /dev/hdd). So when the kernel receives interrupt 14 it only checks the first IDE bus; when it receives interrupt 15 it only checks the second.
[/endquote]

Most other sources say its a pagefault
[startquote]
......(interrupt 14) is triggered when the processor attempts to access a page, which is marked as not-present.
[/endquote]

From [http://www.delorie.com/djgpp/doc/ug/interrupts/inthandlers2.html](http://www.delorie.com/djgpp/doc/ug/interrupts/inthandlers2.html)

[startquote]
       So, what seems to be the problem? Well, the problem can be the demand paging itself. If, during the process, the paging unit determines that the required page table or the page itself is externally stored (swapped), then the i386 issues an interrupt 14 (0eh). Normally, this offers no trouble whatsoever as the operating system (or in our case the DPMI host) can load the respective page or page table into memory and resume its operation. However, this should not be done during the execution of an interrupt handler because DOS is a non-reentrant operating system. If an interrupt handler, any other functions it invokes or any variable it touches is swapped out then a page fault (exception 14) might be issued and your program goes to the little fishes...

       The solution, as you may have guessed, is to 'lock' the memory regions that must be available, telling the DPMI host to keep them in active memory at all times. This can be done with the Djgpp library functions '_go32_dpmi_lock_code()' and '_go32_dpmi_lock_data()'. How do you use them? It depends on the circumstances.
[/endquote]

In conclusion, I really don't know whats going on and i'm hoping a developer can sort this out for me.


---

### Post by dragon52225 on 2007-04-06
ISSUE SOLVED.  This bug is bogus: Ubuntu now works fine (i'm typing this on ubuntu) after i updated my BIOS.

---

### Post by neenjaoflove on 2007-04-22
how did you get it to work?

---

### Post by DooMRunneR on 2007-04-23
> **neenjaoflove said:**
> how did you get it to work?

Just make a Bios-Update, works for me....

---

### Post by KOTishe on 2007-05-13
Noop, BIOS updates don`t give my PC goodworking.

I`m disabled ACPI feature in boot options, and this only way :(

Any other distro cant boot normally on this PC (SuSe, Kubuntu)

My chipse ATI Radeon xpress 220

---

### Post by natrium on 2007-10-14
I had a similar problem booting ubuntu-server (6.10 and 7.04) on VMWare
and solved it following this

[http://www.virtualbox.org/ticket/289](http://www.virtualbox.org/ticket/289)

bye,
natrium

---

