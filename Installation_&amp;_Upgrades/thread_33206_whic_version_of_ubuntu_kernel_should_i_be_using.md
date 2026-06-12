---
title: "whic version of ubuntu kernel should i be using?"
date: 2005-05-09
forum: Installation &amp; Upgrades
---

### Post by jzietman on 2005-05-09
so i'm gonna install ubuntu soon, but browsing these forums i've seen tons of different versions of ubuntu kernels that people have.  

i am sure i don't want to use the 64-bit version, as there are too many complications and compatibility problems with common programs.  

then there are also the k7, 386, 686, etc. kernels.  for my system, which should i be using, and which ubuntu iso should i dl off of ubuntulinux.org to make my install cd with?

:newbie:

---

### Post by Xian on 2005-05-09
[QUOTE=jzietman]then there are also the k7, 386, 686, etc. kernels.  for my system, which should i be using, and which ubuntu iso should i dl off of ubuntulinux.org to make my install cd with?[/QUOTE]
What processor do you have on your system? Pentium-4, AthlonXP, etc. ?

---

### Post by jzietman on 2005-05-10
oh, sorry, i forgot i didn't have a sig with my comp info on this forum.

i have an a64 3000+, an abit kv8-pro, 512 mb ram. if more info is necessary for this, i'll be glad to provide.

---

### Post by BAshworth on 2005-05-10
in a console, type 'uname -a'  that will tell you which version of the kernel you are currently running, and what type of kernel your processor can handle.

As an example, here's mine..

Linux ####### 2.6.10-5-686 #1 Tue Apr 5 12:27:02 UTC 2005 i686 GNU/Linux

The part before the date lists your computer's name (hence the blocks), and the part after the date lists your processor type.  In this case, I have an i686 processor, so I installed the 686 kernel.

---

### Post by DJ_Max on 2005-05-10
These guys here can probably help you better, as to which kernel to use.
[http://ubuntuforums.org/forumdisplay.php?f=60](http://ubuntuforums.org/forumdisplay.php?f=60)

---

### Post by jzietman on 2005-05-10
well, i don't have it installed yet (waiting for weekend), but what kernel would isntall by default? what are the differences between the 386, 686, k7, k8, and generic kernels?

---

### Post by tread on 2005-05-10
Well, the 386 kernel would mostly work on any x86 compatible processor, the 686 kernel would use optimizations available on a pentium 4, the amd 64 kernel would be run in 64 bit mode etc.

---

### Post by jzietman on 2005-05-10
my proc is an a64, but i would like to run the 32-bit version of ubuntu. when i install from the 386 iso (the iso you dl for x86 32-bit) will it install 2.6.10-5-k8?  that would be optimum for my cpu, wouldn't it?

---

### Post by AndEat on 2005-05-10
[QUOTE=BAshworth]in a console, type 'uname -a'  that will tell you which version of the kernel you are currently running, and what type of kernel your processor can handle.

As and example, here's mine..

Linux ####### 2.6.10-5-686 #1 Tue Apr 5 12:27:02 UTC 2005 i686 GNU/Linux

The part before the date lists your computer's name (hence the blocks), and the part after the date lists your processor type.  In this case, I have an i686 processor, so I installed the 686 kernel.[/QUOTE]

New to this OS, I have been looking around the forums for as much info as possible.

I ran uname -a and here is what I got:

Linux acesdfgrtertfdszdgdfvbnbv-XXXXX 2.6.10-5-386 #1 Tue Apr 5 12:12:40 UTC 2005 i686.....it would seem I'm not optimized for my processor and I have noticed some...less than optimal performance. I couldn't find the 686 kernel and I don't remember the option, or I don't know enough yet to find the kernel.

 Is this something I can do myself at a basic level or is this a more advanced option  I overlooked on install?

thanks

---

### Post by bored2k on 2005-05-10
[QUOTE=AndEat]New to this OS, I have been looking around the forums for as much info as possible.

I ran uname -a and here is what I got:

Linux acesdfgrtertfdszdgdfvbnbv-XXXXX 2.6.10-5-386 #1 Tue Apr 5 12:12:40 UTC 2005 i686.....it would seem I'm not optimized for my processor and I have noticed some...less than optimal performance. I couldn't find the 686 kernel and I don't remember the option, or I don't know enough yet to find the kernel.

 Is this something I can do myself at a basic level or is this a more advanced option  I overlooked on install?

thanks[/QUOTE]
 sudo apt-get install linux-686

---

### Post by BAshworth on 2005-05-11
[QUOTE=jzietman]my proc is an a64, but i would like to run the 32-bit version of ubuntu. when i install from the 386 iso (the iso you dl for x86 32-bit) will it install 2.6.10-5-k8?  that would be optimum for my cpu, wouldn't it?[/QUOTE]

It will install the 386 kernel by default.  Most distros do the initial install using only one version of the kernel.  You can update your kernel to one of the other version either through Synaptic, under Base System (restricted), or via the terminal, as bored2k posted.

---

### Post by AndEat on 2005-05-14
thanks. I figured it out after hastily posting. easy. :)

