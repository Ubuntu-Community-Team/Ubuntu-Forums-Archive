---
title: "PAE kernel does not see all 4GB of RAM"
date: 2010-02-05
forum: Installation &amp; Upgrades
---

### Post by bakhy on 2010-02-05
I've just installed the linux-generic-pae package, and I've checked the GRUB menu, that kernel gets loaded, but I still see only 3GB of RAM. BIOS says I have 4GB.

I'm on Karmic, 2.6.31-19-generic-pae kernel.

---

### Post by bakhy on 2010-02-05
Also, a side-problem, ATI Catalyst drivers don't work with the PAE kernel. Reading through the Xorg log I found that there's something wrong with the kernel module, and DRI fails because of it... Do I have to do something extra when I install a different kernel to make it work with ATI drivers?

---

### Post by tgalati4 on 2010-02-05
Go through your BIOS settings.  Sometimes there is a PAE switch to activate.  Also, your motherboard chipset needs to handle PAE.

---

### Post by Cabs21 on 2010-02-05
are you using the 32-bit version of PAE Kernel or 64-bit version.  32-bit OS's can not see more then 3GB of RAM.  64-Bit can see as high as 32GB of RAM (i think)  This is probably your issue

---

### Post by tgalati4 on 2010-02-06
I'm running 32-bit Hardy on a dell poweredge server with pae.  It can see 4.5gb I have on the machine.  The older Xeon processors are 32-bit.

---

### Post by Cabs21 on 2010-02-08
> **tgalati4 said:**
> I'm running 32-bit Hardy on a dell poweredge server with pae.  It can see 4.5gb I have on the machine.  The older Xeon processors are 32-bit.

Check this site out because 32-Bit OS can not address more then 4GB or RAM.  That is the limitation of the OS.  

