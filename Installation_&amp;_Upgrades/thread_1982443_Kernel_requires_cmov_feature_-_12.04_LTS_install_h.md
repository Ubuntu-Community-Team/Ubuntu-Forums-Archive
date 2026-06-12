---
title: "Kernel requires cmov feature - 12.04 LTS install hangs"
date: 2012-05-18
forum: Installation &amp; Upgrades
---

### Post by martinr on 2012-05-18
My XUbuntu 12.04 LTS installation hangs with the message:
> This kernel requires the following features not present on the CPU:
cmov
Unable to boot - please use a kernel appropriate for your CPU.
My CPU is an AMD K6-2 3D 550 MHz (year 2000) on a fast board with 256 MB memory and an ad-on RAID controller. (It's quick!).

Before I bothered to completely rebuild, upgrade and heavily optimize my old rig I tested with XUbuntu 12.04 beta and I could have sworn that it worked! I overwrote the beta version when I downloaded the released version 12.04 LTS (I waited for it). Now I can't even install it. I thought XUbuntu was especially designed to run on older hardware? What's wrong?
How can I fix it.
Are more people experiencing the same problem?

---

### Post by jadtech on 2012-05-18
yup it will  not completely sure but I am pretty sure that error is telling you that your CPU does not have  on board pae and starting with version 12.04  the 32 bit has to support pae .. 

how ever at this time lbuntu xbuntu  still work without as I understand it in the near future they will no longer work on older cpu  either the  only way to run will be upgrades..

 they are moving from support for these older processors

check here 

[http://www.adminreseau.fr/how-to-install-ubuntu-12-04-on-non-pae-capable-hardware/](http://www.adminreseau.fr/how-to-install-ubuntu-12-04-on-non-pae-capable-hardware/)


 also try burning an ISO os version 11.04 or 11.10 and then try to upgrade using  your 12.04 cd or an online upgrade

---

### Post by martinr on 2012-05-18
Thanks for you reply.
What is pae and why do you need it?
Is it mandatory in Open Office now?
Will email bounce without it?

Does somebody know where I can get my hands again on:
[http://xubuntu.org/news/beta-2-released-new-branding/](http://xubuntu.org/news/beta-2-released-new-branding/)

I could have sworn that worked.

I can't believe that WinXP runs like a charm out of the box and XUbuntu doesn't even support my rig anymore? Lets scrap the planet with perfectly working hardware.

---

### Post by jadtech on 2012-05-18
pae  lets the cpu address morethen 3gb of ram like fake 64bit more of less

pae allows the system to handle a far larger more efective  memmory file system , xp I dont believe was true 64bit OS though it  could run on 64 bit you could load 20 gb of ram in a machine with xp it would still only address and use 2 gb  ...

---

### Post by martinr on 2012-05-18
> **jadtech said:**
> pae  lets the cpu address morethen 3gb of ram like fake 64bit more of less
Great, I don't even need that much SWAP.
You wrote that 12.04 does work without pae. Is there a way around the installer? 
Heck, have you ever printed out 1MB of text? It looks like a phone book. Now the basic install entails provisions for 3000000 phone books of text. We're using up too much resources, if you'd ask me (the things that I do with a computer are not that different from 15 years ago). Ah well, lets have a beer.

---

### Post by jadtech on 2012-05-18
> **martinr said:**
> Great, I don't even need that much SWAP.
You wrote that 12.04 does work without pae. Is there a way around the installer? 
Heck, have you ever printed out 1MB of text? It looks like a phone book. Now the basic install entails provisions for 3000000 phone books of text. We're using up too much resources, if you'd ask me (the things that I do with a computer are not that different from 15 years ago). Ah well, lets have a beer.

yeah the link I posted shows the way to a mini ISO  that will install 12.04  on that processor the istall will be text based and  void of  a lot of things you will have to add from repository  after install ..

if  all you have a lite duty might try puppy linux

---

### Post by martinr on 2012-05-19
> **jadtech said:**
> yeah the link I posted shows the way to a mini ISO  that will install 12.04  on that processor the istall will be text based and  void of  a lot of things you will have to add from repository  after install ..

if  all you have a lite duty might try puppy linux

Thanks for your reply. 
I'm a really heavy duty user, hosting repositories, programming, testing and debugging, etc.

I read the link that you posted and it also recommends XUbuntu as a solution ;). I'm not looking forward to having to handpick what is otherwise a fine distro together myself. :(
Furthermore according this [http://ubuntuforums.org/showthread.php?t=1973440&highlight=PAE+XUbuntu](http://ubuntuforums.org/showthread.php?t=1973440&highlight=PAE+XUbuntu) thread, XUbuntu 12.04 should also have a non PAE kernel?! 

Is there anybody out there, that has a more simple solution? The XUbuntu beta 2 worked as far as I can recall. Why the heck do I get the cmov problem now? Is it really a PAE mandatory problem for XUbuntu of all distros?

---

### Post by martinr on 2012-05-26
anybody?

---

### Post by mörgæs on 2012-05-26
Two different and unrelated topics are being mixed in this thread.

a) PAE or non-PAE.

L/Xubuntu 12.04 are by default delivered with a non-PAE kernel, which also works on PAE computers. You will only notice a difference if you have a 32 bit system with more than 4 GB of memory. This has nothing to do with your problem, which is

b) CMOV

CMOV is required for all Buntu kernels after 10.04. You can install Lubuntu 10.04 and use it for a little less than a year from now [1], but frankly: A computer without CMOV is hardly usable by today's standards, even if you find a distro which installs. You can buy 4-5 years old hardware for next to nothing, so my advice is to let go of the old iron.

[1] [https://help.ubuntu.com/community/Lubuntu/GetLubuntu#A10.04](https://help.ubuntu.com/community/Lubuntu/GetLubuntu#A10.04)

---

### Post by dino99 on 2012-05-26
[http://askubuntu.com/questions/115690/this-kernel-requires-cmov-not-present-on-cpu-error-message](http://askubuntu.com/questions/115690/this-kernel-requires-cmov-not-present-on-cpu-error-message)

---

### Post by martinr on 2012-05-26
> **mörgæs said:**
> 
b) CMOV

CMOV is required for all Buntu kernels after 10.04. You can install Lubuntu 10.04 and use it for a little less than a year from now [1], but frankly: A computer without CMOV is hardly usable by today's standards, even if you find a distro which installs. You can buy 4-5 years old hardware for next to nothing, so my advice is to let go of the old iron.


Thanks mörgæs for your explanation. I got mixed messages regarding PAE.

The K6-2 has a "CMOV", it's just missing a few addressing modes that of course segfault when and if you run into them.

Is there a way around CMOV (recompiled kernel, etc) or a patch for AMD K6-2 3D?

Is only the kernel dependent on the CMOV features? So if I can fix that all else runs?

I just upgraded and optimized the heck out of my machine. It uses little power and runs quite cool.

---

### Post by mörgæs on 2012-05-26
I don't know of any hacks to get the new kernels to work, and in general I wouldn't spend long time on such a computer.

Lubuntu 10.04 will give you one year more. You could also try Puppy.

---

### Post by martinr on 2012-05-31
Thanks for your help.
I've got LUbuntu 10.04 up and running on the AMD K6-2 (although it feels slower that the bloody Windoze XP, I'm flabbergasted by that?!).

If there are any plans of keeping a non CMOV Ubuntu strain alive, I'd be interested to hear about it.

Furthermore all information about what Ubuntu software is impacted by the lack of a complete set of CMOV instuctions in the processor is also very welcome (e.g. only impacts kernel vs impacts X11 directly, etc).

---

### Post by mörgæs on 2012-05-31
In the Buntu family there are no plans of supporting non-CMOV computers. You need to try other distros.

It surprises me that Lubuntu 10.04 is so slow. Does **top** show a heavy load?

---

### Post by martinr on 2012-06-20
> **mörgæs said:**
> In the Buntu family there are no plans of supporting non-CMOV computers. You need to try other distros.

It surprises me that Lubuntu 10.04 is so slow. Does **top** show a heavy load?
That's a shame, so the last of the Socket 7 CPU's outlived Ubuntu. :cool:

They don't build hardware like that any more.

Regarding loads, this is what I get:

```

top - 10:09:32 up 8 min,  2 users,  load average: 2.49, 1.71, 0.90
Tasks: 108 total,   1 running, 106 sleeping,   0 stopped,   1 zombie
Cpu(s): 17.9%us,  8.5%sy,  0.0%ni, 72.6%id,  0.0%wa,  0.7%hi,  0.3%si,  0.0%st
Mem:    250688k total,   242080k used,     8608k free,    11584k buffers
Swap:  2062328k total,        0k used,  2062328k free,   134960k cached

```

107 processes for LUbuntu, pretty much?!

---

### Post by mörgæs on 2012-06-21
> **martinr said:**
> 
107 processes for LUbuntu, pretty much?!

No, that's normal. 

What matters most are the columns %CPU and %MEM just below the text you pasted (that is, below the white bar in **top**).

Anyway, this computer is allowed to be a little under strain. 256 MB memory and a 12 years old CPU...

---

### Post by martinr on 2012-06-25
> **martinr said:**
> I tested with XUbuntu 12.04 beta and I could have sworn that it worked! 

I was able to retest the beta2 and it also runs into the same missing CMOV trouble. I was mistaken and probably tested the beta2 before the processor upgrade. Although the K6-2 is 3 times as fast as the Pentium, it's lacking a complete set of CMOV instructions.

---

### Post by martinr on 2012-06-29
Does somebody know what Ubuntu software is impacted by the lack of a complete set of CMOV instructions in the processor? (e.g. only impacts kernel vs impacts X11 directly, etc).

In the [pre-installation]("https://help.ubuntu.com/12.04/installation-guide/i386/hardware-supported.html#id2615549") manual of 12.04 I found the following:
```

However, Ubuntu precise will not run on i586 or earlier processors. Despite the architecture name "i386", support for actual 80386 processors (and their clones) was dropped with the Sarge (r3.1) release of Debian[2]. (No version of Linux has ever supported the 286 or earlier chips in the series.) Support for i586 and lower processors, as well as for i686 processors without the cmov instruction, was dropped in Ubuntu 10.10. Most i686 and later processors are still supported[3]. 

```

Where references 2 and 3 point to:
```



[2] We have long tried to avoid this, but in the end it was necessary due a unfortunate series of issues with the compiler and the kernel, starting with an bug in the C++ ABI provided by GCC. You should still be able to run Ubuntu on actual 80386 processors if you compile your own kernel and compile all packages from source, but that is beyond the scope of this manual.

[3] Many Ubuntu packages will actually run slightly faster on modern computers as a positive side effect of dropping support for these old chips. The i486, introduced in 1989, has three opcodes (bswap, cmpxchg, and xadd) which the i386, introduced in 1986, did not have. Previously, these could not be easily used by most Ubuntu packages; now they can.

```

This talks about dropping support for the i486, introduced in 1989 and not about the i686 (AMD K6-2) without a complete set of CMOV instructions.

Does somebody know what Ubuntu software is impacted by the lack of a complete set of CMOV instructions in the processor?

---

### Post by martinr on 2012-10-01
> **mörgæs said:**
> 
Lubuntu 10.04 will give you one year more.

After some tuning I've got Lubuntu running okay. During my last upgrade I read that the kerner is supported untin 2015. :)

What support will stop exactly in a year and what will it affect?

---

### Post by mörgæs on 2012-10-01
I don't know exactly which packages are running out of support, and regardless of the support question: As I mentioned before my advice is to consider switching to some (possibly used, but still) younger gear.

---

### Post by martinr on 2012-10-05
> **mörgæs said:**
> I don't know exactly which packages are running out of support, and regardless of the support question: As I mentioned before my advice is to consider switching to some (possibly used, but still) younger gear.
Your advise is noted, but the younger gear is too power hungry for my purposes. I invested a lot of time in optimizing it and would like to enjoy it for a while.

---

### Post by martinr on 2012-12-09
Can I easily move (without re-installing and configuring everything) from the LUbuntu 10.04 LTS Desktop update channel to the server channel so that I can enjoy the 5 year support lifespan of LUbuntu 10.04 LTS Server?

---

### Post by mörgæs on 2012-12-11
There is only one channel. The packages in this channel which are normally used server-side are supported five years, and the desktop packages (including the complete X environment) three years.

---

### Post by martinr on 2013-01-05
> **mörgæs said:**
> There is only one channel. The packages in this channel which are normally used server-side are supported five years, and the desktop packages (including the complete X environment) three years.

Thanks mörgæs, that's good to know.
Might there be an easy way to identify and uninstall all the desktop packages in one go?

---

### Post by mörgæs on 2013-01-06
The easy way would be installing the server ISO. 

It will give you a working system until 2015, but with command line only.

---

