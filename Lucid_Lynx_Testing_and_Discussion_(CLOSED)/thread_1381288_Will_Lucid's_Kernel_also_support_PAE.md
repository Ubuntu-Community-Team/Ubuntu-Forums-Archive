---
title: "Will Lucid's Kernel also support PAE?"
date: 2010-01-14
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by kevpan815 on 2010-01-14
I noticed that Karmic's Kernel is now supporting Physical Address Extension!

Will Lucid's Kernal support Physical Address Extension as well?

---

### Post by Ibidem on 2010-01-14
Here's the short answer (/boot/config-2.6.32-10-generic):
# CONFIG_HIGHMEM64G is not set

That means, no PAE in the standard kernel.

Apparently the server kernel is PAE enabled.
 
There's also linux-generic-pae, which should be PAE enabled
But what's the trouble with looking at the config file and finding the string CONFIG_HIGHMEM64G or searching the repositories for "PAE"?
Those give you the answer.

Ibidem

---

### Post by kevpan815 on 2010-01-14
I am currently back at 9.10 and am waiting for the Official Alpha 2 Release Announcement to be posted in this Forum in order to go back to 10.04!

---

### Post by Merk42 on 2010-01-14
I don't want to sound rude or anything, I'm just asking:

What exactly is the point anymore of PAE? If you want to use 4GB+ of RAM why not use the 64-bit version? (which has other advantages)

---

### Post by VMC on 2010-01-14
> **Merk42 said:**
> I don't want to sound rude or anything, I'm just asking:

What exactly is the point anymore of PAE? If you want to use 4GB+ of RAM why not use the 64-bit version? (which has other advantages)

But only for 64-bit machines, correct? I'm assuming your referring to the OP's, DELL XPS 630, as being a 64-bit.

I still have a 32-bit machine but only 2gigs ram and don't need PAE.

---

### Post by scheuri on 2010-01-15
> **Merk42 said:**
> I don't want to sound rude or anything, I'm just asking:

What exactly is the point anymore of PAE? If you want to use 4GB+ of RAM why not use the 64-bit version? (which has other advantages)

I personally see at least the following reasons:
[LIST]
[*]You have older hardware (CPU to be exact) which is not 64bit capable, but you have more than 3.6 GB of RAM.
[*]Although everyone tells me that 64bit is flawless, it is not. You still run into problems with certain applications when you use 64bit OS. So maybe someone has recent hardware, with loads of RAM, but does not want or does not can switch to 64bit
[/LIST]

Sure...there might not many people here who fall into those categories, but PAE has been around for alonge time, is rather stable and there are still people using it (and are happy with it).

The only question valid IMHO would be, of Ubuntu really needs to support that. Ubuntu as a distribution might decide to disable PAE in their kernels and not provide any kernels in which PAE is enabled (for whatever reason).
However, PAE itself is surely still in use and necessary.

my 2 rappen
scheuri

---

### Post by pressureman on 2010-01-15
Remember, although PAE allows 32-bit boxes to utilise more than 4GB of memory *in total*, each process will still only be able to address a maximum of 4GB virtual memory.

If you're working on really big datasets that are bigger than 4GB, you really have no choice other than to move to 64-bit.

---

### Post by cariboo on 2010-01-15
> **scheuri said:**
> I personally see at least the following reasons:
[LIST]
[*]You have older hardware (CPU to be exact) which is not 64bit capable, but you have more than 3.6 GB of RAM.
[*]Although everyone tells me that 64bit is flawless, it is not. You still run into problems with certain applications when you use 64bit OS. So maybe someone has recent hardware, with loads of RAM, but does not want or does not can switch to 64bit
[/LIST]

Sure...there might not many people here who fall into those categories, but PAE has been around for alonge time, is rather stable and there are still people using it (and are happy with it).

The only question valid IMHO would be, of Ubuntu really needs to support that. Ubuntu as a distribution might decide to disable PAE in their kernels and not provide any kernels in which PAE is enabled (for whatever reason).
However, PAE itself is surely still in use and necessary.

my 2 rappen
scheuri

Please give us a list of applications from the repositories, that don't work with a 64-bit processor.

---

### Post by Merk42 on 2010-01-15
> **cariboo907 said:**
> Please give us a list of applications from the repositories, that don't work with a 64-bit processor.

I know off the top of my head, ZSNES. 
(Personally I figured it was a small sacrifice for all the advantages of 64bit, over even a 32bit PAE kernel)

Maybe scheurl will know of much more.

---

