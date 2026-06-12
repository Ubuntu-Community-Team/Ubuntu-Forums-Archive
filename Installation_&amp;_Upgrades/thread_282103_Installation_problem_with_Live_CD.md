---
title: "Installation problem with Live CD"
date: 2006-10-22
forum: Installation &amp; Upgrades
---

### Post by deviantcynic on 2006-10-22
I ordered a Ubuntu cd from shipit, and got it. But during the installation, the CD takes atleast half an hour, to go to step 2 of Installation, and then it all becomes, sort of mess...
I have 256 mb ddr Kingston ram, 40 gb hd SATA Seagate, and Intel Celeron D 2.4 ghz processor.

---

### Post by Tasadduq khan on 2006-10-22
Hello,

Today I Installed ubuntu as well without any problem. Though having some other type of problems. 
step 2 of installation ? DO you mean when you clicked on install and it asked for 6 steps before starting installation?

---

### Post by deviantcynic on 2006-10-22
Yes, I surely meant that. It is when the Installer asks, 'Where are you?' and then it takes forever to load that page! 

And in between, your name suggests you are a Pakistani, I am one too. I am from Karachi, what abt you?

---

### Post by Tasadduq khan on 2006-10-22
LOL

Well I am not sure what the problem is (Coz I am noob too :) ) But you shouldn't face this problem. I have Ubuntu installed on my slow PC (As compared to yours)

yeh I am from Islamabad Pakistan. (nice to see that pakistanis are tending towards linux too ;) ).

---

### Post by scubacuda on 2006-10-22
I got the same problem.

I think your solution is solved by getting the alternate install CD.

[http://ubuntu-releases.cs.umn.edu//6.06/ubuntu-6.06.1-alternate-i386.iso](http://ubuntu-releases.cs.umn.edu//6.06/ubuntu-6.06.1-alternate-i386.iso)

---

### Post by deviantcynic on 2006-10-22
Can I order this CD from somewhere? As I cannot download such large  files! A lil' help would always be appreciated. And yes, if anyone needs more specifications, my motherboard is Intel D845GVSR, has it got something to do with it?

---

### Post by deviantcynic on 2006-10-22
And yes, what is the difference b/w alternate CD and the normal one? ](*,)

---

### Post by deviantcynic on 2006-10-22
and finally my chipset is Intel 845GV Chipset from Intel for D845GVSR Motherboard from Intel. :) Please help!

---

### Post by deviantcynic on 2006-10-23
I tried Instlux but it too sends me to GRUB, and I dont know what in the name of sweet heavens is it... This is really tiring.... I am about to give up on Ubuntu if I dont find any possible solution to it! ](*,)

---

### Post by darrelljon on 2006-10-23
> **deviantcynic said:**
> Can I order this CD from somewhere? As I cannot download such large  files! A lil' help would always be appreciated. And yes, if anyone needs more specifications, my motherboard is Intel D845GVSR, has it got something to do with it?If like me, you're on dial-up, the only option to obtain the alternate CD, is to order from one of the many people online who will burn Linux CDs for you for about £1.99.

---

### Post by Kateikyoushi on 2006-10-23
You could try this.

Boot from the cd at menu press F6 then start with these options

Boot: linux noapic
Boot: linux pci=irqroute
Boot: linux pci=noacpi
Boot: linux acpi=off
Boot: linux pci=acpi
Boot: linux nolapic
Boot: linux framebuffer=false
Boot: linux irqpoll

---

### Post by deviantcynic on 2006-10-23
When I press F6 key, a text line with a lot of stuff in it opens.... should I add your lines to it? or should I erase it and then and then add the lines? Sorry, I am a real NooB

---

### Post by Kateikyoushi on 2006-10-23
After the live cd boots up and you see the menu then press F6 and enter one line to boot the cd with that option. Use one line at a time to see if it works or not. I think the first one might help, but depends on your exact configuration.

---

### Post by deviantcynic on 2006-10-23
Thank you.. I'll try these out, what exactly is the function of these commands? can u please explain? :) :)

---

### Post by deviantcynic on 2006-10-24
:( It's not working this way either! HELP! I am downloading an alternate cd but can someone tell me how to install it without burning the image on cd as I dont have a CD Burner! I am stuck! And really, I was expecting better from Ubuntu! 

p.s: I tried Instlux but it dosent help either! and I dont know how to use GRUB! ](*,) ](*,) ](*,) ](*,) ](*,)

---

### Post by Kateikyoushi on 2006-10-24
Those commands should disable some componets in your system which might not be supported from the live cd or require tweaking.
If you have a thumbdrive you could boot from that.

---

### Post by deviantcynic on 2006-10-24
My thumbdrive is 256mb only. Anyways, how do we boot from thumbdrive? My bios dosent offer anything of that sort! :confused:

---

### Post by deviantcynic on 2006-10-24
Can you tell a specific boot command from those you gave above, there are loads of them and none of these seem to work... They all seem to load the same way they always do - NO CHANGE! Would there be any visible change from these commands and can u be a bit more specific about them. My hardware specs might help. 
D845GVSR Intel Motherboard. 845GV Intel Chipset. Intel Celeron D 2.4 Ghz Processor. 40 GB Sata Seagate Harddisk, and I would only be keeping Ubuntu on it. 256 mb ddr Kingston RAM. That's all...
P-U-H-L-E-S-E --- P-U-H-L-E-S-E --- HELP!

---

### Post by deviantcynic on 2006-10-25
Woah Boy! I quit on Ubuntu!

---

