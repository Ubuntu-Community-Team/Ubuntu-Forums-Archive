---
title: "64 or 32 bits?"
date: 2008-03-21
forum: Installation &amp; Upgrades
---

### Post by pmatos on 2008-03-21
Hello all,

I am having _loads_ of problems with installing Ubuntu.
I had a couple of CDs back from the 5.10 time that I installed on an old PC.
I thought this was a 64bit system. Tried 64bit 5.10 cd and it failed (arch was not 64 so I neede a 32bit distro). Tried 32bit ubuntu next. Installation was sweet! When I started it everything was so old that I tried to update to Dapper (6.04 I guess). Update destroyed system state, so I decided to burn a 32bit 7.10 cd and install it.
Live CD kept crashing during install so I burn yet another CD but with the text install. Installation was sweet. Started gnome and tried some suggested security updated. System halted. From time to time everything halts. Using E16 given Gnome is giving loads of halts. Trying to install or update anything halts. There is no memory problem! It seems that it is some page access or unknown asm op that panics the kernel.

Here's my CPU:
[INDENT]$ sudo cat /proc/cpuinfo
[sudo] password for pmatos:
processor       : 0
vendor_id       : AuthenticAMD
cpu family      : 6
model           : 10
model name      : AMD Athlon(TM) XP 2500+
stepping        : 0
cpu MHz         : 2319.744
cache size      : 512 KB
fdiv_bug        : no
hlt_bug         : no
f00f_bug        : no
coma_bug        : no
fpu             : yes
fpu_exception   : yes
cpuid level     : 1
wp              : yes
flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov 
pat pse36 mmx fxsr sse syscall mmxext 3dnowext 3dnow up ts
bogomips        : 4643.32
clflush size    : 32[/INDENT]

Should I try 64 bits? System has 512 mgs RAM.

I really don't understand what is going on, any help would be appreciated.

Cheers,

Paulo Matos

---

### Post by mikewhatever on 2008-03-21
thlon(TM) XP 2500+ does not seem to be a x64 bits CPU, so go for a 32 bits version. I'd also suggest a memtest from the Live cd.

---

### Post by kushykush on 2008-03-21
Never heard of "XP" athalon before.  In any case, AMD 64 bit have to be dual core processors starting with Athalon 3500 and up.  Your processor is definitely not 64 bit. That might be the reason why you are having problems.  Stick with the i-386, 32 bit until you change the processor.  There is no advantage to having 64 bit unless you have the upgraded hardware.  i have a dual core Opteron AMD 6000. I am happy with the 32 bit. There is no visible difference thus far.

---

### Post by Raptor354 on 2008-03-22
I agree with kushykush  in that there isn't a noticeable difference.  I started out with 64-bit Ubuntu 7.10, but most of the things in synaptic don't work unless you get the 64-bit sources.  I now have 32-bit installed, complete with OS X theme, without any problems.  Thus, I prefer the 32-bit version.

Another thing I'd do would be to do the CD check when you boot to the CD.

32-bit processors CANNOT run 64-bit operating systems natively.  If you want to find out why, go try to install Vista 64-bit.

Kushykush:  The 'XP' series was the predecessor the '64' series.  They're all 32-bit single-cores.  Pretty much anything from AMD without a 64 in its name, as far as mainstream processors go, is 32-bit (i.e.: Sempron 64, Athlon 64).  The mainstream dual cores start at the Athlon 64 X2 3600+, then the 3800+, then the 4000+, etc all the way to 6400+.  Opterons and FX's are a different story.  Semprons are just a wimpier, cheapskate version of the Athlons (less cache, mainly).

Raptor354

P.S.: Anybody's free to correct me if I'm wrong.

---

### Post by kushykush on 2008-03-22
Thank you for the info on the XP AMD chips.  I started with the dual core Athalon 3500 and now have replaced it with the Opteron.  I also increased my RAM from 1 gig to 2.

While there is some difference ofcourse, there is not much difference when it comes to using software (most of which is 32 bit) and also hardware (most hardware drives are easily available in 32 bit).  While the hardware situation has remarkably changed since Windows Vista came out, the irony still is that Windows 64 bit Vista drivers will not work under Linux OSs.  

In that sense, there is no advantage in moving to 64 bit.  The software and hardware functions and speed are identical and probably work better in the 32 bit environment.

My two cents.

---

### Post by sh4d0w808 on 2008-03-22
Hmmm... strange what kushykush wrote - I have found the same opinions on some other forums also, although my experience is a little bit different. I have had installed a 32bit Ubuntu first and that system was definitely OK. After some weeks, I have deleted this system and installed a 64bit version on the same hardware - and found that the new system booting up faster, shutting down faster and the whole system was faster than the 32bit, so I stayed at 64bit. Of course, everybody should know that it is a little bit harder to install flash and java but Automatix2 package is able to install these. Because this is my test Ubuntu machine, I have installed some packages on it without problems. Of course, if there are special needs, it can be that it cannot run on a 64bit system.

---

### Post by Raptor354 on 2008-03-23
64-bit processors are capable of handling twice the information as the 32-bit processors given the same time.  The 32-bit OSs running on 64-bit hardware will obviously run slower than 64-bit on 64-bit.

sh4d0w808:  I didn't know about Automatix2.  What is it?  If it's anything like synaptic, then I may switch back to 64-bit.  :)

---

### Post by sh4d0w808 on 2008-03-24
Hello Raptor354,

U can find Automatix2 [here]("http://www.getautomatix.com/"). It is not instead of Synaptic but a little bunch of programs, which are hard to install them manually under 64bit system. As far as I remember, it installs the 32bit version of flash and java, but I'm not sure. I think U may check it's page and decide to use it (and switch to 64bit) or  not.

---

### Post by kushykush on 2008-03-25
I was misunderstood.  I was trying to say: Switch to 64 bit only if you have the right hardware ( dual core CPU, more than 1 gig of memory, and enough hard drive space).   If you have a minimally performing processor and not enough RAM then even if you install 64 bit version (and it works), it is not a big advantage.  What makes the difference is the HARDWARE.  Upgrade the hardware before you decide to go 64 bit.

I have installed the new Beta 8.04 Ubuntu (AMD-64bit version).  It is working very well because I have the right hardware (Opteron dual cached processor, 2 gig Ram, and high speed SATA drives).  You bet, I do see the difference. 

Ubuntu 8.04 is a beta version.  I was expecting glitches.  My compliments to the Ubuntu Hardy Heron development team. They have been on top of problems.   The glitches, to begin with, did not impact the basic running of the OS.  Ubuntu developers were able to fix problems the same day.(for example, using third party graphic drivers, such as Nvidia)

Adobe Flash Player was not installing in FireFox beta 3.0, even after I followed the instructions.  But the "bug" was fixed in a few hours by Ubuntu developers. Adobe Flash Player installed automatically.  I do not know how! Now everything works and the internet is faster than before.  I am also using the alternative browser called Seamonkey, which seems to be a twin of Netscape.  Seamonkey is working better than the beta Firefox 3.0.

Recap:  By all means go for the 64 bit if you have supporting hardware to take advantage of 64 bit capabilities.  If, however, you have a "borderline" machine, you are better off using the 32 i-86.

---