### Post by Gourgi on 2010-01-15
> **cariboo907 said:**
> Please give us a list of applications from the repositories, that don't work with a 64-bit processor.

wink

---

### Post by kevpan815 on 2010-01-15
I have a 5 Gigabyte Download Limit per month with U.S. Cellular, since my dad does NOT let me connect my Linux machines 2 his Comcast connection (I live with my parents since I live on U.S.A. Government Assistance due 2 a mental disability) and how I aquired Ubuntu was by purchasing the X86 9.10 Share the Spirit package (since Ubuntu would NOT let me request any more free disks), and then Upgraded it 2 10.04 Alpha 2 using Sudo Update-Manager -d, Just FYI.

---

### Post by kevpan815 on 2010-01-15
P.S. X64 Ubuntu often does NOT work correctly on my 3 computers, and sometimes all I get with X64 Ubuntu is a continues BEEP, BEEP, BEEP, etc. on computer startup, especially when using Pre-Release versions of Ubuntu!

---

### Post by terry_gardener on 2010-01-15
yes pae kernels are still in lucid using one now, installed by default

---

### Post by kevpan815 on 2010-01-15
P.S. I now have Alpha 2 installed and notice that it did install Kernel Linux 2.6.32-10-generic-pae as the Default Kernel, Just FYI.

---

### Post by diebels on 2010-01-16
Quit the silly 32-bit bashing already.  Everybody is aware that it's coming to end of life, but if you have special needs and want to stay on 32 bit, you're free to do so.  I think that it's great Ubuntu started providing a generic-pae kernel in Karmic.  It's the same as the generic kernel with pae added, and I can't see it adding much maintenance burden. 

Another special case where pae could be preferable is when running several virtual machines, as each process on the system will take up slightly less ram.

Program startup time might also be slightly quicker with less data to read from disk.

Anyway, it's great that we have the choice.  And if you're ok with the performance hit you get in processing intensive programs when you downgrade from 64-bit to 32-bit then go ahead.

---

### Post by Ibidem on 2010-01-16
There are other things to consider, also: VMWare and Dosemu, along with anything that calls BIOS code (such as a little package to properly restore video state), will run much faster.  64-bit doesn't have VM86, but any bootloader or hardware interrupt is 16-bit, so VMWare switches to 32-bit mode if and when your OS uses any legacy code.  Everyone else uses emulation.  Both solutions are slower than VM86.
The Atom 330 (standard netbook CPU) is 32-bit only, and there are plenty of other 32-bit systems still in production.

Ibidem

---

### Post by pressureman on 2010-01-16
> **Ibidem said:**
> The Atom 330 (standard netbook CPU) is 32-bit only, and there are plenty of other 32-bit systems still in production.

Ibidem

Actually the Atom 330 is 64-bit (and dual core even). The specs say so ([http://processorfinder.intel.com/Details.aspx?sSpec=SLG9Y](http://processorfinder.intel.com/Details.aspx?sSpec=SLG9Y)) and we have an Atom 330 box in the office which is running 64-bit Centos 5.4.

Maybe you're thinking of the N270 or N280, which are also fairly popular in netbooks (and are 32-bit).

---

### Post by Merk42 on 2010-01-16
Why would people running Netbooks run with PAE?
What netbook has 4GB+ of RAM?

---

### Post by Ibidem on 2010-01-16
I guess you're right there, although PAE comes handy around 3 1/2 GB...But the CPU is still 32-bit PAE enabled (no idea why).

---

### Post by NCLI on 2010-01-18
> **cariboo907 said:**
> Please give us a list of applications from the repositories, that don't work with a 64-bit processor.

Wine is also problematic.

---

### Post by kahumba on 2010-01-18
64 bit are clearly better cause:
- you can address a lot of memory by default
- it's more efficient cause it has more registers and one can safely assume the likes of SSE2 are present too.

but 32 bit:
- uses less memory (C apps typically use 30% less than 64 bit ones, and Java about 2.5x times less, this is huge!)
- still, there are random minor (or major) annoyances, 64 bit is still an afterthought in some cases for some software companies (especially in the windows world), the likes of skype don't provide native 64 bit apps for Linux, so 32 bit is still more pervasive, but hopefully will soon fade away.

---

### Post by philinux on 2010-01-18
Interesting article.

[http://www.tuxradar.com/content/ubuntu-904-32-bit-vs-64-bit-benchmarks](http://www.tuxradar.com/content/ubuntu-904-32-bit-vs-64-bit-benchmarks)

---

