---
title: "newbie Q:  Unable install ubuntu 8.0.4.1 server"
date: 2008-08-30
forum: Installation &amp; Upgrades
---

### Post by aaarathibs on 2008-08-30
Hello Everyone,

Thanks in advance. I am new to installing Linux.
I need a Ubuntu LAMP server running on my laptop and I have following setup, later i will tell about the issues i am facing.


1) Hardware:
HP Pavilion dv6500 laptop
CPU : Intel Core 2 Duo T7100 1.80 Ghz
RAM : 2GB ram

Software:
Windows Vista 32 bit OS.

I have installed Sun xv Virtual Box (Ver 1.6.4)
and has created a portion of 8GB hard disk and 512 MB RAM for the Ubuntu Linux OS.

I downloaded 
ubuntu-8.04.1-server-i386.iso
and Installed.
Installation went perfect. But when i restarted, I got an error:

[B][U]This kernel requires the following feature not present on the CPU : 0:6 
unable to boot - please use a kernel appropriate your cpu [/U][/B]

so I searched internet and saw some people having issues in Core 2 Duo CPU and they had suggested use the other image on the website
ubuntu-8.04.1-server-amd64

Now when try to boot from this CD, i get the following error :-(

**"This Kernel requires an x86-64 cpu, but only detected an i686 cpu. unable to boot - please use a kernel appropriate your cpu" **

So now i have tried both the images on the website. I was not able to figure out where to download the alternative platform CD

I even tried to see if there is anything in grub menu that will help.

But I am a newbie so no idea how to get a new kernel for my laptop. Hopefully some one will give me an iso image that work and everything needed in there.

Please Help.
Thanks
Arati

---

### Post by dsilvia on 2008-11-24
> **aaarathibs said:**
> Hello Everyone,

Thanks in advance. I am new to installing Linux.
I need a Ubuntu LAMP server running on my laptop and I have following setup, later i will tell about the issues i am facing.


1) Hardware:
HP Pavilion dv6500 laptop
CPU : Intel Core 2 Duo T7100 1.80 Ghz
RAM : 2GB ram

Software:
Windows Vista 32 bit OS.

I have installed Sun xv Virtual Box (Ver 1.6.4)
and has created a portion of 8GB hard disk and 512 MB RAM for the Ubuntu Linux OS.

I downloaded 
ubuntu-8.04.1-server-i386.iso
and Installed.
Installation went perfect. But when i restarted, I got an error:

[B][U]This kernel requires the following feature not present on the CPU : 0:6 
unable to boot - please use a kernel appropriate your cpu [/U][/B]

so I searched internet and saw some people having issues in Core 2 Duo CPU and they had suggested use the other image on the website
ubuntu-8.04.1-server-amd64