---

### Post by DutchLau on 2005-05-14
@ jzietman

I'm doing the same thing as you, for the moment. Just download the x86 CD and install Ubuntu that way. Once you've installed Ubuntu, open up a terminal and type in " sudo apt-get install linux-686 " to get the 686 kernel. It will do the rest automatically. Reboot and choose the 686 kernel from the Grub menu.

Good Luck,

DutchLau

---

### Post by jzietman on 2005-05-15
and 686 is the correct version for a64 cpus?

---

### Post by DutchLau on 2005-05-15
@ jzietman

All you do is install the x86 Ubuntu and if you have more than 900MB Ram, then you install the i686 kernel. Even without that much Ram you might experience a small boost in performance.

Good luck,

DutchLau

---

### Post by jzietman on 2005-05-15
i only have 512 megs.... will it be ok?

---

### Post by DutchLau on 2005-05-15
Perhaps, you can just keep the i386 kernel.

---

### Post by jzietman on 2005-05-15
i know i'm being persistent, but what exactly are the k7 and k8 kernels?

---

### Post by DutchLau on 2005-05-15
K7 is the AMD XP/Athlon etc. kernel. The K8 is the AMD 64 ( I believe ). The K7 kernel was actually really bad on my AMD64 and it was really choppy. Maybe that's just a problem I had but see what you do. i686 is amazingly fast for me. Should be for you also, I guess.

---

### Post by jzietman on 2005-05-15
why would 686 need 1 gig of ram to shine whereas 386 wouldn't?

---

### Post by DutchLau on 2005-05-16
LoL, that's not it my friend.

The i386 kernel only supports up to 900 mb of ram, the i686 kernel supports 900+ :D

---

### Post by jzietman on 2005-05-16
ahh, i see. well, i've only 512, so it shouldn't matter

---

### Post by DutchLau on 2005-05-16
Exactly, I`m switching over to Hoary 64 soon (well I'm going to try it out that is  :grin: ) I installed it already, and I can tell you the boot up process is alot faster, so the programs will undoubtedly also be much faster.

The only thing I'm annoyed about is the lack of compatibility with codecs, mainly win codecs. This it the only thing restricting me from stepping over just now. See you in the forums and have fun playing with Linux!

---

### Post by pdk001 on 2005-05-16
why do i have a problem to multiple booting when i update 386 to 686 kenel?

---

### Post by bored2k on 2005-05-16
[QUOTE=pdk001]why do i have a problem to multiple booting when i update 386 to 686 kenel?[/QUOTE]
 Can you be more verbose on that ?

---

### Post by DutchLau on 2005-05-16
Did you do "sudo apt-get install linux-686" ?

Press esc at GRUB and make sure to check the 686 kernel

Don't really know what you're doing wrong by your limited response tho  :-?

---

### Post by jzietman on 2005-05-16
[QUOTE=DutchLau]Exactly, I`m switching over to Hoary 64 soon (well I'm going to try it out that is  :grin: ) I installed it already, and I can tell you the boot up process is alot faster, so the programs will undoubtedly also be much faster.

The only thing I'm annoyed about is the lack of compatibility with codecs, mainly win codecs. This it the only thing restricting me from stepping over just now. See you in the forums and have fun playing with Linux![/QUOTE]

yeah, codecs and the fact that it's already difficult to get sb live! cards working on the 32-bit version are keeping me from using the 64-bit version.

---

### Post by DutchLau on 2005-05-16
Your mobo shoud be fine for sound though. I couldn't possibly see any reason why I'd get a soundcard with my A8V. Doesn't the K8V have onboard sound?

---

### Post by jzietman on 2005-05-16
it does, but it doesn't sound too good. also it refuses to use any irq but the one my onboard nic uses, so whenever i do something internet intensive, like limewire or online gaming, the sound crackles. plus the sound card sounds so much better, especially with the nice headphones i'll be getting soon (i tested my friend's pair, and there's a noticeable diff between onboard sound and the sb live).

---

### Post by DutchLau on 2005-05-16
I'll take your word for it  :razz:  My A8V - Deluxe has surround sound built in, and it worked "out of the box"! Amazing sound quality, except that my speakers blow (300w generic craps - but I have a headset!). I can play many many sounds at the same time and run America's Army and Seti@Home without any crackling  so I'm a happy camper :) Just make sure to get Alsa set up properly  ;-) 

Ciao

---

