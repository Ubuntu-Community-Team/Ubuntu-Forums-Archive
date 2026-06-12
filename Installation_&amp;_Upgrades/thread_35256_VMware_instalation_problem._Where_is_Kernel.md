---
title: "VMware instalation problem. Where is Kernel"
date: 2005-05-18
forum: Installation &amp; Upgrades
---

### Post by mkg on 2005-05-18
Hallo happy people,

It seems to me that I’m day worker and others want to work in the end of the day. Find with me it is important to keep going forward. For today I will go around wine for now and try to install vmware instead I mean I start to install vmware and have this massage:

Trying to find a suitable vmmon module for your running kernel

None of the pre-built vmmon modules for Vmware Workstation is suitable for your running kernel. Do you want this program to try to build …….. you need to have C compiler installed on your system ………. 

I type yes of course and than next massage:

What is location of the directory of C header files that match your running kernel? [/usr/src/linux/include] 

I hit Enter

The path “/usr/src/linux/include” is not an existing directory

After this I try to locate needed directory, but I failed.

And what now …. PLEASE HELP

---

### Post by lao_V on 2005-05-18
You need to install the linux headers which can be found in synaptic under linux-headers-`your running kernel`

Once you have this installed, you can point the vmware installation to /usr/src/linux-headers-`your running kernel`/include

---

### Post by mkg on 2005-05-18
[QUOTE=lao_V]You need to install the linux headers which can be found in synaptic under linux-headers-`your running kernel`

Once you have this installed, you can point the vmware installation to /usr/src/linux-headers-`your running kernel`/include[/QUOTE]

Prompt answer Thak you very much I getting better with you gays everyday.

Everyday in every way I going forward  :grin:

---

### Post by mkg on 2005-05-18
[QUOTE=mkg]Prompt answer Thak you very much I getting better with you gays everyday.

Everyday in every way I going forward  :grin:[/QUOTE]

I did install vmware for linux and how I did it.

First of all I open toor teminal and type:

uname -a

' you will see something like: Linux hostname 2.6.10-5-386

sudo apt-cache search headers 2.6.10-5-386

' next you what you see will be: linux-headers-2.6.10-5-386 - Linux kernel headers 2.6.10 on 386

sudo apt-get install linux-headers-2.6.10-5-386
sudo apt-get install gcc

After finiching, you are ready to install VMware according to the installation help files vmware offer. Through installation you will be asked about nerworking so if you have network and want to be connected throu VMware, please read carefully installation note, In one moment you will be asked to input IP adress and subnet mask, but I can not remember when. It was something about NAT..

Thaks to the community I managed to install something on Kubuntu 5.04 and that makes me happy   \\:D/   :grin: 

Many regards from Macedonia

Goran

---

