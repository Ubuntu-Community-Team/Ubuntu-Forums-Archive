---
title: "64 versus 32bit - myths?"
date: 2009-09-29
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by virtualu2 on 2009-09-29
Hi,
I have used both 64 and 32bit versions of ubuntu and other distros.  Often I read alot of threads that there is not a big performance increase with 64bit and that if you use 3rd party apps (non-free, citrix client, etc) that you will have issues with 64bit.

I had one issue getting the citrix web client installed on the 64bit version of jaunty, but finally got it working after searching around.

With a 4gb system, I would like to use 64bit, and on a test server I use I also rather use it since I want to bump that to like 8gb.

What are the major issues or does really almost everything work?

What repos and packages are best to add for 64bit?  I know adobe flash has to be pulled from the adobe labs site, are there other critical items?

---

### Post by chrisjsmith on 2009-09-29
I've not really found much of an issue using either version.

64-bit is better for larger memory as you don't lose a chunk to the crappy x86 architecture on the 4Gb boundary.

---

### Post by DougieFresh4U on 2009-09-29
> **virtualu2 said:**
> What repos and packages are best to add for 64bit?  I know adobe flash has to be pulled from the adobe labs site, are there other critical items?

Java 64 bit

---

### Post by dino99 on 2009-09-29
problem is that lot of bios dont deal with memory upper than 4Gb

---

### Post by 23meg on 2009-09-29
Is this thread supposed to be related to Karmic in any way?

---

### Post by andrewabc on 2009-09-29
> **23meg said:**
> Is this thread supposed to be related to Karmic in any way?

Hopefully people post some differences.
I think there is the no 64 bit flash (uses 32 bit), and in a firefox thread they said tracemonkey is not enabled on 64 bit ubuntu.

I'm kinda wondering if I should use 64 bit or switch back to 32 bit if there are no benefits (no tracemonkey is big problem). I only have 3gb of ram.

My 64 bit jaunty works fine, although the flash error stating there is no flash for 64 bit is a bit annoying and forces me to go into synaptic to install adobe flash.

---

### Post by wizard10000 on 2009-09-29
Video rendering works better under 64-bit.  Used to take me about two hours to render two hours of video on a 2.8GHz hyperthreading machine under 32-bit Linux - the same operation in my shiny new Core i7 with a 64-bit OS takes a bit more than ten minutes.

---

### Post by Longinus00 on 2009-09-29
> **wizard10000 said:**
> Video rendering works better under 64-bit.  Used to take me about two hours to render two hours of video on a 2.8GHz hyperthreading machine under 32-bit Linux - the same operation in my shiny new Core i7 with a 64-bit OS takes a bit more than ten minutes.

I think that time improvement has more to do with you jumping several generations of CPU architectures rather than the 32 vs 64 bit improvement.

---

### Post by tad1073 on 2009-09-29
try a pae kernel, I am running 32 bit w/ 2.6.31.11-generic-pae. I have 6 gigs or ram and able to access 5.9 gigs with this kernel.

32 bit seem a little more snappy than 64 bit to me, could just be me though.

---

### Post by RAOF on 2009-09-29
A not very comprehensive list:
[list]
[*] The 64bit install will have somewhat higher RAM usage, because memory addresses now take 4 bytes rather than 2 (**Edit:** I suck at dividing by 8.  These should be *8* bytes rather than *4*).
[*] CPU-bound 64bit apps are likely to be slightly faster than 32bit apps, because x86-64 exposes two times as many general-purpose registers than IA32.  This makes it easier for the compiler to optimise.
[*] The 64bit install is potentially slightly more secure; address-space-randomisation is significantly easier to break in a 32bit address space.
[*] There might be a handful of packages unavailable in the 64bit install, but I haven't run into any for the last couple of releases.  Flash, Java, etc work just fine.
[/list]

---

