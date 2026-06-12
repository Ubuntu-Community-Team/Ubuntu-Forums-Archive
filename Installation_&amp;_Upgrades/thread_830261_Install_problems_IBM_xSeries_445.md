---
title: "Install problems IBM xSeries 445"
date: 2008-06-15
forum: Installation &amp; Upgrades
---

### Post by RunsWithScissors on 2008-06-15
I have a IBM eServer xSeries 445 with is a 8 CPU Rack-mount server I'm trying to install Ubuntu on it. 8.04LTS. I have tried the regular and the ALT CDs and both give the same result with I tell it to install or and thing shortly after doing the unco9mpressing the kernel gauge thing it goes to a black screen with a white cursor in the upper left hand corner and will stay there.

does anyone know that this could be? Is there some way to make it get past this? Currently the systems has Fedora 8 on it but I'm not a big fan of fedora.

---

### Post by wpshooter on 2008-06-15
Have you tried starting/installing in safe graphics mode ?

---

### Post by RunsWithScissors on 2008-06-15
isn't that what the alternative CD is?

---

### Post by wpshooter on 2008-06-16
> **RunsWithScissors said:**
> isn't that what the alternative CD is?

I think there is a safe graphic mode on both the LIVE and the ALTERNATE CDs.

I generally always attempt to install from the ALTERNATE.

---

### Post by RunsWithScissors on 2008-06-16
yeah I tried both and both do the same thing. It is definitely and Ubuntu Issues as I have also tried Fedora 8 and 9 and both get past that point. it is right after the init image is uncompressed and gets ready to start the setup. it just hangs.  On fedora it does the exact same thing and then goes to the screen with the cursor in the upper left for about 2-3 seconds and then starts the fedora install wizard. But Ubuntu just freezes when it gets tot he screen with the blinking cursor I have tried just walking away and leaving it for over an hour it is defiantly hung.

---

### Post by Dunkeltron on 2008-09-04
*RunsWithScissors*, do you have given up?

I want to buy an old Xseries 445 and install Ubuntu 8.04 on it.

In Recovery Mode you should see much more than a blank screen. Sometimes on Terminal 4 the output is hidden.

Or try modifying some Boot Parameters: delete the "silent" and the "splash"; Powermanagement sometimes makes problems (acpi?).

---

### Post by Alex53 on 2008-09-04
I have a similar problem with an IBM xSeries 335, the monitor displays 'out of range'. Safe graphics mode didn't make any difference. :/

---

### Post by RunsWithScissors on 2008-09-04
yeah I gave up. using Fedora 8 instead. I want to figure out how to get PAE working with it though.

gonna load it full of ram and then put a bunch of VM Ware servers on it.

Fedora 8 was a total breeze to install though. The way that ubuntu usually is on the desktop. Ubuntu I have found just is no good for servers. at least all of the ones I have tried installing it on.

---

### Post by Alex53 on 2008-09-05
Yeah, I installed using the alternate CD, went through the installation because it's text based, but then had the same problem as soon as it tried to boot up. 

So I am also heading for the Fedora CDs as soon as I click on submit I'm afraid.

---

### Post by okonita on 2008-10-18
I have just bought a bare-bones used xSeries 445 sever and getting ready to put it to use. Problem is I am not a hardware person and I don't know what other hardware/software accessories that I must have or may need to get the box to work. So, some beginer questions: Can I use a 64-bit OS on this box? What OSs would you recommend? Can I put virtualization (VMware?) software on this box? 
I see in this thread that some had problem installing Ubuntu. Anyone successfully installed Ubuntu on a xSeries 445? Can you share how you overcame the problem you had?

This server that I have comes with no OS,HDD,mouse,monitor and things like that. I plan to use this server at home. So any advice I can get to help me work this server will be highly appreciated.

Thanks in advance for all the recommendations, suggestions and write-ins!

---

### Post by Alex53 on 2008-10-21
Woops, sorry I didn't follow up on this thread. The problem had nothing to do with the server. It was the 2 different Asus monitors I tried that just dont work with Ubuntu, or with Fedora for that matter. 

Once I tried with a different (LG) monitor I installed Ubuntu no problems and its already become our production flavour of Linux for web/ftp servers over Fedora.

---

### Post by Mizzou_Engineer on 2009-04-13
> **okonita said:**
> I have just bought a bare-bones used xSeries 445 sever and getting ready to put it to use. Problem is I am not a hardware person and I don't know what other hardware/software accessories that I must have or may need to get the box to work. So, some beginer questions: Can I use a 64-bit OS on this box? What OSs would you recommend? Can I put virtualization (VMware?) software on this box? 
I see in this thread that some had problem installing Ubuntu. Anyone successfully installed Ubuntu on a xSeries 445? Can you share how you overcame the problem you had?

This server that I have comes with no OS,HDD,mouse,monitor and things like that. I plan to use this server at home. So any advice I can get to help me work this server will be highly appreciated.

Thanks in advance for all the recommendations, suggestions and write-ins!


I think I may be able to help:

1. The CPUs in the 445 are 32-bit only, so you must use the 32-bit OS. I believe the linux-image-server kernel has PAE enabled so you can see more than 3.x GB RAM while only running a 32-bit OS.

2. Almost any 32-bit Linux will work on that machine. I would recommend Ubuntu Sever Edition if you do not want a GUI and the standard desktop install if you do. Debian is also an excellent OS as well and is what Ubuntu is based from.

3. You can run VMware or any other virtualization software except for Xen on that machine, as long as you do not tell the virtualization software to use CPU VM extensions such as SVM or VT. The Xeon MPs in that unit do not have that capability.

4. I don't have an xSeries 445, so I can't tell you if you'll have trouble installing Ubuntu or any other OS. However, I may very well be getting an 8-way 2.7 GHz 445 in a couple of days, so I may be able to tell you.

One question: is the xSeriex 445 very loud? I want to know because I will order some quieter fans if it is very noisy.

---

