---
title: "With PAE, still limited to 3.00 GB"
date: 2010-07-27
forum: Installation &amp; Upgrades
---

### Post by fishtoprecords on 2010-07-27
I've got a system running 10.04 32 bit. Its got 4GB of ram, but only seems to use 3.0. I expected that it could use 3.something, with some blocked out for video buffers, LPT: support, etc.

I really could use as much memory as I can get. I don't want to switch to 64 bit, because the hardware is limited to 4GB of ram, and I expect that the 64 bit code is a bit flabbier (longer instuctions, etc.) than the 32.

I've installed the latest PAE packages. Uname reports:


Linux tools 2.6.32-24-generic-pae #38-Ubuntu SMP Mon Jul 5 10:54:21 UTC 2010 i686 GNU/Linux

 free  -m
          ```
   total       used       free     shared    buffers     cached
Mem:          3022       2224        798          0        207        976
-/+ buffers/cache:       1039       1983
Swap:         3922          0       3922
```

Is it possible to get it to use more than 3.00 GB? What do I do to enable it?

Thanks
pat

---

### Post by davidmohammed on 2010-07-27
double check that in synaptic manager that both linux-generic-pae and linux-headers-generic-pae are installed.

If they are, also double check you are definitely booting with the pae kernel through displaying grub (shift on boot).

If both of these pass - then check your bios.  Some bios settings are either limited on the RAM that it supports, or there is a setting you need to enable.  What RAM does your bios claim to see?

---

### Post by fishtoprecords on 2010-07-27
> **davidmohammed said:**
> double check that in synaptic manager that both linux-generic-pae and linux-headers-generic-pae are installed.
If they are, also double check you are definitely booting with the pae kernel through displaying grub (shift on boot).
Both of these pass. Uname shows pae as well.

Will check the bios and get back

---

### Post by Icarus315 on 2010-07-27
I know you stated that you don't like 64-bit but I urge you to reconsider.  On average 64-bit executables (not data) are 9% or so larger and run on average 4% faster.  These numbers by themselves are not that great a reason to switch to 64-bit.  The main, and best, reason to switch to 64-bit is if memory requirements prompt it.  You are being prompted, so have a serious decision to make.

My experience with 64-bit is that I don't notice it's not 32-bit.  If you install Ubuntu Restricted Extras in Synaptic you'll inherit 32-bit compatibility libraries for the code that absolutely must be 32-bit (practically nothing) and you'll also get the 32-bit Adobe Flash set up correctly.  64-bit consumes a small fraction more in hard-drive space but on any modern system you shouldn't even notice it.

What do you think?

---

### Post by fishtoprecords on 2010-07-27
my big desktop, 8GB ram, quad core, works great in 64. There were problems with things like Flash and Skype, but even they are a lot better these days.

I may consider it, but the system (a laptop) is maxed at 4GB. I just checked the bios, and there is no mention of memory limits, shaddow IO buffers, etc. so I don't see anything to adjust to free PAE to use more.

Its an older system, Lenovo, I'm happy with it, except when I am running MySql, Apache, GlassFish, Netbeans, my application, Thunderbird, Chrome, Firefox, etc. I just run out of real memory and it starts to swap.

If I had to get a new one, I'd just get one with 6 or 8GB to start and go 64 bit from day one.

Thanks

---

### Post by Icarus315 on 2010-07-27
You're welcome. ;)

---

### Post by davidmohammed on 2010-07-27
> **fishtoprecords said:**
> 
I may consider it, but the system (a laptop) is maxed at 4GB. I just checked the bios, and there is no mention of memory limits, shaddow IO buffers, etc. so I don't see anything to adjust to free PAE to use more.


does the BIOS report 4GB?

I dont use PAE myself - but if you use

sudo dmidecode

you should see something like
System Configuration Options

Handle 0x0014, DMI type 16, 15 bytes
Physical Memory Array
	Location: System Board Or Motherboard
	Use: System Memory
	Error Correction Type: None
	_**Maximum Capacity: 3 GB**_
	Error Information Handle: Not Provided
	Number Of Devices: 2

Another possibly - a faulty memory stick?

---

### Post by cascade9 on 2010-07-27
> **fishtoprecords said:**
> I may consider it, but the system (a laptop) is maxed at 4GB. I just checked the bios, and there is no mention of memory limits, shaddow IO buffers, etc. so I don't see anything to adjust to free PAE to use more.

