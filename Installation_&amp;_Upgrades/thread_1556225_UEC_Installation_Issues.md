---
title: "UEC Installation Issues"
date: 2010-08-19
forum: Installation &amp; Upgrades
---

### Post by WiseHacker on 2010-08-19
I have been at this for some time now and hopefully someone can point out what I am doing wrong.

When they bundled Ubuntu with Eucalyptus, I thought it would be great to build my own cloud.  To keep things under control, I decided to get the Package Install approach using VMware virtual machines.

Everything is fine until I get to the part with the Node Controller installation.  For reference, my Cluster Controller has two NICs: eth0 is bridged to the physical NIC and eth1 uses a HostOnly network (VMware network that exists on the server running it).

Naturally, I have my Node Controller using the HostOnly as well, the intension is to have the Node Controller access the Internet via the Cluster Controller.  This has the same effect as me using physical systems where my Cluster Controller is connected to a broadband router and my Node Controller is connected to the Cluster Controller via a cross over cable.

The problem I have is despite following the documentation to the letter (twice), I keep getting stuck when I go to update and install packages for the Node Controller.  I am able to install the base system via a ISO image but the Node Controller is not able to connect to the Internet via the Cluster Controller.

Am I missing something in the documentation?  I have been through it twice to no success and it would be great if someone could point out why my Cluster Controller is not acting as a bridge for my Node Controller.  All the other nodes (Cloud, Walrus and the Cluster) seem to have their software install and update just fine.  I have even gone ahead with the later sections (the registration of UEC components) and still no result.

This concerns me as if my Node Controller cannot get through the Cluster  Controller, how will my cloud VM instances when I later try to create  them?

I am currently using Ubuntu Server 10.04 if that helps.  I have even tried the Beginner's Guide from CSS and got stuck at the same spot again (getting the Node Controller to go through the Front End).

My thanks in advance.

---

### Post by abhijeetdesai on 2010-08-21
i am having a problem before this stage !! when i install node controller it gives me a message abt Virtualization not supported !!
did u get the same  warning msg ??

---

### Post by Old_Grey_Wolf on 2010-08-21
> **WiseHacker said:**
> I have been at this for some time now and hopefully someone can point out what I am doing wrong.

I haven't used UEC for a while; however, when I did it used KVM rather than VMware. You could play with Eucalyptus to get VMware to work but UEC used KVM. 

> **abhijeetdesai said:**
> i am having a problem before this stage !! when i install node controller it gives me a message abt Virtualization not supported !!
did u get the same  warning msg ??

Did you check your processor chip for the Virtualization extensions?

---

### Post by abhijeetdesai on 2010-08-22
i have a core i7 & virtulisation is enabled in bios !!!

---

### Post by WiseHacker on 2010-08-22
Thanks for the replies, everyone.  But as luck would have it, on my third try, the installation worked.  So I am now in the process of gathering my previous virtual machines and disecting to find out what went wrong.

While I am here though, I should clarify a few things.  When I said I was using VMware, I meant that I was creating a array of virtual machines and I was installing UEC into the virtual machines.  I was not installing natively.

@abhijeetdesai: If you are using the same approach as me, installing UEC into VMware virtual machines and not natively, then you would get that error.  The reason for this is VT extensions are used to support virtualisation software.  The software running inside the virtual machines do not see the extensions.

---

### Post by sephtin on 2010-09-27
I got it to install, but KVM requiring VT Extensions from the CPU kept me from running UEC inside VMWare.  I made a few quick (failed) attempts to get Xen running as the hypervisor instead of KVM with no joy, forcing me to re-purpose my home ESXi server to Ubuntu as well as round up some additional hardware to use as a second physical machine.  HUGE inconvenience for me, because my home Asterisk PBX as well as boxes for web/database/application servers resided within ESXi, and are down until I finish with a little side project of testing UEC as a private cloud dev. environment.  

I normally prefer Ubuntu solutions over other dists.  In this case, I had more than a few regrets...

---

### Post by pallaire on 2011-03-14
> **WiseHacker said:**
> Thanks for the replies, everyone.  But as luck would have it, on my third try, the installation worked.

Hello WiseHacker !

Did you find what went wrong on your first two installations ? 

I am having the same problems. My NC can't access the web through the CC !!! I have tried more than twice :(

I don't have this problem on 10.04, but I need to upgrade to 10.10 for other reasons ... but look likes its not possible.

---

### Post by geb1 on 2011-11-14
ive tried many times to get uec 10 4 installed on diff tyes of computers 
I got cloud installed -the first time but  not sure if it included cluster to walrus etc but I could not connect to it on port vi chrome firefox etc 
i then installed node but despite best efforts could still not connect to cluster 
I then reinstalled cluster + all except node only to have software install step and grub install fail again and again 
Not sure if it was because I had node installed 
I tried on a laptop and was told that it could not take Uec hardware error Sorry cant remember error but it had something to do with virtualisation hardware -it is an older laptop.

I then installed it on pc that had node runningf  quad pc ( on another hardrive ie i disconnect node hardrive  ) which  runs esxi 64bit no problems but once again Cloud/*Cluster*/Storage/*Walrus* fails on software install and grub steps . It cant be hardware causing this 
I have now tried three computer and all fail on software install and grub step 

Therefore I am now convinced its a software problem. Possible reasons being 

1. Use of Lvm option 
2. cant be cos node installed cos I disconnect that and tried again and it still   failed 
3. perhaps its something to do with choosing all three options Cloud/*Cluster*/Storage/*Walrus*  i tried only cloud option but this also  failed so it cant be this 
4. perhaps its something to do with IP range I tried other closer ranges that I scanned as being available - no go 
5. perhaps the cloud ip must be outside range I tride this - still no go still software and grub step fail 
6. I checked bios but on the working  Esxi pc running 64 bit -nothing in bios evens mentions  a virtualisation switch still no go 

I just cant recall if I had selected all three options on the original pc Cloud/*Cluster*/Storage/[I]Walrus on whcih i managed to get uec installed 
I do see that the three options are selected by default so I can safely assunme that they where selected in the original install - the one that gave me Http error on port connect 

[/I]*Hope this helps those also stuggling with same problem *
[I]Basicacly Im stuck 

any ideas ?


[/I]

---

### Post by geb1 on 2011-11-14
I retied the installation without software updates thinking it may be somethoing in the update that was failing 

no go

---

