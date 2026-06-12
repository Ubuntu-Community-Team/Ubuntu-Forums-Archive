---
title: "Imstallation ERROR:[ 0.628000] PCI: Cannot allocate resource region 1 of device 0000:"
date: 2007-10-19
forum: Installation &amp; Upgrades
---

### Post by mahacita on 2007-10-19
I'd like to Install to my PC. But I got the eroor message like this.

[ 0.628000] PCI: Cannot allocate resource region 1 of device 0000:00:14.0

And Nothing happens. I tried to install ubuntu 7.10, 7.04 and 6.xx but the result was always same. I'm using brisbane 3600+, jetway M2A692-GDG MotherBoard, 7600GS VGA.

Please Help!!

---

### Post by genbie on 2007-10-19
I have the same error when trying to boot kernel 2.6-22-14-generic. Kernel 2.6-20 works fine though.  Both are with my new Ubuntu Gutsy upgrade from Feisty. I have an Acer computer with ATI on-board graphics. Searching the internet, I found many people experiencing the same issue but it was not fatal (i.e. they were able to complete the boot process). But in our case it appears to be a critical error unfortunately :(

---

### Post by erv2 on 2007-10-20
i am having a simular problem. but i m using amd64 cpu and the 7600GS display card.

how to change the kernel exactly? i m very new to linux, it'd be much better that you can be as specific as you can.

---

### Post by h_jodat on 2007-10-21
I get the following messages when trying to boot the Ubuntu 7.10 installation CD:

PCI: Cannot allocate resource region 1 of device 0000:00:14.0

At this point the system is locked up.

Does anyone have any idea what is happening or how I can fix?

---

### Post by elnerdo on 2007-10-21
I too have been having this mysterious problem.  I'm able to run the Live CD fine, and while I had the same problem with Feisty, feisty ran fine as well.  It's only now that I have Gutsy that it doesn't work.  After I get this error (Which repeats eight times) the computer screen turns black and nothing happens.

---

### Post by elnerdo on 2007-10-22
To clarify and bump, my error says:

PCI: Cannot allocate resource region 1 of device 0000:00:14.0
PCI: Cannot allocate resource region 2 of device 0000:00:14.0
PCI: Cannot allocate resource region 3 of device 0000:00:14.0
PCI: Cannot allocate resource region 4 of device 0000:00:14.0
PCI: Cannot allocate resource region 5 of device 0000:00:14.0
PCI: Cannot allocate resource region 6 of device 0000:00:14.0
PCI: Cannot allocate resource region 7 of device 0000:00:14.0
PCI: Cannot allocate resource region 8 of device 0000:00:14.0

But these messages only stay on the screen for about one second.  After that, the screen goes completely black, and I need to restart my laptop.  Before this error is shown, it just says "Starting up..."

If I boot into recovery mode, it seems to work, but I don't know enough about Linux and Ubuntu to actually do anything from the console.

---

### Post by elnerdo on 2007-10-22
1.  I just realized that the original question was about installation and I'm talking about booting (Sorry!)

2. I get the same message when I run the live cd, but the live cd works fine.

---

### Post by opm8 on 2007-10-22
Does this bug report help? (scroll to the bottom)

[https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.22/+bug/107516](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.22/+bug/107516)

---

### Post by elnerdo on 2007-10-22
No, it didn't help my problem.  I have been trying to work things out by experimenting with recovery mode.  I just found out that you can run the GUI in recovery mode with "startx," so recovery mode works fine, I still can't boot normally, though.

---

### Post by outlaw686 on 2007-10-23
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.22/+bug/144245](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.22/+bug/144245) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
Hop in the the terminal and type uname -r

				I had the same problem I found it was only when I booted the 2.6.22.14-386 version of the  linux kernel that I think the update installer snuck onto my system. When I booted into the generic version by hitting the esc button when grub pops up. I still got the same pci allocation error, But everything magically seemed to work. After that I just booted into the generic kernel again through grub and removed the 386 kernel from my system using the synaptic package manager.

If you like command line stuff, I'm sure "apt-get remove kernel-image-2.6.22-14-386" would work. That providing that you already have the generic kernel on your system. 

If you don't have the generic on your system for some reason, "apt-get install kernel-image 2.6.22-14-generic" or install it from the synaptic package manager. 

 I'm not to particularly worried about the allocation error as "lspci -v" revealed it's for my internal graphics card which I don't use anyway.

hope It's just a bug in the 386 kernel that gets fixed soon. hope this helps guys (and gals).

---

### Post by elnerdo on 2007-10-28
Crap.  I got really excited when I read your post which had a possible answer, but it turns out that I'm already running the generic kernel (At least in recovery mode, I am).  

You mentioned that for you, the error was with your internal graphics.  On my laptop, I only have the internal graphics, and a graphics error would explain why I can't see anything after that point.  In that case, do you have any idea how to fix it?

---

### Post by farbinfarkt on 2007-11-21
I got the same problem: Installation works fine but when I try to start the fresh system, I see these messages and the screen turns black.
I also got an Acer Notebook with ATI graphics.

Gutsy did work on this system after I upgraded from feisty but as the upgrade had reported errors related to not being able to remove some packages I thought Id do a complete reinstall of Gutsy... then it never worked again

---

### Post by elnerdo on 2007-11-21
I solved my problem.  I doubt that very many other people have this problem, but I realized that my processor (Sempron 3500+) is actually a 64 bit processor, and I had originally installed the 32 bit version.  When I reinstalled with the 64 bit version, it worked fine.

---

### Post by mikewhatever on 2007-11-21
Hey guys, don't get too excited. That same bug has been around for quite some time revealing itself in different kernels and different distros. There are several entries already on launchpad.net and here on the forums. I kind of doubt it will get fixed soon.

---

### Post by farbinfarkt on 2007-11-22
Ok, I somewhat fixed it for me.

My system DID boot, only without displaying anything. Booting stopped at a certain point because of a broken partition. After removing that partition from fstab I could boot completely. I still dont see anything durign the boot process but as soon as X loads, my display shows it and everything is ok.

So the problem was not that the system did not boot, but only that it does not display anything while booting.

---

### Post by tomcat1_12 on 2007-11-22
Well, I have similar problem with my acer travelmate 4103wlci laptop, after showing the errors, the screen just goes blank, and it won't boot at all, BUT if I press ctrl + alt + f1 (which open the terminal I think), it'll continue to boot normally!!!, so you may try it to see if it works for you

---

### Post by genbie on 2007-12-07
Anyone knows how to fix this problem please? I am sure there are others also using Acer computers who might know how to do it! Any chance the developers have a look at it please? It has taken almost two months in my case! 

Thanks in advance.

---

### Post by genbie on 2007-12-09
Any help anyone?

Thanks!

---

### Post by genbie on 2007-12-29
Surely I am not the only one with this problem?!

---