Its an older system, Lenovo, I'm happy with it, except when I am running MySql, Apache, GlassFish, Netbeans, my application, Thunderbird, Chrome, Firefox, etc. I just run out of real memory and it starts to swap.

What model Lenovo? IIRC, there were a few chipsets that were advertised as 'supporting 4GB', and yeah, they work with 4GB, but they can never see more than 3GB.

---

### Post by fishtoprecords on 2010-07-27
> **davidmohammed said:**
> does the BIOS report 4GB?

I dont use PAE myself - but if you use

sudo dmidecode


The BIOS doesn't report anything about memory. 

The result of your command is

```

Handle 0x0029, DMI type 16, 15 bytes
Physical Memory Array
	Location: System Board Or Motherboard
	Use: System Memory
	Error Correction Type: None
	Maximum Capacity: 2 GB
	Error Information Handle: Not Provided
	Number Of Devices: 2

Handle 0x0008, DMI type 6, 12 bytes
Memory Module Information
	Socket Designation: DIMM Slot 1
	Bank Connections: 0 3
	Current Speed: Unknown
	Type: DIMM SDRAM
	Installed Size: 2048 MB (Double-bank Connection)
	Enabled Size: 2048 MB (Double-bank Connection)
	Error Status: OK

Handle 0x0009, DMI type 6, 12 bytes
Memory Module Information
	Socket Designation: DIMM Slot 2
	Bank Connections: 4 7
	Current Speed: Unknown
	Type: DIMM SDRAM
	Installed Size: 2048 MB (Double-bank Connection)
	Enabled Size: 2048 MB (Double-bank Connection)
	Error Status: OK
```



BTW, it also says:


```
Handle 0x0001, DMI type 1, 27 bytes
System Information
	Manufacturer: LENOVO
	Product Name: 8744J2U
	Version: ThinkPad T60p

```

Thanks

---

### Post by fishtoprecords on 2010-07-27
> **cascade9 said:**
> What model Lenovo? IIRC, there were a few chipsets that were advertised as 'supporting 4GB', and yeah, they work with 4GB, but they can never see more than 3GB.

Manufacturer: LENOVO
	Product Name: 8744J2U
	Version: ThinkPad T60p

Actually, the old documentation never talked about more than 2GB, I bet because back then, 1GB sticks was all that you could have. When I got the memory bump, I checked explicitly with Crucial to make sure that the two sticks would "work" because the documentation from Lenovo was, er, unclear. Since the RAM was not expensive, I'm happy with the performance bump that I got going from 2 to 3.

But like everyone, if I can get a bit more speed, I'll take it.

So far, the PAE kernel has had zero visible impact. Not slower, not faster.

---

### Post by cascade9 on 2010-07-27
The ThinkPad T60p (8744J2U) uses the Intel 945GM chipset. 

From a quick search, it looks like there is no definitive answer as to if the 945GM actually does support 3GB, r 4GB (I've seen stuf about how the I945GM was limited to limited to 2^32 addressable points on the memory bus, and others saying that the 'missing' 1GB is 'reserved for system use', etc..) 

BTW, when I was checking for the chipset used, I did find this- 

> 2 GB (1 GB x 1) / 3 GB (max)[http://www.superwarehouse.com/Lenovo_ThinkPad_T60p_8744_Notebook/8744J2U/ps/1495679](http://www.superwarehouse.com/Lenovo_ThinkPad_T60p_8744_Notebook/8744J2U/ps/1495679)

hat could be someone who was trying to stop poor 32bit windows users from having freakout about 'where is my other 1GB', or it could just be that the person who wrote up those specs saw a link, or knew something I dont. 

Sorry if that doesnt help much, I'll have a poke around later and see if I can find something a little more concrete ;)

---

### Post by davidmohammed on 2010-07-28
from the sudo dmidecode - it makes clear that officially the bios only supports a max of 2GB.  Given that you've managed to push it to 3GB - take that as a bonus!

You might want to see if there is a bios upgrade for your laptop.  Otherwise, 2 to 3Gb is your limit.

---

### Post by fishtoprecords on 2010-07-29
> **davidmohammed said:**
> from the sudo dmidecode - it makes clear that officially the bios only supports a max of 2GB.  Given that you've managed to push it to 3GB - take that as a bonus!


Thanks, I'll declare that its a bonus

---