### Post by Nullack on 2009-09-29
The other point is that the 64 bit compiles have more optimisations in them than the 32 bit because the 64 bit builds dont have to suppport the lowest common denominator of 32 bit ancient cpus.

---

### Post by dasunst3r on 2009-09-29
Java 64-bit is actually available on the Medibuntu repository -- [www.medibuntu.org](www.medibuntu.org)

---

### Post by RAOF on 2009-09-29
64bit Java is actually available from the [official repositories]("http://packages.ubuntu.com/karmic/openjdk-6-jre")!

---

### Post by ktp on 2009-09-29
> **dasunst3r said:**
> Java 64-bit is actually available on the Medibuntu repository -- [www.medibuntu.org](www.medibuntu.org)

Sun Java 64-bit with the 64-bit browser plugin can be found here:

[http://packages.ubuntu.com/karmic/sun-java6-plugin](http://packages.ubuntu.com/karmic/sun-java6-plugin)

---

### Post by mariner09 on 2009-09-29
I have a work app that is 32-bit only, so for me, trying to create a 32-bit chroot for it was more pain than it was worth.  PAE kernel was the no-brainer on 32-bit and it works great with 4gb RAM.

Maybe stick with PAE on your 4gb system, but consider 64-bit for your 8gb server.

---

### Post by NormanFLinux on 2009-09-29
Can a 64 bit OS be installed on today's 32 bit PCs? Or will we have to wait for 64 bit PCs to reach the consumer market?

---

### Post by Longinus00 on 2009-09-29
> **NormanFLinux said:**
> Can a 64 bit OS be installed on today's 32 bit PCs? Or will we have to wait for 64 bit PCs to reach the consumer market?

Short answer, no. 64 bit PCs have been the market standard on the market for the past few years though, so if your computer is new, it's a good change it's actually 64 bit. In fact, AMD has been 64 bit for a long time now.

---

### Post by Sef on 2009-09-29
> Can a 64 bit OS be installed on today's 32 bit PCs? Or will we have to wait for 64 bit PCs to reach the consumer market?


It depends on your hardware.  If you have 64-bit hardware, then all will be well.  If you have 32-bit hardware, then it won't install.  All hardware now is 64-bit, although many computers are installed with 32-bit software.

---

### Post by NormanFLinux on 2009-09-29
Ok then. What is the difference between a 32 bit and 64 bit PC? My desktop Pentium M and my Centrino Duo laptop have dual core processors but they run 32 bit operating systems and software. My Pentium 4 laptop, Celeron M and old Pentium III desktop are single core processors.

---

### Post by RAOF on 2009-09-29
> **mariner09 said:**
> I have a work app that is 32-bit only, so for me, trying to create a 32-bit chroot for it was more pain than it was worth...

It's entirely possible that ia32-libs would have contained the right libraries to get it running without a chroot.  But your situation should dictate the technology, not the other way around.

> 
Ok then. What is the difference between a 32 bit and 64 bit PC? My desktop Pentium M and my Centrino Duo laptop have dual core processors but they run 32 bit operating systems and software. My Pentium 4 laptop, Celeron M and old Pentium III desktop are single core processors.

Out of those, the Centrino Duo laptop is the only one which might be 64bit capable; it depends on whether it's got a Core Duo (32bit only) or Core Duo 2 (64bit capable) chip in it.

Simple, isn't it :).

---

### Post by novafluxx on 2009-09-29
> **RAOF said:**
> It's entirely possible that ia32-libs would have contained the right libraries to get it running without a chroot.  But your situation should dictate the technology, not the other way around.


Out of those, the Centrino Duo laptop is the only one which might be 64bit capable; it depends on whether it's got a Core Duo (32bit only) or Core Duo 2 (64bit capable) chip in it.

Simple, isn't it :).

Very much appreciate your input here RAOF! Good stuff in here! I'm still running 32-bit Karmic right now, mainly due to only having 3GB of memory. I don't see a reason to burden myself with 64-bit unless I have a need for it. However on my desktop, with 4GB, I'll be installing Karmic 64-bit :P:)

---

### Post by benjamimgois on 2009-09-30
Yeap, i just upgraded my laptop to 4GB of RAM and karmic will be the first release that i will use a 64bit version. Can anyone post some applications that DO NOT work or have several issues under 64bits ? It seens that flash and java aren't a problem anymore.

---

### Post by RAOF on 2009-09-30
> **benjamimgois said:**
> Yeap, i just upgraded my laptop to 4GB of RAM and karmic will be the first release that i will use a 64bit version. Can anyone post some applications that DO NOT work or have several issues under 64bits ? It seens that flash and java aren't a problem anymore.

Here's the list of problems I run into:




.

---

### Post by dinxter on 2009-09-30
> **RAOF said:**
> Here's the list of problems I run into:




.
:)

