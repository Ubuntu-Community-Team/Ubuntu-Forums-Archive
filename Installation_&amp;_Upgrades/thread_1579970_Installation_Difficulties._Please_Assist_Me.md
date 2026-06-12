---
title: "Installation Difficulties. Please Assist Me?"
date: 2010-09-22
forum: Installation &amp; Upgrades
---

### Post by TheBritishEditor on 2010-09-22
Greetings everyone. I am BRAND NEW to Ubuntu and to the forum. I am completely aware that I am a noob and I don't expect to act like I know anything. I am just coming here for some help. 

I installed 10.04 using Wubi to install inside Windows. I ADORED it so I removed the program and used EasyBCD to remove it from the boot loader. Once I go into the live environment to install Ubuntu as a dual-boot system, I am forced to resize partitions manually. (I assume this is because I have multiple partitions on my computer already.) that's no big deal, as I found some tutorials on how to do this. The real problem is when I go to resize my Windows partition. There is no option at the top of the pop up window to type in the new, smaller size. I went and checked my other partitions, but the option was there on those. :confused: I've also tried to resize the partition in windows, and I am told to use chkdsk to fix "corruption" problem and then try again. So I go to chkdsk, and it says I must restore computer to earlier settings. So I go and do THAT, and it says I must do a DISK CHECK. HELP ME. :P 

Sorry this is sorta long, I'm just super aggravated at this point.

---

### Post by zvacet on 2010-09-24
What version of Windows do you use?If it is Win7 then you can resize partition with that OS.If you are not using that then download [Gparted live Cd]("http://gparted.sourceforge.net/") and resize your Win partition.Leave unallocated space.On that space you will install Ubuntu.

---

### Post by TheBritishEditor on 2010-09-24
Well, I use Win7. Like I said in the original post, I tried using the program in Windows, but it said I had a corruption problem. o_o Will GParted still work?

---

