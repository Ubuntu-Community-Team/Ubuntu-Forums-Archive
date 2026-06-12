---
title: "Error when trying to install Win 7 x64 - Virtual Box"
date: 2010-08-16
forum: Installation &amp; Upgrades
---

### Post by elwayisgod on 2010-08-16
Hi,

New here and I downloaded and installed VirtualBox x64 and installed it.  Created my first image and now am trying to install my Win 7 Ultimat x64 on it via the disk.. However I get this error:

Attempting to load 64bit application, however this CPU is not compatible with 64 bit mode.  

Why would I be getting that.  I have a 64 bit i7 processor and my ubuntu is x64_AMD.....

stumped....

---

### Post by scrooge_74 on 2010-08-16
I had a similar message today trying to install Ubuntu Studio on a 64bit host.

Havent done much to fix it, only thing I did was in a terminal I did 

uname -a 

System says x86_64 GNU/Linux

so Im not sure what is going on either

You should check virtualbox documentation

---

### Post by elwayisgod on 2010-08-16
Seen this...

Please ensure that you have enabled VT-x/AMD-V properly in the BIOS of your host computer.

Where exactly do I do this?  Boot up my laptop and just enter BIOS?  Is it fairly simple?  Or does the Ubuntu have it's own BIOS?  Gray area for me..

---

### Post by elwayisgod on 2010-08-16
Went to Bios went laptop was booting and enabled the VT setting and it worked and I was able to install Win 7 x64.... Solved.. Just learning this Linux stuff... Now to try and get Adobe Flash :)

---