---

### Post by benjamimgois on 2009-09-30
> **RAOF said:**
> Here's the list of problems I run into:




.

rsrsrsrrs.... That's nice ! Well, so i guess that 32bits never more !   :)

hahaha.... offtopic: It reminds me of the "bits race" on video-games industry, couple of years ago. Sega Genesis had a "16bit" written in big letters.

---

### Post by foremannz on 2009-09-30
Customer of mine spent NZ$5,500 on a laptop do to his video editing, but for all the good it did him, with XP Pro x32 limiting him to just 2.5GB RAM, it still took him hours to do his video editing for a news segment.  I built him a system for under NZ$2,000 with 8GB RAM, 1GB video and Vista Home Prem x64, and he can do the same job in around half an hour.

It seemed that while he was cutting up all the media clips, it would cache it all into memory - once he used up all the ram, it went insane reading and writing to the HDD, in trying to cope with the ram shortage.  His new system has plenty of RAM to work with and is optimised for 64bit Windows, and he's never had the software run the HDD like what he had on his laptop

For anyone looking for such software, this customer uses Adobe CS4 - native 64bit on Windows, native multicore cpu.  Tests have shown that CS4 on 64bit Windows is unbelievably fast compared to installing on 32bit OS, in some cases more than 10 times faster!!!

---

### Post by FuturePilot on 2009-09-30
> **RAOF said:**
> Here's the list of problems I run into:




.

Yep I'll second that :D

---

### Post by TrueTom on 2009-09-30
> **RAOF said:**
> The 64bit install will have somewhat higher RAM usage, because memory addresses now take 4 bytes rather than 2


Your are either 20 years or so too late with this statement or you run some pretty weird hardware... :D

---

### Post by dinxter on 2009-09-30
a bit of bumf
[http://www.tuxradar.com/content/ubuntu-904-32-bit-vs-64-bit-benchmarks](http://www.tuxradar.com/content/ubuntu-904-32-bit-vs-64-bit-benchmarks)

remember ia32 libs are available for those 'must have' 32 bit closed binaries, i dont have any problems with anything myself

---

### Post by bluenova on 2009-09-30
I used 64bit with Intrepid on my AMD 3Ghz dual core but I went back to 32bit with Jaunty. I didn't really see any speed benefits over 32bit other than when I was video rendering which is only a few times a year so no biggy. The reason I went back to 32bit with Jaunty is because although I had no real problems I do like to try out lots of new software and usually new projects only compile 32bit debs. I don't have time to compile from source all the time to quickly try something out. It's not a huge issue though and if I had seen a general speed benefit I would have stayed 64bit for Jaunty.

For Karmic, I'm not sure yet, I may go back to 64bit just to show support as it is the future.

---

### Post by Joe_Bishop on 2009-09-30
I have 4Gb on my worst machine (computer at my work). Others have 8 and 12Gb. So, I've only 64 bits linuxes there. I feel it's slightly better than 32, more responsive.

---

### Post by RAOF on 2009-09-30
> **TrueTom said:**
> Your are either 20 years or so too late with this statement or you run some pretty weird hardware... :D

:redface: 

Ahem.  Only a factor of 2 off :)

