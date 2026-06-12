---
title: "Detection of 4go RAM 32 bits Processor"
date: 2012-12-14
forum: Installation &amp; Upgrades
---

### Post by lfmparente on 2012-12-14
Hi all,

I have 4 Go Ram but I can only see 3, in the BIOS I can see 4096 Ram...

I have the Ubunto 12.10 32 bits and I have read the following:

```
You misunderstand PAE. It allows you to access more REAL RAM (on the  motherboard). The 32-bit address space remains at 4 Gig - of which  (usually) 1 Gig is kernel reserved."
```

If Correct how I can see if how much RAM is reserved for de Kernel, and hence is normal to see only 3Go RAM?

Another problem....

After this:

```
sudo apt-get install linux-generic-pae linux-headers-generic-pae sudo apt-get remove linux-generic linux-image-generic linux-headers-generic
```
and 
```
[COLOR=#0080ff]dpkg[/COLOR] [COLOR=#339933]-l[/COLOR] [COLOR=black]|[/COLOR] [COLOR=#0080ff]grep[/COLOR] linux-image
```

```

ii  linux-image-3.5.0-17-generic              3.5.0-17.28                               i386         Linux kernel image for version 3.5.0 on 32 bit x86 SMP
ii  linux-image-3.5.0-19-generic              3.5.0-19.30                               i386         Linux kernel image for version 3.5.0 on 32 bit x86 SMP
ii  linux-image-extra-3.5.0-17-generic        3.5.0-17.28                               i386         Linux kernel image for version 3.5.0 on 32 bit x86 SMP
ii  linux-image-extra-3.5.0-19-generic        3.5.0-19.30                               i386         Linux kernel image for version 3.5.0 on 32 bit x86 SMP
ii  linux-image-generic                       3.5.0.19.22                               i386         Generic Linux kernel image

```

well ok.... I Have found the following:

```
For permanent change you'll need to edit your /etc/default/grub file -- place a "#" symbol at the start of line GRUB_HIDDEN_TIMEOUT=0.

Save changes and run sudo update-grub to apply changes.
```

But nothing appears....

I know that my processor is compatible with PAE because:
I have run a script and this the result

```
check-my-hardware.py - version: SJ [COLOR=#cc66cc]2009[/COLOR]-[COLOR=#cc66cc]12[/COLOR]-[COLOR=#cc66cc]21[/COLOR] OK, you[COLOR=#ff0000]'re root ANALYSIS: Total of physical memory modules found 4096 MB in 2 memory module(s) [    0.000000] BIOS-e820: [mem 0x0000000000000000-0x000000000009f7ff] usable   [    0.000000] BIOS-e820: [mem 0x0000000000100000-0x00000000bf67ffff] usable   BIOS offers 6122 MB as usable Memory seen by OS 3021 MB BIOS version 08/12/2008 CPU is PAE enabled CPU is 32-bit, and not x86_64 enabled OS is 32-bit without PAE ADVICE: You'[/COLOR]re running a plain [COLOR=#cc66cc]32[/COLOR]-bit OS on a [COLOR=#cc66cc]32[/COLOR]-bit PAE-enabled CPU. Upgrade to the [COLOR=#cc66cc]32[/COLOR]-bit kernel with PAE [COLOR=#ff0000]'linux-generic-pae'[/COLOR] to get access to [COLOR=#0080ff]more[/COLOR] memory 

```:

Thanks for any suggestion!

Best regards.

---

### Post by dino99 on 2012-12-14
you need to install the generic-pae, not the generic.
install & open synaptic to do the changes

sudo apt-get install synaptic
sudo synaptic

---

### Post by lfmparente on 2012-12-14
Hi, thanks for your response;

Well I thought with this line 

```
sudo apt-get install linux-generic-pae linux-headers-generic-pae sudo apt-get remove linux-generic linux-image-generic linux-headers-generic
```

I installed de Kernel with support PAE?


Can you explain how I have to do this?

Thanks,

best regards!

---

### Post by lfmparente on 2012-12-14
> **dino99 said:**
> you need to install the generic-pae, not the generic.
install & open synaptic to do the changes

sudo apt-get install synaptic
sudo synaptic

 				 				**Re: Detection of 4go RAM 32 bits Processor** 			
 			 			 		   		 		 		Hi, thanks for your response;

Well I thought with this line 

 	Code:
 	sudo apt-get install linux-generic-pae linux-headers-generic-pae sudo apt-get remove linux-generic linux-image-generic linux-headers-generic 
I installed de Kernel with support PAE?


Can you explain how I have to do this?

Thanks,

best regards!

---

### Post by mastablasta on 2012-12-14
in 12.10 the pae kernel is installed by default (which give problems to some old maschines).
 
could it be possible that processor doesn't recognise the 4GB.

---

### Post by lfmparente on 2012-12-14
> **mastablasta said:**
> in 12.10 the pae kernel is installed by default (which give problems to some old maschines).
 
could it be possible that processor doesn't recognise the 4GB.

Yes my processor is old, is a T2250.... 

Thanks for your response.

---

### Post by grahammechanical on 2012-12-14
I am confused. I see this in the printout of the script that you ran:

> CPU is PAE enabled CPU is 32-bit, and not x86_64 enabled OS is 32-bit without PAE ADVICE: _You're running a plain 32-bit OS on a 32-bit PAE-enabled CPU._ Upgrade to the 32-bit kernel with PAE 'linux-generic-pae' to get access to more memory

I have underlined the words that I think are important. I am confused because I also understood that Ubuntu 12.10 only came with a PAE kernel. And that the non-PAE versions had been discontinued with Ubuntu 12.10.

Could it be that you are using one of the flavours of Ubuntu that still have a non-PAE kernel available, such as Xubuntu?

[https://help.ubuntu.com/community/EnablingPAE]("https://help.ubuntu.com/community/EnablingPAE")

[http://www.webupd8.org/2012/11/how-to-install-ubuntu-1210-on-non-pae.html]("http://www.webupd8.org/2012/11/how-to-install-ubuntu-1210-on-non-pae.html")

Another thought occurs to me. Did you upgrade to 12.10 from a version of Ubuntu that was a non-pae OS?

Regards.

---

### Post by lfmparente on 2012-12-14
> **grahammechanical said:**
> I am confused. I see this in the printout of the script that you ran:



I have underlined the words that I think are important. I am confused because I also understood that Ubuntu 12.10 only came with a PAE kernel. And that the non-PAE versions had been discontinued with Ubuntu 12.10.

Could it be that you are using one of the flavours of Ubuntu that still have a non-PAE kernel available, such as Xubuntu?

[https://help.ubuntu.com/community/EnablingPAE](https://help.ubuntu.com/community/EnablingPAE)

[http://www.webupd8.org/2012/11/how-to-install-ubuntu-1210-on-non-pae.html](http://www.webupd8.org/2012/11/how-to-install-ubuntu-1210-on-non-pae.html)

Regards.
  
I will try it, thanks.

mY pc is an Acer aspire 5612 AWLmi

---