[http://en.wikipedia.org/wiki/32-bit](http://en.wikipedia.org/wiki/32-bit)

---

### Post by sanderj on 2010-02-08
Run the attached python script to get information about your system.

> 
sudo python check-my-hardware.py

Post the output here. See my output below.

HTH


```
sander@quirinius:~$ sudo python check-my-hardware.py 
check-my-hardware.py - version: SJ 2009-12-21
OK, you're root
ANALYSIS:
Total of physical memory modules found 1024 MB in 1 memory module(s)
BIOS offers 1013 MB as usable
Memory seen by OS 993 MB
BIOS version 04/14/2009
CPU is PAE enabled
CPU is 32-bit, and not x86_64 enabled
OS is 32-bit with PAE
ADVICE:
Your physical memory is less than 3200 MB, and your system does not need special memory treatment
sander@quirinius:~$ 
sander@quirinius:~$ python check-my-hardware.py 
check-my-hardware.py - version: SJ 2009-12-21
please run as root with 'sudo'
sander@quirinius:~$ 
```

---

### Post by cascade9 on 2010-02-08
> **Cabs21 said:**
> are you using the 32-bit version of PAE Kernel or 64-bit version. 32-bit OS's can not see more then 3GB of RAM. 64-Bit can see as high as 32GB of RAM (i think) This is probably your issue

Its a bit higher than 32GB. The theoretical limit is 16 exabytes (16 million terabytes). AFAIK, that isnt going to be common any time soon, and AMD64 (and I would assume intel 64) cant see that much, but AMD64 can see 256 TB of RAM.  

> **Cabs21 said:**
> Check this site out because 32-Bit OS can not address more then 4GB or RAM.  That is the limitation of the OS.  

[http://en.wikipedia.org/wiki/32-bit](http://en.wikipedia.org/wiki/32-bit)

The 4GB limit from 32bit is exactly what PAE is meant to get around- 

> n [computing]("http://en.wikipedia.org/wiki/Computing"), **Physical Address Extension** (**PAE**) is a feature first implemented in the [Intel Pentium Pro]("http://en.wikipedia.org/wiki/Intel_Pentium_Pro") to allow [x86]("http://en.wikipedia.org/wiki/X86") processors to access more than 4 [gigabytes]("http://en.wikipedia.org/wiki/Gigabyte") of [random access memory]("http://en.wikipedia.org/wiki/Random_access_memory") if the operating system supports it.[http://en.wikipedia.org/wiki/Physical_Address_Extension](http://en.wikipedia.org/wiki/Physical_Address_Extension)

---

### Post by Cabs21 on 2010-02-09
> The 4GB limit from 32bit is exactly what PAE is meant to get around-Interesting....very interesting.

I looked this up shortly after posting and realized I was only half right since I did not know what PAE was. :confused: But now I am more learned on the subject ;)

---

### Post by bakhy on 2010-02-14
@sanderj
```

josip@extensa:~/Desktop$ sudo python ./check-my-hardware.py 
./check-my-hardware.py - version: SJ 2009-12-21
OK, you're root
ANALYSIS:
Total of physical memory modules found 4096 MB in 2 memory module(s)
BIOS offers 3064 MB as usable
Memory seen by OS 3019 MB
BIOS version 08/05/2008
CPU is PAE enabled
CPU is x86_64 64-bit enabled
OS is 32-bit without PAE
ADVICE:
Your BIOS is not offering all of your physical memory. Try to update your BIOS, and/or enable 'memory hole rempapping / hoisting' in your BIOS to get more usable memory

```
Will I have to install Windows to update my BIOS?.. :/ -- edit: downloading this bootable cd from acer (?)

p.s. Thank you!

---

### Post by sanderj on 2010-02-14
> **bakhy said:**
> 

Will I have to install Windows to update my BIOS?.. :/

Well, it depends: my own BIOS (Asus M2A-VM HDMI) can be updated from a USB stick: by saving the new BIOS-firmware to a USB-stick, then booting into the BIOS, and then instruct the BIOS to update itself with the new version on the USB-stick.

So consult your BIOS or BIOS' manual how to update your BIOS.

---

### Post by lotuseclat79 on 2010-04-04
The script check-my-hardware.py definitely helped (I had to manually execute the cmds internal to the script), but had the following error:
Traceback (most recent call last):
  File "debug.py", line 31, in <module>
    dimmtotal += int(thisline.split()[1])
ValueError: invalid literal for int() with base 10: 'Size;'

The fix is to modify the cmd to:
'dmidecode | egrep -A8 -i -e "Memory Device" | grep -i MB | egrep -v Range'

Now I know that I must at least upgrade my BIOS as only 3GB of 4GB is usable, however, that might not even work due to the following restriction in my motherboard's CPU chip/per documentation - I'll upgrade to find out:
Intel Desktop Motherboard: D925XECV2 w/4GB RAM w/PAE and
Note: System resources (such as PCI and PCI Express*) require physical memory address locations that reduce available memory addresses above 3GB.  This may result in less than 4GB of memory being available to the operating system and applications.

-- Tom

---

### Post by sanderj on 2010-04-04
> **lotuseclat79 said:**
> The script check-my-hardware.py definitely helped (I had to manually execute the cmds internal to the script), but had the following error:
Traceback (most recent call last):
  File "debug.py", line 31, in <module>
    dimmtotal += int(thisline.split()[1])
ValueError: invalid literal for int() with base 10: 'Size;'

Anyone know what the correct code is to fix this problem?



I'm the author of the script, so I'm curious:

1: what's the exact command you use to (try to) run the script? And what's the output?

2: what's the full output of the 


```
sudo dmidecode | egrep -A8 -i -e "Memory Device" | grep -i MB

```

See my output here:


```
ubuntu@ubuntu:~$ sudo dmidecode | egrep -A8 -i -e "Memory Device" | grep -i MB
	Size: 1024 MB
ubuntu@ubuntu:~$ 
```

---

### Post by lotuseclat79 on 2010-04-04
Hi sanderj,

Read post #12 posted just before your post #13 for the fix.  My full output prior to the fix (thus the error) was:
	Size: 1024 MB
	Size: 1024 MB
	Size: 1024 MB
	Size: 1024 MB
	Range Size: 4194176 MB

After I made the fix while running the standard Ubuntu 9.10 Live CD, I decided to try my customized Live CD w/PAE and your script properly reported the line:
OS is 32-bit with PAE.  

I had gone to the trouble of custom compiling the 2.6.31-20.58 linux-source w/64-bit HIGH-MEM and kernel-debugging turned off, but now, since I have more information, I will pursue a BIOS update to see what happens - I've had it for well over a year, but have not been motivated to install it until now.

-- Tom

---

### Post by sanderj on 2010-04-04
> **lotuseclat79 said:**
> Hi sanderj,

Read post #12 posted just before your post #13 for the fix.  My full output prior to the fix (thus the error) was:
	Size: 1024 MB
	Size: 1024 MB
	Size: 1024 MB
	Size: 1024 MB
	Range Size: 4194176 MB

After I made the fix while running the standard Ubuntu 9.10 Live CD, I decided to try my customized Live CD w/PAE and your script properly reported the line:
OS is 32-bit with PAE.  

I had gone to the trouble of custom compiling the 2.6.31-20.58 linux-source w/64-bit HIGH-MEM and kernel-debugging turned off, but now, since I have more information, I will pursue a BIOS update to see what happens - I've had it for well over a year, but have not been motivated to install it until now.

-- Tom

'egrep -v Range' (or: 'grep -vi range') is a good workaroud. I'll put that in my updated script; it avoids that 'Size:' is tried to be converted into an int.

Can you post the output of your updated script here? Can't you run a PAE-kernel? That's much eachter than your own kernel.

---

### Post by lotuseclat79 on 2010-04-04
Hi sanderj,

The output of the modified script w/Ubuntu 9.10 Live CD is;
ubuntu@ubuntu:~/Desktop$ sudo python ./check-my-hardware.py
./check-my-hardware.py - version: SJ 2009-12-21
OK, you're root
ANALYSIS:
Total of physical memory modules found 4096 MB in 4 memory module(s)
BIOS offers 2941 MB as usable
Memory seen by OS 2896 MB
BIOS version 10/12/2004
CPU is PAE enabled
CPU is 32-bit, and not x86_64 enabled
OS is 32-bit without PAE
ADVICE:
Your BIOS is not offering all of your physical memory. Try to update your BIOS, and/or enable 'memory hole rempapping / hoisting' in your BIOS to get more usable memory

Yes, I can run a PAE kernel, as I mentioned, my customized PAE Live CD, however, the BIOS is not cooperating.  I'll have to install the latest BIOS for my MB to see if it makes a difference or not.  Of course, I could email Intel support and ask them, but since I also have the original BIOS installation code and instructions, I'll have to go back and refresh my memory on the instructions for installing the latest BIOS to make sure I don't screw it up (as so many do).

-- Tom

---

### Post by Slim Odds on 2010-04-04
It is SOOOO easy to find this information these days. You people who keep making incorrect statements need to stop and take a look around before wasting peoples time and leading them in the wrong direction.

From this page: [http://en.wikipedia.org/wiki/Physical_Address_Extension](http://en.wikipedia.org/wiki/Physical_Address_Extension)> **Linux**

 The [Linux kernel]("http://en.wikipedia.org/wiki/Linux_kernel") includes full PAE mode support starting with version 2.3.23,[[3]]("http://en.wikipedia.org/wiki/Physical_Address_Extension#cite_note-2") enabling access of up to 64 GB of memory on 32-bit machines. A PAE-enabled Linux-kernel requires that the CPU also support PAE. As of 2009[[update]]("http://en.wikipedia.org/w/index.php?title=Physical_Address_Extension&action=edit")[*[citation needed]("http://en.wikipedia.org/wiki/Wikipedia:Citation_needed")*], many common Linux distributions are beginning to use a PAE-enabled kernel as the distribution-specific default[[4]]("http://en.wikipedia.org/wiki/Physical_Address_Extension#cite_note-3") because it adds the NX bit [[5]]("http://en.wikipedia.org/wiki/Physical_Address_Extension#cite_note-4").

Took me about 12 seconds.

---

### Post by psusi on 2010-04-04
Yes, the PAE kernel can address up to 64gb of physical ram, however many motherboards can not remap physical addresses around reserved blocks.  If, for example, your video card is using a 256 meg address in the area just under the 4gb mark, in order to address the physical ram using those same addresses, your motherboard must support remapping those physical ram addresses to higher addresses, otherwise requests to those addresses go to the video card, not the DIMMs.  Many motherboards can not do this, so that memory on the DIMMs is not accessible.

---

### Post by sanderj on 2010-04-05
> **lotuseclat79 said:**
> 
Total of physical memory modules found 4096 MB in 4 memory module(s)
BIOS offers 2941 MB as usable
Memory seen by OS 2896 MB
BIOS version 10/12/2004


Yes, you need a BIOS update. ;-)

IMHO, a BIOS update is not that difficult or dangerous; I've done it a lot of times. So if you can find a newer BIOS, use it.

---

### Post by lotuseclat79 on 2010-04-05
Hi sanderj,

I have been mulching over the raw data - only some of which you address in your script, and I would like to suggest a few changes:

1) the data from the memory map indicates {reserved, usable, ACPI NVS|data}, but it would be useful to the user to see both the reserved below and above 3GB w/4GB or more of RAM.
2) a computation of potentially recoverable RAM above 3GB w/memory hoisting.