---

### Post by WorfSOM on 2009-09-30
> **RAOF said:**
> Here's the list of problems I run into:




.

I know it is a minor issue, but ZSNES is not available in 64-bit.

---

### Post by dinxter on 2009-09-30
> **WorfSOM said:**
> I know it is a minor issue, but ZSNES is not available in 64-bit.
though Snes9x (+express) is, you'll know if thats a worthy replacement better than i will :)

---

### Post by sonicb00m on 2009-09-30
The biggest factor for me using 64bit was a kernel bug that made my SATA drives transfer data between themselves at an alarmingly slow rate.

I decided to give 64bit ago again and I must say i'm totally delighted now. The sata issue seems fixed and im utilising my full ram again. I used to use 32bit with the pae but didn't find the performance that great. It was better forgoing the ram unless you really need it.

I must say though that 32bit seemed nippier on the desktop for general use. And flash isn't a problem.

Fortunately, the official adobe 64bit alpha plugin is working fine with karmic and no rpoblems with pulse audio. NOt a single crash yet!

---

### Post by benmoran on 2009-09-30
I've been pure 64-bit for about 9 months now. Zero problems, and I love the encoding speed increase.

For a 64-bit SNES emulator, use SNES9X-GTK. It's waaaay better than the version of Snes9x in the repos, and equaly better than ZSnes. I used to be a ZSnes fanboy, but this is so much better. 

[http://www.snes9x.com/phpbb2/viewtopic.php?t=3703](http://www.snes9x.com/phpbb2/viewtopic.php?t=3703)

---

### Post by WorfSOM on 2009-09-30
Thanks for the Snes9x recommendations guys.

---

### Post by coolvibe on 2009-09-30
if you install 32-bit support libs, 32-bit apps will work just fine on 64-bit ubuntu.

So use whatever you like. I'm on 64-bit (because my lappy has 4 GB), and I kinda hardly notice the difference. I say, if you can go 64-bit, try it out. If it doesn't work, just go back to 32 bit.

---

### Post by nanog on 2009-09-30
> **Sef said:**
> All hardware now is 64-bit, although many computers are installed with 32-bit software.


LOL!

I'd love to see you install 64 bit on the Dell Minis that have been selling like hotcakes (I have two).


I switched to 64 bit years ago because we run many applications that algorithmically *require* 64 bit addressing.

---

### Post by wizard10000 on 2009-09-30
> **Longinus00 said:**
> I think that time improvement has more to do with you jumping several generations of CPU architectures rather than the 32 vs 64 bit improvement.

Yup.  It appears that's the difference - I looked at several sites and there doesn't appear to be a significant performance difference between 32- and 64-bit rendering.

I stand corrected  ;)

---

### Post by tuppe666 on 2009-09-30
Having used 64-bit for a long time. Particularly on the Pentium4 where it is hard to tell if you even have it as an option. Shouldn't Ubuntu simply choose to install the 64-bit if available.

Interestingly I have a media centre running 64-bit Ubuntu, but really I want the 64-bit remix on there. Which is simply not available.

Its important to note that those upgrading Do not get an option to upgrade to 64-bit without a fresh install. I did it and its a painful move.

---

### Post by ranch hand on 2009-09-30
I prefer the 64bit route myself because of my box.  With the Core2 Quad I can run on 32 or 64bit.  32bit = 4.8GHZ and 64bit = 9.6GHz.

---

### Post by Amaranth on 2009-09-30
> **tuppe666 said:**
> Having used 64-bit for a long time. Particularly on the Pentium4 where it is hard to tell if you even have it as an option. Shouldn't Ubuntu simply choose to install the 64-bit if available.

As the 64-bit installer is a completely separate 700MB disc it would be rather hard to autodetect and install the right one. Besides, 64-bit is still somewhat of a power user feature as not everything will work. We still need multiarch support (coming soon, apparently) to fix that.

