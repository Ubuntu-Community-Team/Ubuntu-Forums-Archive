---
title: "Has anybody got the new linux_2.6.28-4.5"
date: 2008-12-27
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by ShirishAg75 on 2008-12-27
Has anybody got the new linux_2.6.28-4.5 as part of updates, I'm looking for people on i386 architecture.

---

### Post by autocrosser on 2008-12-27
Have not seen it yet--using the main repo---will post as soon as I do.....

---

### Post by Starks on 2008-12-27
The packages are built but not in the repo yet.

[https://launchpad.net/ubuntu/jaunty/+source/linux/2.6.28-4.5](https://launchpad.net/ubuntu/jaunty/+source/linux/2.6.28-4.5)

---

### Post by vishalrao on 2008-12-27
looks like ext4 is built in...

---

### Post by ShirishAg75 on 2008-12-27
ext4 is built in the new kernel, now need grub2 and ubuntu-installer to have ext4 support.

Vishal, did you get the new kernel yet in updates (I mean with metapackage and all).

---

### Post by obsrv on 2008-12-27
Have it on x86_64 :) no problems so far.

---

### Post by plun on 2008-12-27
> **ShirishAg75 said:**
> Has anybody got the new linux_2.6.28-4.5 as part of updates, I'm looking for people on i386 architecture.

Yup...  linux-libc-dev just arrived and image and headers are also available...  testing :)

Running a clean vanilla 2.6.28 for the moment... good to compare with.

---

### Post by Gina on 2008-12-27
Once the daily builds have settled in and provided whatever it was that prevented installation is fixed, I'll do a new install of Jaunty on my AMD64 and check things out.  If/when ext4 is available with it's dependent other bits to use at installation, I shall try that.  Looks like things are beginning to get a bit exciting - I haven't had a new filesystem format to try since going over to Linux fully.

---

### Post by plun on 2008-12-27
Followup... excellent performance and everything seems to work at least for me.

Also beloved eye-candy after reinstalling my dirty driver... :D

---

### Post by autocrosser on 2008-12-27
I'm in--the PPA nvidia driver works very well in the new kernel---no problems noted as of yet...

---

### Post by ayates on 2008-12-27
No joy here.  The NVIDIA-Linux-x86-173.14.15 driver doesn't find any input devices. Worked fine on 2.6.28-3.

---

### Post by ShirishAg75 on 2008-12-27
ayates, 
 did you get it through normal updates (i.e. the metapackage) or did you install it?

---

### Post by ayates on 2008-12-27
> **ShirishAg75 said:**
> ayates, 
 did you get it through normal updates (i.e. the metapackage) or did you install it?
Installed. Did the same for 2.6.28-3.

---

### Post by ShirishAg75 on 2008-12-27
I had got the metapackage by updates.

---

### Post by vishalrao on 2008-12-27
shirish, what command did you run to get .28-4.5 ? i ran "sudo aptitude safe-upgrade" and im on .28.3 still. i do see -4.5 listed in apt search...

---

### Post by Slug71 on 2008-12-27
I just checked Synaptic and didnt see it there either.

Edit: And i'm all up to date.

---

### Post by autocrosser on 2008-12-27
Hey slug---are you using the US repos or the ubuntu main? The main had it this morning----

---

### Post by Slug71 on 2008-12-27
> **autocrosser said:**
> Hey slug---are you using the US repos or the ubuntu main? The main had it this morning----

Main, 
I got the Headers and Image from Packagekit but still missing the Restricted Modules.

---

### Post by autocrosser on 2008-12-27
AH---I don't have anything that needs the restricted--I only have the nVidia driver & a Ralink card that uses DKMS for the build...I did see that restricted .4 was in the build, so it should be available soon.

---

### Post by ronacc on 2008-12-27
on main here too still not seeing the restricted modules either but got the rest and it works fine with a hand installed 180.16 and ignore abi on my 7600gs

---

### Post by ShirishAg75 on 2008-12-28
seems linux-meta just passed through, let's see if it got built or not. 

