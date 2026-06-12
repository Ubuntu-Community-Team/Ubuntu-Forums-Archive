---
title: "Feisty Fawn + Virtual PC 2007?"
date: 2007-03-04
forum: Installation &amp; Upgrades
---

### Post by war59312 on 2007-03-04
Hi,

Anyone have any luck getting Ubuntu "Feisty Fawn" 7.04 Herd 5 working in Virtual PC with Vista RTM as the host PC?

I boot up Virtual PC with the ISO image and select "Start or install Ubuntu" then I see  "Loading Linux kernel" and then I see two checksums are invalid messages and then "loading, please wait..." and then the screen just goes black forever. :(

If I instead choose "Start Ubuntu in safe graphics mode" during setup I simply seeing the same messages but it stays on that screen with a blinking cursor forever.

[[IMG]http://img339.imageshack.us/img339/4523/ouchwk9.th.jpg[/IMG]](http://img339.imageshack.us/my.php?image=ouchwk9.jpg)

Any ideas?

Thanks a lot,

Will

---

### Post by steve101101 on 2007-03-05
Im not sure about fiesty fawn but for 6.10 i know that Virtual PC 2007 (Microsoft) is annoying. You have to change the bit depth to 16 instead of 24 and the sound is always crackly even after trying to fix it. I would use VMWare Player. This is what i use for Ubuntu 6.10 and it works great. here is a site for instructions for VMWare player. 

Here is the howto for edgy
[http://www.petri.co.il/virtual_installing_ubuntu_as_virtual_machine.htm](http://www.petri.co.il/virtual_installing_ubuntu_as_virtual_machine.htm)

---

### Post by war59312 on 2007-03-05
Yeah never really liked vmware but I see there is a "new" 6.0 beta so I'll check it out...

Thanks!

---

### Post by grossie on 2007-03-18
[http://arcanecode.wordpress.com/2007/02/26/installing-ubuntu-610-on-virtual-pc-2007-step-by-step/](http://arcanecode.wordpress.com/2007/02/26/installing-ubuntu-610-on-virtual-pc-2007-step-by-step/)

This link made it pretty simple. Some of the steps are not the easiest way to get there, but it worked just fine. I am replying inside a vm running Ubuntu now. 

Early impressions are that it worked fairly well, but I need to get my sound card configured.

I do not doubt that vmware is likely a better option, but for my circumstances, this worked well.

---

### Post by SmithAtlanta on 2007-03-28
Did you ever get this working in VPC?

I can get it to come up but I have no mouse movement and maybe keyboard movement(can't tell for sure)

---

### Post by love2learn on 2007-03-29
I am trying to get Fiesty beta and virtual pc 2004 to work so if/when I get it to work I will let you know what I did

---

### Post by EmmEff on 2007-03-29
> **war59312 said:**
> Yeah never really liked vmware but I see there is a "new" 6.0 beta so I'll check it out...

What's to dislike about VMware?  VMware Server works perfectly and it's (also) free.

VPC 2004 performance is absolutely lousy compared to VMware Server.  Can't comment on VPC 2007 since I haven't bothered with it.

---

### Post by esaym on 2007-03-29
Why why why do people want to run a *LIVE* cd virtually??!?  I have come across this question many times.  From what I hear micosoft's virtual pc does not support the color mode ubuntu defaults with (does vpc only support 16bit or something??!)  Kudos to microsoft yet again.



Try using virtualbox [http://www.virtualbox.org/](http://www.virtualbox.org/) it's free and MS free.:guitar:

---

### Post by EmmEff on 2007-03-29
Who said anything about a Live CD?

---

### Post by esaym on 2007-03-29
> **EmmEff said:**
> Who said anything about a Live CD?

Oh good point.  I still don't see why one would want to run windows and have linux virtually.  It should be the other way around:rolleyes:

---

### Post by EmmEff on 2007-03-29
Some people have to, man...  better running Linux virtually than not at all, I guess.

I'm pretty much OS agnostic.  I run Linux virtually on Windows or OS X and sometimes natively on Linux.

---

### Post by AusIV4 on 2007-03-29
> **esaym said:**
> Why why why do people want to run a *LIVE* cd virtually??!?  I have come across this question many times.  From what I hear micosoft's virtual pc does not support the color mode ubuntu defaults with (does vpc only support 16bit or something??!)  Kudos to microsoft yet again.
I've used LiveCD ISO's with VMs (in VMware) and found that they run about as quickly as if they were installed on the VM.
> Try using virtualbox [http://www.virtualbox.org/](http://www.virtualbox.org/) it's free and MS free.:guitar:
I've tried VirtualBox, and it seemed a bit more sluggish than VMware. The second time it crashed inexplicably, I went back to VMWare.

Just my 2 cents.

---

### Post by EmmEff on 2007-03-29
Haven't yet tried VirtualBox myself either, but VMware works consistently well so I'll stick with it...  Xen shows promise too, but I don't have VT-enabled hardware so I can't run unpatched OSes.

---

### Post by paulexander on 2007-03-30
I had an interesting experience with 6.10 and Virtual PC 2007 that might help some of you.

I first ran into the usual problem with the color depth. Thanks to the posts, that was relatively easily fixed. (Safe Graphics mode, ctrl + alt +F1, edit /etc/X11/xorg.conf, etc..)

The second problem drove me absolutely batty. 

I created a fixed size 6.5GB virtual disk, with the hopes of having one 5.5 GB ext3 partition and a 1GB Swap partition. That's what worked for me before on Virtual PC 2004. 

Every time I would try to partition the virtual disk, it would fail. This happened both automatically with the installer, and manually using Gparted (which is what the installer uses on the live CD). No matter what I did, I could not format any partition to take a linux-swap FS type. I tried resizing the swap partition to leave a little space before and/or after the end of the disk; I tried formatting it with ext2 first, and then tried to convert it to Linux-swap. Nothing. I also had problems creating and formatting the first partition to format with ext3. This was intermittent; sometimes it worked, most times is did not.

I looked for MS updates on the application, recreated the virtual disk file on the machine, even tried it on another PC. Each time, the partition job would fail on my virtual Disk.

I finally thought to boot to my Knoppix CD to create the partitions manually. Instead of running Gparted, I used QTparted, which finally created the partitions just fine. I then rebooted back to the Ubuntu 6.10 ISO image, and the install completed just fine, so long as I did not let the installer automatically re-do my virtual disk (the third option down, when you are prompted to choose how to partition your disk). 

I did have another annoying little issue with using the newest Knoppix (5.1.1) though - my mouse would not work. Knoppix 5.0 worked just fine.

So, if anyone has issues partitioning their virtual disks, try QTParted instead.

Hope that helps

---

### Post by sabmann on 2007-04-21
Ik got feisty fawn up and running on virtual pc 2007. I use this [article]("http://arcanecode.wordpress.com/2007/02/26/installing-ubuntu-610-on-virtual-pc-2007-step-by-step/")...
Everything worked except the mouse. I'm going to try vmware player. Specs:

Dell Dimension 9200
Vista Home Premium
Intel Viiv E6600

---

### Post by hinsdale on 2007-04-21
> **sabmann said:**
> Ik got feisty fawn up and running on virtual pc 2007. I use this [article]("http://arcanecode.wordpress.com/2007/02/26/installing-ubuntu-610-on-virtual-pc-2007-step-by-step/")...
Everything worked except the mouse. I'm going to try vmware player.

I upgraded my 6.10 VPC 2007 virtual image to 7.04 this morning via Synaptic and had the same result -- everything runs except for the mouse.  I can get to a text entry box through the Alt+F2 command, but don' t know how to debug to the mouse driver problem.  Not sure what changed from 6.10 to 7.04, but it broke mouse support.

---

### Post by rampant badger on 2007-04-21
I  have the same problem with the mouse not working on Virtual PC for the Mac.
This was with a clean install of Feisty Fawn!

Virtual PC 7.0.2 (Mac)
Ubuntu 7.04

---