In my case, the potential is about 3/4 GB!

I'll flash the BIOS after I get my taxes done and mailed (might need some forms - and I can't risk losing my system before that), but that is no guarantee that my updated BIOS will incorporate memory hoisting, etc. to recover usable RAM for the OS given it is no longer supported and the last BIOS update is November 29, 2006.

-- Tom

---

### Post by sanderj on 2010-04-05
> **lotuseclat79 said:**
> Hi sanderj,

I have been mulching over the raw data - only some of which you address in your script, and I would like to suggest a few changes:

1) the data from the memory map indicates {reserved, usable, ACPI NVS|data}, but it would be useful to the user to see both the reserved below and above 3GB w/4GB or more of RAM.
2) a computation of potentially recoverable RAM above 3GB w/memory hoisting.

In my case, the potential is about 3/4 GB!


OK, good point. So separately show memory above the 0x0000000100000000 = 4.2 GB (in decimal) boundary. Question: is the 0000000100000000 always shown as a boundary, like in my dmesg below?
Oh wait: your dmesg does show NOT show anything above 0000000100000000 as your BIOS does not understand that, right?



EDIT: 
Assuming your dmesg does not show anything above 0000000100000000, here's my new script:


[http://wattcher.015.info/check-my-hardware.py]("http://wattcher.015.info/check-my-hardware.py")


Can you run that and post the output here? 



```
sander@athlon64:~$ dmesg | grep usable
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009f000 (usable)
[    0.000000]  BIOS-e820: 0000000000100000 - 00000000dbee0000 (usable)
[    0.000000]  BIOS-e820: 0000000100000000 - 0000000120000000 (usable)
[    0.000000] e820 update range: 0000000000000000 - 0000000000010000 (usable) ==> (reserved)
[    0.000000] e820 update range: 00000000dbf00000 - 0000000100000000 (usable) ==> (reserved)
[    0.000000]  modified: 0000000000010000 - 000000000009f000 (usable)
[    0.000000]  modified: 0000000000100000 - 00000000dbee0000 (usable)
[    0.000000]  modified: 0000000100000000 - 0000000120000000 (usable)
sander@athlon64:~$
```

---

### Post by lotuseclat79 on 2010-04-06
Hi sanderj,

Here are several outputs:
ubuntu@ubuntu:~/Desktop$ dmesg | grep BIOS-e820
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009fc00 (usable)
[    0.000000]  BIOS-e820: 000000000009fc00 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000e6000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 00000000b7e2fc00 (usable)
[    0.000000]  BIOS-e820: 00000000b7e2fc00 - 00000000b7e3fc0e (ACPI NVS)
[    0.000000]  BIOS-e820: 00000000b7f10000 - 00000000b7f30000 (reserved)
[    0.000000]  BIOS-e820: 00000000b7f30000 - 00000000b7f40000 (ACPI data)
[    0.000000]  BIOS-e820: 00000000b7f40000 - 00000000b7ff0000 (ACPI NVS)
[    0.000000]  BIOS-e820: 00000000b7ff0000 - 00000000b8000000 (reserved)
[    0.000000]  BIOS-e820: 00000000e0000000 - 00000000f0000000 (reserved)
[    0.000000]  BIOS-e820: 00000000fed13000 - 00000000fed1a000 (reserved)
[    0.000000]  BIOS-e820: 00000000fed1c000 - 00000000feda0000 (reserved)

ubuntu@ubuntu:~/Desktop$ dmesg | grep usable
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009fc00 (usable)
[    0.000000]  BIOS-e820: 0000000000100000 - 00000000b7e2fc00 (usable)
[    0.000000] e820 update range: 0000000000002000 - 0000000000006000 (usable) ==> (reserved)
[    0.000000]  modified: 0000000000000000 - 0000000000002000 (usable)
[    0.000000]  modified: 0000000000006000 - 000000000009fc00 (usable)
[    0.000000]  modified: 0000000000100000 - 00000000b7e2fc00 (usable)

ubuntu@ubuntu:~/Desktop$ sudo python check-my-hardware.py
check-my-hardware.py - version: SJ 2009-04-06
OK, you're root
ANALYSIS:
Total of physical memory modules found 4096 MB in 4 memory module(s)
BIOS offers 2941 MB as usable
BIOS offers 2941 MB as 'modified' usable
Memory seen by OS 2896 MB
BIOS version 10/12/2004
CPU is PAE enabled
CPU is 32-bit, and not x86_64 enabled
OS is 32-bit without PAE
Summary:
Memory difference between DIMM hardware and BIOS offering 1155 MB
Memory difference between BIOS offering and memory seen by OS 45 MB
Memory difference between DIMM hardware and memory seen by OS 1200 MB
ADVICE:
Your BIOS is not offering all of your physical memory. Try to update your BIOS, and/or enable 'memory hole rempapping / hoisting' in your BIOS to get more usable memory

I'm not really sure what you new output means in my case, since I have only 4GB RAM.

I was only interested in identifying "potentially recoverable usable" RAM between the highest usable RAM (just under 3GB) and up to 4GB if memory remapping and hoisting is able to recover it.

So my question is What does the following output mean in those terms?:
Memory difference between DIMM hardware and BIOS offering 1155 MB
Memory difference between BIOS offering and memory seen by OS 45 MB
Memory difference between DIMM hardware and memory seen by OS 1200 MB

If you could interpret that for your three new lines in those terms, it would be more helpful to the user (at least to me).

-- Tom

---

### Post by dino99 on 2010-04-06
even if you use pae kernel you have first to enable ram mapping into your BIOS.

---

### Post by Slim Odds on 2010-04-06
> **psusi said:**
> Yes, the PAE kernel can address up to 64gb of physical ram, however many motherboards can not remap physical addresses around reserved blocks.  If, for example, your video card is using a 256 meg address in the area just under the 4gb mark, in order to address the physical ram using those same addresses, your motherboard must support remapping those physical ram addresses to higher addresses, otherwise requests to those addresses go to the video card, not the DIMMs.  Many motherboards can not do this, so that memory on the DIMMs is not accessible.

True.

But my point was that many people are making uninformed and incorrect statements that are easy to check. They, themselves, should check before misinforming the innocent and potentially wasting someones time.

---

### Post by Slim Odds on 2010-04-06
> **dino99 said:**
> even if you use pae kernel you have first to enable ram mapping into your BIOS.

Absolutely!

Without more than 32 bits of hardware memory address space, there is no 4GB+ no matter what OS you use.

---

### Post by sanderj on 2010-04-06
Tom,

Would this text be useful:

[INDENT]Your BIOS is not offering all of your physical memory. **You now loose about 1155 MB of memory.**
Try to update your BIOS, and/or enable 'memory hole rempapping / hoisting' in your BIOS to get more usable memory
[/INDENT]

Let me know.

---

### Post by lotuseclat79 on 2010-04-07
Hi sanderj,

With a bit more digging, I have isolated the issue to the fact that my MB will not be helped by updating the BIOS because Intel MB w/945 and earlier chipsets do no support memory hole remapping/hoisting in the BIOS.

But, thanks for all of your effort - I hope I helped to provide feedback that was useful to you with your handy tool.

I have also been looking into the possibility of reverse engineering the BIOS - lots of new and exciting happenings out there: flashrom and superiotool packages for ubuntu, and the fact that I have 1024 KB of flash ROM and only 64 KB runtime executable - means there is room for improvement, since apparently the so-called Linux BIOS effort now SmartFirmware (CodeGen) and Openfirmware (Firmworks) re: OpenBIOS efforts are making inroads, but the BIOSes w/o memory remapping looks like a neglected market wrt 4GB usage at the user level - unfortunately, due to the other items that need memory either reserved/etc. like PCI, its like there is a focus on new hardware development and an attitude of instead of fixing/retrofitting the BIOS problem - let them buy new hardware.  The notion is that with only 4GB of RAM, at most you can probably only hope to use 3.5 w/memory remapping anyway and if you add new hardware to your rig - you lose - unless you have either a 64-bit processor with RAM expansion capability above 4GB (for the hardware addons, etc).

Thanks,

-- Tom

---

### Post by lotuseclat79 on 2010-04-07
> **Slim Odds said:**
> True.

But my point was that many people are making uninformed and incorrect statements that are easy to check. They, themselves, should check before misinforming the innocent and potentially wasting someones time.

> **Slim Odds said:**
> It is SOOOO easy to find this information these days. You people who keep making incorrect statements need to stop and take a look around before wasting peoples time and leading them in the wrong direction.

From this page: [http://en.wikipedia.org/wiki/Physical_Address_Extension](http://en.wikipedia.org/wiki/Physical_Address_Extension)

Took me about 12 seconds.
Hi Slim Odds,

The issue in my case - has not been about the Linux kernel supporting PAE, which it has for some time now, but finding out whether or not my BIOS can be remapped (Intel sucks at telling anyone about this in their documentation).  My processor has always supported PAE, but I can't use it even with 4GB due to the limitations of my chipset/MB - and Intel's decision not to upgrade it with memory remapping/hoisting - at least if the would have provided it, I would probably be able to use 3.5GB, but no such luck.

Further, it appears that BIOS is a neglected area in terms of vendors that just want to push new hardware out the door to make the bottom line this financial quarter.

Luckily, lots of new things are happening on the BIOS front.  See my previous post to this.

Cheers,

-- Tom

---

### Post by Slim Odds on 2010-04-07
> **lotuseclat79 said:**
> Hi Slim Odds,

The issue in my case - has not been about the Linux kernel supporting PAE, which it has for some time now, but finding out whether or not my BIOS can be remapped (Intel sucks at telling anyone about this in their documentation).  My processor has always supported PAE, but I can't use it even with 4GB due to the limitations of my chipset/MB - and Intel's decision not to upgrade it with memory remapping/hoisting - at least if the would have provided it, I would probably be able to use 3.5GB, but no such luck.

Further, it appears that BIOS is a neglected area in terms of vendors that just want to push new hardware out the door to make the bottom line this financial quarter.

Luckily, lots of new things are happening on the BIOS front.  See my previous post to this.

Cheers,

-- Tom

I'm sorry that some people misunderstood my original comment, which was to address these:> are you using the 32-bit version of PAE Kernel or 64-bit version.   [COLOR=Red]32-bit OS's can not see more then 3GB of RAM.[/COLOR]  64-Bit can see as high as  32GB of RAM (i think)  This is probably your issue> Check this site out [COLOR=Red]because 32-Bit OS can not address more then 4GB or  RAM.  That is the limitation of the OS[/COLOR].  Which are completely false.

---

### Post by lotuseclat79 on 2010-04-08
Hi Slim Odds,

We appear to be on the same page:

While it is true that a 32-bit OS alone cannot address more than 4GB, with a PAE endowed CPU, a 32-bit OS kernel can address up to 36-bits of address space which extends the virtual address space from 4GB to 64GB.  Refer to second paragraph at [Physical Address Extension](http://en.wikipedia.org/wiki/Physical_Address_Extension).  

However, it is the BIOS limitation of not having memory remapping that restricts the OS from making available usable memory between 3-4GB.

The interplay between a BIOS and a cpu w/PAE and 4GB of RAM is limited by the ability of the BIOS to memory remap or not with 4GB.  If the BIOS vendor would accomodate memory remapping between 3-4GB in a RAM limited to 4GB, then approximately 3.5 GB could potentially be usable - but due to hardware innovations proceeding at a rapid pace, many vendors decided to punt on MBs/chipsets with those limitations.

Cheers,

-- Tom

---

### Post by Slim Odds on 2010-04-08
> **lotuseclat79 said:**
> Hi Slim Odds,

We appear to be on the same page:

...

Totally agree......

One of the problems that we have in these forums is that there are some very inexperienced people trying to do some complicated stuff.

---

