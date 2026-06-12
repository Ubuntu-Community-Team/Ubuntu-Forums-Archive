---
title: "Question about a microkernel (seL4) and my hardware"
date: 2011-05-09
forum: Installation &amp; Upgrades
---

### Post by ClientAlive on 2011-05-09
I've been contemplating a project recently and am curious if a particular microkernel I have my eye on would work on my hardware. I am not as technically advanced to get into all the cpu architectures and things; I'm just trying to understand enough to pick out some parts and pieces that could possibly work on my hardware.

There is a microkernel called seL4 that I've had my eye on. Perhaps this could be something to build on?

 Here's a couple links to information for it:

[http://ertos.nicta.com.au/research/sel4/](http://ertos.nicta.com.au/research/sel4/)

[http://www.sigops.org/sosp/sosp09/pa...ein-sosp09.pdf](http://www.sigops.org/sosp/sosp09/pa...ein-sosp09.pdf)

In the pdf (second link) it talks about being designed around ARMv6 which I gather is a microprocessor architecture. In the little reading I have done I have seen that the company who makes my cpu labeled their architecture beginning with the letter AM.

What I am wondering is if this microkernel could be used as a building block that would actually run on my system AND if so, what I could expect from doing so. Pros? Cons?

Here is some infomation on my system from the terminal. Hope it isn't overkill. On the other hand, if it is not enough please let me know.

MODEL INFORMATION FROM DMIDECODE:

```
System Information
        Manufacturer: Hewlett-Packard
        Product Name: HP Pavilion ze2000 (PV336AV#ABA)  
        Version: Rev 1
        #
        #
        Wake-up Type: Power Switch

```


LSPCI INFO:

```

00:00.0 Host bridge: ATI Technologies Inc RS480 Host Bridge (rev 10)
00:01.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
00:13.0 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller (rev 80)
00:13.1 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller (rev 80)
00:13.2 USB Controller: ATI Technologies Inc IXP SB400 USB2 Host Controller (rev 80)
00:14.0 SMBus: ATI Technologies Inc IXP SB400 SMBus Controller (rev 81)
00:14.1 IDE interface: ATI Technologies Inc IXP SB400 IDE Controller (rev 80)
00:14.3 ISA bridge: ATI Technologies Inc IXP SB400 PCI-ISA Bridge (rev 80)
00:14.4 PCI bridge: ATI Technologies Inc IXP SB400 PCI-PCI Bridge (rev 80)
00:14.5 Multimedia audio controller: ATI Technologies Inc IXP SB400 AC'97 Audio Controller (rev 80)
00:14.6 Modem: ATI Technologies Inc SB400 AC'97 Modem Controller (rev 80)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control

```


CPU INFO:

```

cpu family	: 15
model		: 36
model name	: AMD Turion(tm) 64 Mobile Technology ML-34
stepping	: 2
cpu MHz		: 800.000
cache size	: 1024 KB
fdiv_bug	: no
hlt_bug		: no
f00f_bug	: no
coma_bug	: no
fpu		: yes
fpu_exception	: yes
cpuid level	: 1
wp		: yes
flags		: fpu vme de pse tsc msr pae mce cx8 apic mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 syscall nx mmxext fxsr_opt lm 3dnowext 3dnow up pni lahf_lm
bogomips	: 1595.27
clflush size	: 64
cache_alignment	: 64
address sizes	: 40 bits physical, 48 bits virtual
power management: ts fid vid ttp tm stc

```


Any conclusions out there?

Thanks a whole bunch for taking the time to look.

Jake

---

### Post by Blasphemist on 2011-05-10
Hi Jake-

I'm no more of an expert on this than you and I'll be interested in the replies you get. I can offer this.

[http://en.wikipedia.org/wiki/ARM_architecture](http://en.wikipedia.org/wiki/ARM_architecture)

For your pc, I don't think this is the direction you will want to go and I don't _think_ you could. I think it will help if you can flesh out the seed of the idea you have for us. I have a feeling, there will be people that can help and give guidance if you want to use or create a slimmed down and very secure desktop environment. If your idea is bigger or more specific, go ahead, talk it out here.

Good to hear from you again.

---

### Post by ClientAlive on 2011-05-10
> **Blasphemist said:**
> Hi Jake-

I'm no more of an expert on this than you and I'll be interested in the replies you get. I can offer this.

[http://en.wikipedia.org/wiki/ARM_architecture](http://en.wikipedia.org/wiki/ARM_architecture)

For your pc, I don't think this is the direction you will want to go and I don't _think_ you could. I think it will help if you can flesh out the seed of the idea you have for us. I have a feeling, there will be people that can help and give guidance if you want to use or create a slimmed down and very secure desktop environment. If your idea is bigger or more specific, go ahead, talk it out here.

Good to hear from you again.


Good to hear from you too my friend.

I found the manual for seL4:  [http://ertos.nicta.com.au/research/sel4/sel4-refman.pdf](http://ertos.nicta.com.au/research/sel4/sel4-refman.pdf)

Thought it might be of some interest or use.

How this began for me can be seen here:  [http://ubuntuforums.org/showthread.php?t=1753492](http://ubuntuforums.org/showthread.php?t=1753492)

Also notice the last paragraph of post #3 (explains a lot)

And let me clarify something about that other thread that may not be as obvious. What I am talking about there, the real idea, is the idea of the virtual box being the o/s. Sort of like a blank slate o/s where you put what you want into it. On another, somewhat related point, I hear virtual box came up with something that makes your system able to run any apps together in one unified system (whether they be windows, mac, Linux or whatever). Neat stuff.

So, looking on the internet, I see that this thing (seL4) seems to be pretty high tech! This  [http://permalink.gmane.org/gmane.comp.capabilities.general/12849](http://permalink.gmane.org/gmane.comp.capabilities.general/12849) is dated Feb of 2011. And here  [http://www.l4hq.org/oldnews.php](http://www.l4hq.org/oldnews.php)  it talks about this thing being the basis of some kind of virtualized system that outperforms native Linux.

Interestingly enough, that (virtualized system concept) fits perfectly with the idea I had that got me started on all this (at the link to my other thread above). Now I didn't think this seL4 business would turn out to be that cutting edge when I wrote first got into it, but now I'm thrilled to death to discover as much and just itchin to tear into this thing.

Finally, yes, there are a lot of things I can't do right now. This is true for all of us. It's also true that there are a lot of things we could do - if given enough time. Time is the factor. So I guess the real question is one of dedication and desire. As I mentioned in that last paragraph of post #3 (at other thread linked above) I think choosing a difficult challenge is exactly where truly high reward comes from. Now I didn't say it like that when I wrote it there, but that's pretty much what I was getting at.

Please, please don't take that paragraph above as though I were upset or defensive in any way. I am not. It was merely meant to explain my mindset.

Thanks blasphemist and everyone.

Jake
---------------------------------------

Edit: found something more info. I think I may be on to something here guys.

[http://ertos.nicta.com.au/research/l4/performance.pml](http://ertos.nicta.com.au/research/l4/performance.pml)

AND

[http://en.wikipedia.org/wiki/X86](http://en.wikipedia.org/wiki/X86)

what do you think folks? Can it be done?

---

### Post by MAFoElffen on 2011-05-10
> **ClientAlive said:**
> I've been contemplating a project recently and am curious if a particular microkernel I have my eye on would work on my hardware. I am not as technically advanced to get into all the cpu architectures and things; I'm just trying to understand enough to pick out some parts and pieces that could possibly work on my hardware.
```

cpu family    : 15
model        : 36
model name    : AMD Turion(tm) 64 Mobile Technology ML-34
stepping    : 2
cpu MHz        : 800.000
cache size    : 1024 KB
fdiv_bug    : no
hlt_bug        : no
f00f_bug    : no
coma_bug    : no
fpu        : yes
fpu_exception    : yes
cpuid level    : 1
wp        : yes
flags        : fpu vme de pse tsc msr pae mce cx8 apic mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 syscall nx mmxext fxsr_opt lm 3dnowext 3dnow up pni lahf_lm
bogomips    : 1595.27
clflush size    : 64
cache_alignment    : 64
address sizes    : 40 bits physical, 48 bits virtual
power management: ts fid vid ttp tm stc

```Any conclusions out there?
Thanks a whole bunch for taking the time to look.
Jake
Jake,

You have an AMD processor <> not an ARM as mentioned above.  Different instruction sets.  ARM proc's are in low=power draw devices like PDA Smartphones (Android and WinMo) and in Netbooks. Actually theres lots more "other" options for AMD Chips than an ARM.

They say they have x86 version that might work as 32bit on your proc... 

Have you looked at MIT's version and project?  I think they are further along.  And--micro-kernel's involve other layers, so it isn't a drop-in piece that you can mate with pieces of a monolithic kernel's system.

---

### Post by ClientAlive on 2011-05-10
> **MAFoElffen said:**
> Jake,

You have an AMD processor <> not an ARM as mentioned above.  Different instruction sets.  ARM proc's are in low=power draw devices like PDA Smartphones (Android and WinMo) and in Netbooks. Actually theres lots more "other" options for AMD Chips than an ARM.

They say they have x86 version that might work as 32bit on your proc... 

Have you looked at MIT's version and project?  I think they are further along.  And--micro-kernel's involve other layers, so it isn't a drop-in piece that you can mate with pieces of a monolithic kernel's system.


Yes, right on. One of the last things I discovered before crashing out last night is that they have the x86 version and that x86 seemed to match up w/ my cpu type. I didn't know about any MIT version of the project. Do you happen to have any good link to useful info on that?

Also, from my research, I gather that this seL4 is actually what is used in virtual machines, maybe not so much standard o/ses. I think that's what you are getting at when you say: " . . . it isn't a drop-in piece that you can mate with pieces of a monolithic kernel's system."?

Actually, whichever route I land on, that was kinda the idea from the start. The idea of running everything in a virtual machine. Just got to thinking it might be a nice project (fun and educational) to build something myself. Can't really code at this point but I'm sure I could compile stuff from source to end up w/ tailored to suit system for myself. If that option is available to me.

Thanks for the input man.

Jake
----------------------

Holy crap! I just found a history of this stuff dating back over 30 years!!

[http://www.coyotos.org/history/index.html](http://www.coyotos.org/history/index.html)

Not only that, but it seems the gnu hurd project is something like this.

I wish to God you guys could've seen my reaction to this.

WOW!
\\:D/

---

### Post by ClientAlive on 2011-05-11
> **Blasphemist said:**
> Hi Jake-

I'm no more of an expert on this than you and I'll be interested in the replies you get. I can offer this.

[http://en.wikipedia.org/wiki/ARM_architecture](http://en.wikipedia.org/wiki/ARM_architecture)

For your pc, I don't think this is the direction you will want to go and I don't _think_ you could. I think it will help if you can flesh out the seed of the idea you have for us. I have a feeling, there will be people that can help and give guidance if you want to use or create a slimmed down and very secure desktop environment. If your idea is bigger or more specific, go ahead, talk it out here.

Good to hear from you again.


I'm sorry blasphemist. Now that I look at this again I don't think you meant what I thought you did the first time around.

My life has been _full_ of people telling me I can't do things. They tell me I can't and then I challenge those assumptions. Most of the time I succeed, sometimes I fail. I guess it's something I'm a little cautious about.
After doing a little more reading, for one thing, I see that this microkernel business goes back decades and has been worked on by some of the most brilliant minds alive. Even the gnu hurd project is coneected with this.

In that respect, no, I don't think I'm somehow miraculously going to solve problems that teams of the most brilliant people around haven't been able to solve in decades of working on it.

Still I think what you may have meant is that there is no working microkernel/ operating system in existence today (at least not that I've seen so far - unless you count coyotos). Its a pretty neat concept though. Makes for some nice reading I guess.

I guess I just didn't understand why I needed some big bloated host o/s to run a virtual machine. I figured that if I wanted to use the virtual o/s as my primary day-to-day o/s then the host shouldn't need to be much. I know there are small distros out there like puppy and dsl but if they end up having components I wouldn't need under the circumstances then I'd have to say waste is waste, right? If you don't need it then why is it sitting there, taking up precious resources that you could be using for your guest o/s. That's how I got off on this track.

Just as a total guess I would think it shouldn't take a something that is more than a few mb in size and use maybe a few mb of ram just to have something virtual box will run on top of. I don't know.

---

### Post by ClientAlive on 2011-06-25
Not that there's any direct correlation to this and micro kernels but I found something that looks really, really cool! The way it works is pretty much what I had in mind when I was asking the question in this thread (and similar questions in other threads). It's called Xen. They have some really cool stuff and I think my next project is to get a personal cloud service going along with a few servers (different types, ldap, ssh and maybe a lamp stack).

It's be cool to see how those things work.

:D

[http://www.xen.org/](http://www.xen.org/)

---

