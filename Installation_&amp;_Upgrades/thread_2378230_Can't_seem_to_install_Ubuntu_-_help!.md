---
title: "Can't seem to install Ubuntu - help!"
date: 2017-11-21
forum: Installation &amp; Upgrades
---

### Post by furious-bruce on 2017-11-21
Forgive me if this has already been posted / answered in another forum, I'm a first timer. 

I'm trying to set up an old travel laptop of mine for my son so we can learn together how to make a Minecraft Server and mod it - I thought I'd give him a kickstart in life and get him to learn how to use Ubuntu.

I work in IT, but I'm in Service Management so my knowledge in this field (my knowledge in every field...) is limited. 

I first ran in to trouble when the EPC wouldn't boot off a USB - so I had to do the workaround of burning uber-v2-install on to a DVD and booting off that, and using the USB along with it. I thought I was doing some really good computering, but....

I've attempted to install Ubermix, and I was confronted with the error '*This kernel requires an x86-64 CPU, but only detected an i686 CPU. Unable to boot – please use a kernel appropriate for your CPU*'

Thinking that this is due to the EPC being 32 bit and Ubermix being 64, I got the 32bit lite version of Ubermix. I still got the same result. 

I've now tried ubuntu-16.04.3-desktop-i386 - and it's still giving me the same error message. 

The laptop itself is around 10 years old. 

**System Overview. **
ASUS Eee PC ACPI BIOS Revision 1206
Core Version:1206 
Build Date: 10/07/08
EC Firmware Version:EPCB-017

**Processor**
Type: Intel (R) Atom CPU N270 @1.60ghz
Speed: 1600MHz
Count: 1

**System Memory**
Installed Size: 2048MB.

There's no option in the BIOS to enable Intel VT, which is the workaround that Google suggested. 

Is there a version specific to this laptop that I should be using? Have you guys got any advice or suggestions on how I can get us up and running?

Thank you in advance - my 8 year old will get such a kick out of all your help.

---

### Post by slickymaster on 2017-11-21
Thread moved to **Installation & Upgrades** for a better fit

---

### Post by jaweewo on 2017-11-21
Hi, Im new in Ubuntu and I think your problem is that for example in Ubuntu 16.04 it's hard to use an old computer, but maybe try with some Debian, at 32 bits --> i386 kernel and 64 bits --> Amdx86 kernel. 
But maybe as i said, i am new so i recommend you to wait for some real answer ;D Good luck

---

### Post by yancek on 2017-11-21
There are specific instructions on the Ubermix page if that is what you are trying to install?  Link below.  A new Ubuntu might work on this machine but you may be better off with something like Lubuntu.

[http://www.ubermix.org/download.html](http://www.ubermix.org/download.html)

---

### Post by mastablasta on 2017-11-22
ubuntu won't be happy on that machine. use Lubutnu as sugested or LXLE or osme other light distro.

i would also suggest (depending on financial options) that a better option might be to get a fairly recent laptop. you can get a good descent used one for 80 EUR or even less and it will run circles arround what you have. Here they sell 3 or 4 year old business laptops (better build, matt screens, pricier when new) from 200 EUR onwards along with 6m warranty. there are companies that would sell them for much less, while private owners would often give an even lower price.

even when you can get it to run, minecraft could bring a new challenge to it. the EEE was means mostly for web surfing , occasional email, and maybe some typing.

---

