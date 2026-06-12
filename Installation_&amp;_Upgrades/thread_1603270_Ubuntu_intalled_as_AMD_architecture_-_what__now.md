---
title: "Ubuntu intalled as AMD architecture - what  now?"
date: 2010-10-22
forum: Installation &amp; Upgrades
---

### Post by Supermule on 2010-10-22
Hi,

I'm trying Ubuntu which was incorrectly installed by Wubi as an AMD architecture (on a Lenovo T500 Core2). Was that Wubis fault or Ubuntu? It gives me a lot of problems because I need some drivers that are only available for i386. 

Can I reinstall with Wubi and force my architecture? Or must I install Ubuntu correct by booting a CD - what are the chances that it will install correct?

Thanks!

-- 
Supermule

---

### Post by lotharmat on 2010-10-22
Hiya - Core 2 Duo's are identified as AMD64 when it comes to installing Ubuntu 64-bit.

If it is working; it is fine!

---

### Post by Supermule on 2010-10-22
> **lotharmat said:**
> Hiya - Core 2 Duo's are identified as AMD64 when it comes to installing Ubuntu 64-bit.

If it is working; it is fine!

But I have a i386 :(. And I need that arch to install my Canon MP 620 printer...

---

### Post by lotharmat on 2010-10-22
Was it the 32-bit or 64-bit you downloaded?

---

### Post by Supermule on 2010-10-22
> **lotharmat said:**
> Was it the 32-bit or 64-bit you downloaded?

Dont know actually "About Ubuntu" doesn't reveal the bits...

---

### Post by luvr on 2010-10-22
> **Supermule said:**
> Dont know actually "About Ubuntu" doesn't reveal the bits...
Try *"System Monitor"* instead (*"System"* -> *"Administration"* -> *"System Monitor"*).

On the *"System"* tab page, you should see a line identifying your kernel, including the architecture (*"i386"* for 32-bit, or *"amd64"* for 64-bit; or possibly even *"pae"* for 32-bit with Physical Address Extensions).

---

### Post by Supermule on 2010-10-22
> **luvr said:**
> Try *"System Monitor"* instead (*"System"* -> *"Administration"* -> *"System Monitor"*).

On the *"System"* tab page, you should see a line identifying your kernel, including the architecture (*"i386"* for 32-bit, or *"amd64"* for 64-bit; or possibly even *"pae"* for 32-bit with Physical Address Extensions).

It says "Kernel Linux 2.6.32-25-generic" ?

---

### Post by luvr on 2010-10-23
> **Supermule said:**
> It says "Kernel Linux 2.6.32-25-generic" ?
Oops... You're right; should have checked before I posted my reply.

The easiest way to query the system architecture is, to the best of my knowledge, via the command line. Just open the Terminal (*"Applications"* -> *"Accessories"* -> *"Terminal"*) and type the following command:
```
dpkg --print-architecture
```
If you subsequently hit the ***<ENTER>*** key, then the system will show you the architecture.

If you really, *really,* ***really*** do not want to open the Terminal, then you could, alternatively, run the system testing utility (*"System"* -> *"Administration"* -> *"System Testing"*). On the welcome screen, hit the *"Next"* button; the utility will then inform you that it is *"gathering information from the system."* Afterwards, hit the *"Deselect All"* button, then hit *"Next"*; the program will then build the report. Finally, click *"View Report"* to open the report in your browser. Under the ***"Summary"*** heading, you will find a line identifying your Ubuntu version and the architecture.

---

### Post by Supermule on 2010-10-27
> **luvr said:**
> 
The easiest way to query the system architecture is, to the best of my knowledge, via the command line. Just open the Terminal (*"Applications"* -> *"Accessories"* -> *"Terminal"*) and type the following command:
```
dpkg --print-architecture
```If you subsequently hit the ***<ENTER>*** key, then the system will show you the architecture.


Thanks - It says "amd64". However this IS an Intel Centrino 2 (Thinkpad T500). Even so, all this is just to be able to setup my printer which is a mainstream Canon MP620. Amazing that there isn't drivers available as such. I keep Googling the same direction which are [here]("http://www.nervous.it/lang/en-us/2009/04/canon-pixma-mp620-wireless-on-ubuntu/"). As you can see the only drivers are "i386" - I have tried and the install halt with a message saying that my architecture is wrong. 

Of course this is especially annoying since this IS compatible with i386. This could turn out to be a show stopper for my short trial of Ubuntu - pity. I only use my laptop for Office tasks but of course printing is a major subset of that :)

   .ExternalClass .ecxhmmessage p { padding: 0px; }.ExternalClass body.ecxhmmessage { font-size: 10pt; font-family: Tahoma; }

---

### Post by Simian Man on 2010-10-27
I run 64-bit Linux and installed 32-bit drivers for my Cannon printer.  The package manager (yum because I use Fedora), just pulled in a bunch of 32-bit libraries and stuff.

What happens when you try to install the drivers?

---

### Post by Supermule on 2010-10-27
> **Simian Man said:**
> I run 64-bit Linux and installed 32-bit drivers for my Cannon printer.  The package manager (yum because I use Fedora), just pulled in a bunch of 32-bit libraries and stuff.

What happens when you try to install the drivers?

It says: 
"dpkg: error processing cnijfilter-common_2.80-1_i386.deb (--install):
 package architecture (i386) does not match system (amd64)"

The problem here is not 64bit v/s 32bit. But Amd v/s i386 I think...Seems odd that Ubuntu chose my architecture as "amd64". Seems even more odd if this is by design!?

---

### Post by mikewhatever on 2010-10-27
AMD64 is the 64bit architecture for both Intel and AMD, and i386 is the 32bit architecture for both Intel and AMD. There is no such thing as Intel only architecture or core2duo architecture.
Wubi downloads the 64bit Ubuntu by default if a 64bit CPU is detected. Read [Wubi FAQ]("http://wubi.sourceforge.net/faq.php") for more info. You'd have to reinstall - get rid of the 64bit and install the 32bit version.

---

### Post by Supermule on 2010-10-27
> **mikewhatever said:**
> AMD64 is the 64bit architecture for both Intel and AMD, and i386 is the 32bit architecture for both Intel and AMD. There is no such thing as Intel only architecture or core2duo architecture.
Wubi downloads the 64bit Ubuntu by default if a 64bit CPU is detected. Read [Wubi FAQ]("http://wubi.sourceforge.net/faq.php") for more info. You'd have to reinstall - get rid of the 64bit and install the 32bit version.

Excellent - I'll reinstall asap. Thanks to you all....

---

### Post by Simian Man on 2010-10-27
> **Supermule said:**
> The problem here is not 64bit v/s 32bit. But Amd v/s i386 I think...Seems odd that Ubuntu chose my architecture as "amd64". Seems even more odd if this is by design!?

No, the problem is the package dependencies.  Your computer is capable of running 64-bit.  If it was not, it firstly would have not installed, and secondly it would not boot up even if you did install it.

Reinstalling with 32-bit will make it so you can install the driver, but it should still be possible with 64-bit.  Like I said, I have that same driver working in 64-bit.

---