[https://lists.ubuntu.com/archives/jaunty-changes/2008-December/002304.html](https://lists.ubuntu.com/archives/jaunty-changes/2008-December/002304.html)

Update :- It got built atleast on the i386 infrastructure and got published about 26 minutes back . 

[https://edge.launchpad.net/ubuntu/+source/linux-meta](https://edge.launchpad.net/ubuntu/+source/linux-meta)

[https://launchpad.net/ubuntu/+source/linux-meta/2.6.28.4.4/+build/823087](https://launchpad.net/ubuntu/+source/linux-meta/2.6.28.4.4/+build/823087)

---

### Post by DougieFresh4U on 2008-12-28
I got it last nite and all seems smooth :)

---

### Post by ayates on 2008-12-28
> **ayates said:**
> No joy here.  The NVIDIA-Linux-x86-173.14.15 driver doesn't find any input devices. Worked fine on 2.6.28-3.

I have a funny feeling it has something to do with the attachment. 

Does anyone know why they changed all these from modules to loaded ?

The vmlinuz, of course, went from 2.3M to 3.2M.

---

### Post by glasen on 2008-12-28
This is clearly an experiment how much the boot time of the system can be improved if most of the commonly needed modules (filesystem, ide-drivers, etc.) are directly build into the kernel.

Most of the boot time is wasted to "udev" which searches the corresponding driver to the found pci-id. The less drivers "udev" need to search for, the faster this task will ended.

---

### Post by Slug71 on 2008-12-28
The new Kernel seems pretty good so far but still no sound for me though.

---

### Post by ayates on 2008-12-28
> **glasen said:**
> This is clearly an experiment how much the boot time of the system can be improved if most of the commonly needed modules (filesystem, ide-drivers, etc.) are directly build into the kernel.

Most of the boot time is wasted to "udev" which searches the corresponding driver to the found pci-id. The less drivers "udev" need to search for, the faster this task will ended.

Yes. According to bootchart, it saves about 2 secs.

---

### Post by ShirishAg75 on 2008-12-28
> **ayates said:**
> I have a funny feeling it has something to do with the attachment. 

Does anyone know why they changed all these from modules to loaded ?

The vmlinuz, of course, went from 2.3M to 3.2M.

ayates, 
 how did you get that config-diff.txt?

---

### Post by ayates on 2008-12-29
> **ShirishAg75 said:**
> ayates, 
 how did you get that config-diff.txt?

xxxxxxx@jaunty:/boot# diff config-2.6.28-3-generic config-2.6.28-4-generic  > config-diff.txt

---

### Post by ayates on 2008-12-29
> **ayates said:**
> No joy here.  The NVIDIA-Linux-x86-173.14.15 driver doesn't find any input devices. Worked fine on 2.6.28-3.

My bad. I used another xorg.conf someone had posted and now all is fine.
Here it is if anyone's interested.

---

### Post by inxygnuu on 2008-12-29
Ok, I know I am going to sound like a moron, but how do you get the new kernel?

---

### Post by autocrosser on 2008-12-29
If it hasn't shown up in your updates---Open Synaptic & search for Linux-image

---

### Post by inxygnuu on 2008-12-29
Thanks, but when I search, I find it and it says "mark for reinstallation" how do I find out what kernel I am using?

---

### Post by adult swim on 2008-12-29
uname -r

---

### Post by inxygnuu on 2008-12-29
Ok, now I am slightly confused. I don't know how to boot into the kernel. I need to boot into the new kernel, but when I change the -3 to -4.5 it gives me an error, whats the fix? I have 2.6.28-3 and I need _***[COLOR="Red"]BLEEDING EDGE[/COLOR]***_. :P Is there a fix? Sorry to be a nuisance, I just want need a little help.

---

### Post by autocrosser on 2008-12-29
So I would guess that it is not in your menu.lst?  Check in /boot to see if the new kernel is there--if so, you need to edit the menu.lst....

sudo gedit /boot/grub/menu.lst  and then FOLLOWING the way other kernel lines are done---add the current kernel. If you want (and you are at this stage), I can provide the mods if you supply your menu.lst


If it is not in your /boot--you need to install it.....

Also--you should not put 4.5 in the grub list---only -4

---

### Post by Slug71 on 2008-12-29
> **inxygnuu said:**
> Ok, now I am slightly confused. I don't know how to boot into the kernel. I need to boot into the new kernel, but when I change the -3 to -4.5 it gives me an error, whats the fix? I have 2.6.28-3 and I need _***[COLOR="Red"]BLEEDING EDGE[/COLOR]***_. :P Is there a fix? Sorry to be a nuisance, I just want need a little help.

Wait a minute, did you install 2.6.28-4.5 with Synaptic or are you just trying to change the numbers in the grub menu.lst and thinking that it will boot into that Kernel? :confused:

---

### Post by autocrosser on 2008-12-30
I think he installed 4.5 and then edited his grub to reflect -4.5--that would explain the "not found" during boot.

---

### Post by inxygnuu on 2008-12-30
> **Slug71 said:**
> Wait a minute, did you install 2.6.28-4.5 with Synaptic or are you just trying to change the numbers in the grub menu.lst and thinking that it will boot into that Kernel? :confused:

no, I am not that dumb:lol::lol:. Synaptic said it was installed, so i edited the menu.lst to boot into it. I have another thread about this in the same forum if we are to discuss this.

---

### Post by Slug71 on 2008-12-30
> **inxygnuu said:**
> no, I am not that dumb:lol::lol:. Synaptic said it was installed, so i edited the menu.lst to boot into it. I have another thread about this in the same forum if we are to discuss this.

:lolflag: Ok just checking, had a loony come on here earlier freaking out that no one was helping him yet he wasnt giving any info to his problem. Edit the menu.lst to say 2.6.28-4 not 2.6.28-4.5

---

### Post by autocrosser on 2008-12-30
No sweat---If you start posting here regularly, you'll find that there are not many people here (compared to the other forums:D) & we all tend to keep a close track on what is going on....I've read that post & that's what put 2+2 together for me....

O--by the way---welcome to the testing group!!!!

Ya--that one was a real loon!!!!!  :) :)

---

### Post by inxygnuu on 2008-12-30
Oh, him? what was with him? He sounded not to offend, but like he was 5-9. Oh, and thanks for the welcome!:D I also got into Intrepid beta testing, but surprisingly, 8.10 beta is less stable than 9.04 alpha 2:lol:.

---

### Post by autocrosser on 2008-12-30
Don't know---we were all trying to help---I think it was a troll (or his head was the size of California......)

---

### Post by inxygnuu on 2008-12-30
I wanted to try, but I would end up like this:

[:(]("http://www.youtube.com/user/Micsega")

look at his "fag list" I am "Gshinato"

P.S. click on the sad face....

---

### Post by autocrosser on 2008-12-30
Interesting---people are strange.........

---

### Post by keep-on-smiling on 2008-12-30
Yep got the 2.6.28-4.5 - checked in synaptic for the version number - runs well. No nVidia driver available for my FX5500 as yet. System quite snappy :) .

cheers

PS: running Pentium 4 2.6 with 768 megs ram - kinda old, but still going...

---

### Post by ShirishAg75 on 2008-12-30
p4 with 1 GB RAM and still going smooth here as well.

---