> Its important to note that those upgrading Do not get an option to upgrade to 64-bit without a fresh install. I did it and its a painful move.

I've yet to see an OS that can handle a 32-bit -> 64-bit upgrade so the fact that Ubuntu can't do it isn't saying much. Please don't mention OS X, they just blindly write over the existing install. You can do that same by having /home on a different partition and choosing not to format it during a clean install, basically.

---

### Post by tuppe666 on 2009-09-30
> **Amaranth said:**
> As the 64-bit installer is a completely separate 700MB disc it would be rather hard to autodetect and install the right one. Besides, 64-bit is still somewhat of a power user feature as not everything will work. We still need multiarch support (coming soon, apparently) to fix that.



I've yet to see an OS that can handle a 32-bit -> 64-bit upgrade so the fact that Ubuntu can't do it isn't saying much. Please don't mention OS X, they just blindly write over the existing install. You can do that same by having /home on a different partition and choosing not to format it during a clean install, basically.

For the upgrade path. Ubuntu has a distinct advantage over those other OS's simply because of package management. It seems trivial to identify which installs cannot migrate to 64-bit and which can. Simply by comparing whether currently installed packages have a 64-bit equivalent.

---

### Post by priegog on 2009-09-30
Last week I replaced a 5 year-old laptop (32bits, obvioulsy) with a spanking-new core 2 duo one and 4gb of ram. 
I didn't even think twice about it, and went for the 64bit version (BTW, when will they stop calling it AMD64?). And I have to say, it is truly painless, and miss absolutely nothing. granted, the first thing I do upon a new ubuntu install is install ubuntu-restricted-extras which takes care of flash, (i think java) and in 64bit version, ia32 libs too.
A couple of releases ago, this would have been a real debate, but in Jaunty it is pretty much flawless and karmic I supose will be even better. 64bit is, after all, the future (and pretty much the present too). 
Except for netbooks (God knows why they went for the 32bit architecture instead of ARM for instance), I think it's pretty much impossible tu buy a 32bit computer these days, except for old leftover core duo processors rebranded as intel dual core. 
So really, please make your first choice 64-bit, and ONLY consider going back to 32 if you have any problems that you can pin on it being 64-bit.
my $0.02

---

### Post by Longinus00 on 2009-09-30
> **ranch hand said:**
> I prefer the 64bit route myself because of my box.  With the Core2 Quad I can run on 32 or 64bit.  32bit = 4.8GHZ and 64bit = 9.6GHz.

Your clockspeed and architecture of your cpu aren't related in that manner. Your cpu is 2.4 GHz no matter if you run it in 32bit or 64bit mode.

---

### Post by coolvibe on 2009-10-02
> **Longinus00 said:**
> Your clockspeed and architecture of your cpu aren't related in that manner. Your cpu is 2.4 GHz no matter if you run it in 32bit or 64bit mode.

Also, 2 cpus does not mean double the clockspeed or performance. Especially since most apps aren't multithreading anyways. What multiple cores does give you is better multithreading and better stability.

---

### Post by Joe_Bishop on 2009-10-02
> **coolvibe said:**
> Also, 2 cpus does not mean double the clockspeed or performance. Especially since most apps aren't multithreading anyways. What multiple cores does give you is better multithreading and better stability.
It does mate, it does! Double precision increase the manhood twice too. It causes productivity increase (twice too again lol).

---

### Post by benjamimgois on 2009-10-02
I just finished to install my Karmic 64bits. And i can tell that everything is workin just fine. The only problem that i have, was when i tryed to install some DEBIAN packages through GDEBI, it gives me a message "Incompatible Architecture I386" . So , i go to the terminal and type "dpkg -i --force-architecture *.deb" and everything installed without further problems.

---

### Post by ranch hand on 2009-10-02
If you are running boink you will have all 4 pegged at 100% when you are not doing anything else.  Straight up math calc really cranks the buggers up.

---