Now when try to boot from this CD, i get the following error :-(

**"This Kernel requires an x86-64 cpu, but only detected an i686 cpu. unable to boot - please use a kernel appropriate your cpu" **

So now i have tried both the images on the website. I was not able to figure out where to download the alternative platform CD

I even tried to see if there is anything in grub menu that will help.

But I am a newbie so no idea how to get a new kernel for my laptop. Hopefully some one will give me an iso image that work and everything needed in there.

Please Help.
Thanks
Arati


Hi!

I am not a newbie and I'm having exactly the same problem. I have downloaded and tried ***_every_*** 8.04 and 8.10 image I could find, desktop and server, live cd and alternative, cd iso and dvd iso, and they all say the same thing... "use appropriate kernel for your cpu"!](*,)

If the 8.x amd64 iso's are plain vanilla amd64 (implying emt64 compatibility) why is an "exact match" instead of an "at least" cpu check used? It would appear that this is what is being done, but it's only a swag on my part!:?

My platform particulars:
```

----[ EVEREST Ultimate Edition ]----------------------------------------------------

Homepage                    http://www.lavalys.com/
Report Type                 Report Wizard
Operating System            Microsoft Windows Vista Ultimate 6.0.6001 (Vista Retail)

----[ CPU ]-------------------------------------------------------------------------

CPU Properties:
  CPU Type                  QuadCore Intel Core 2 Quad Q6600, 2400 MHz (9 x 267)
  CPU Alias                 Kentsfield
  CPU Stepping              B3
  Instruction Set           x86, x86-64, MMX, SSE, SSE2, SSE3, SSSE3
  Original Clock            2400 MHz

Multi CPU:
  Motherboard ID            nVidia C55MCP51
  CPU #1                    Intel(R) Core(TM)2 Quad CPU @ 2.40GHz, 2400 MHz
  CPU #2                    Intel(R) Core(TM)2 Quad CPU @ 2.40GHz, 2400 MHz
  CPU #3                    Intel(R) Core(TM)2 Quad CPU @ 2.40GHz, 2400 MHz
  CPU #4                    Intel(R) Core(TM)2 Quad CPU @ 2.40GHz, 2400 MHz

CPU Manufacturer:
  Company Name              Intel Corporation
  Product Information       http://www.intel.com/products/processor

----[ BIOS ]------------------------------------------------------------------------

BIOS Properties:
  BIOS Type                 AMI
  BIOS Version              V1.7
  System BIOS Date          07/29/08
  Video BIOS Date           07/04/07

BIOS Manufacturer:
  Company Name              American Megatrends Inc.
  Product Information       http://www.ami.com/amibios
  BIOS Upgrades             http://www.esupport.com/biosagent/index.cfm?refererid=40

----[ Operating System ]------------------------------------------------------------

Operating System Properties:
  OS Name                   Microsoft Windows Vista Ultimate
  OS Kernel Type            Multiprocessor Free (64-bit)
  OS Version                6.0.6001 (Vista Retail)
  OS Service Pack           Service Pack 1
  OS Installation Date      11/12/2008
  OS Root                   C:\Windows

------------------------------------------------------------------------------------

The names of actual companies and products mentioned herein
may be the trademarks of their respective owners.


```

I'm really at a loss as to why the installation doesn't recognize the cpu... :(

Any direction would be appreciated! :???:

Advice re: BIOS upgrades, BIOS settings, and redownloading iso's, however, would not be very helpful since they've been tried or don't really apply. :frown: The BIOS is completely up to date and the settings are fine. I've downloaded and redownloaded now for 2 days to no avail, so that's not it either. I really feel it's a problem with the installer(s).:-({|=

tia:

---

### Post by PmDematagoda on 2008-11-24
Please post the output of:-
```
cat /etc/apt/sources.list
```

---

### Post by dsilvia on 2008-11-25
> **PmDematagoda said:**
> Please post the output of:-
```
cat /etc/apt/sources.list
```

from where? (see, I can be terse and cryptic, too!;)

---

### Post by PmDematagoda on 2008-11-26
> **dsilvia said:**
> from where? (see, I can be terse and cryptic, too!;)

From a terminal. Bring up a terminal by pressing Ctrl+F2, entering "gnome-terminal" and pressing "Run".

---

### Post by dsilvia on 2008-11-26
> **PmDematagoda said:**
> From a terminal. Bring up a terminal by pressing Ctrl+F2, entering "gnome-terminal" and pressing "Run".

I'm afraid you seem to be missing the point in this thread...

Let me reiterate the scenario:

System Platform:  Windows

Software Used:    Virtual Machine

Need to Install:  Ubuntu 8.04.01 amd64

Problem: No Ubuntu 8.04 or 8.10 installs correctly due to the installation erroring out because of what it believes to be an incoompatible CPU.

Specific Error Message:

"This Kernel requires an x86-64 cpu, but only detected an i686 cpu. unable to boot - please use a kernel appropriate your cpu"


Now you come along and say... "well, give me some information from Ubuntu...". But you see, there can be no information from Ubuntu because it fails to install, there is nowhere to login, there's no way to open a terminal or anything else to allow investigation!:rolleyes:

To paraphrase one of your own clever quips that went:

> perhaps if you had decided to create a thread of your own, then you may have already solved your problem

Well...

> perhaps if you read these posts more thoroughly and weren't so keen on finding fault and exhibiting aloof behavior with haughty condescension, then you may have saved yourself some time in inapplicable replies.

Please, if you cannot give clear, credible, authoritative, and exact descriptions/instructions/suggestions as feedback, don't waste your time and ours![-o<

---

### Post by PmDematagoda on 2008-11-26
Well, thanks for taking the time to explain it. However, if you looked carefully, the thread in which you posted before had a different situation where the OP was trying to install Ubuntu 64-bit on a non-64 bit processor. So now you should understand why it is better to create a thread of your own.

About your problem, is this only with Ubuntu in particular or does it occur with other distributions like Fedora or OpenSUSE as well?

---

