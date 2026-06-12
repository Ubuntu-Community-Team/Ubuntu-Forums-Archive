---
title: "Install Linux without floppy or cd-rom?"
date: 2006-08-29
forum: Installation &amp; Upgrades
---

### Post by jarek05 on 2006-08-29
Hi,
I need some direction on how to install xubuntu on my laptop.
It an old Toshiba with 600 MHz processor 256KB RAM, 12GB Hard Drive and PCMCI Network Card.
No floppy, no CD one non bootable USB port basically I have no way of booting this baby except from HD. 

So I have two ways of approaching this problem.
My first plan is to take this hard drive and put in another IBM laptop with bootable CD-Rom and install Linux from there.
However I’m afraid that this may not work and if works it’s going to by less then optimal installation since the installation would be done using totally different hardware.
My other plan is to put this hard drive in external USB case and hook this up to my desktop.
Create 3 partitions, first would be small boot only or boot and loader partition.
My second partition would be the biggest and would hold the Linux and third partition would have some sort of Linux ISO image or installation file for ease restore or reinstall option.
I would really prefer the second option since I think it’s the better option however I have no idea how or where do I start.

First I would need to create 3 partitions 
   aprox. A - 32MB boot/loader,
                                                                           B - 10GB Linux and 
                                                                           C – 2GB ISO/install.
Second what do I install on partition A Linux, dos or some self contain bootable OS Loader?
How should I execute above step (make A bootable) as main drive in IBM laptop or secondary USB drive in my workstation.
What can I put on C partition to easily reinstall or restore the B partition, I’m thinking about extracting ISO image from CD but how do I execute the install process or some sort of ghost image that I would have to create first.

Can you guys help me with this? Or is there better and easier option?

Thanks.

---

### Post by JamesB on 2006-08-29
I have heard that it is possible to put the HD in another computer and intall the server edition onto the HD, put back into original laptop and then install gnome, ubuntu desktop etc from repos and all should be well. If you search the forums, I think theres a post in dapper development which is now closed but accessable... where people have done just this. I was going to but then found the laptop itself ws broke.

All the best

James

---

### Post by confused57 on 2006-08-29
I don't know if this would work for you:

[https://help.ubuntu.com/community/Installation/Netboot](https://help.ubuntu.com/community/Installation/Netboot)

---

### Post by hakre on 2006-08-29
Is there a running OS on the machine? If yes, which one? This would be good to know, because it is possible to do what you want to do, for example:

Installation/FromWindows - Installing Ubuntu from Windows without using floppies, a CD, or any other removeable media
[https://help.ubuntu.com/community/Installation/FromWindows](https://help.ubuntu.com/community/Installation/FromWindows)

More Information might be available in that document and in the Installation section: [https://help.ubuntu.com/community/Installation](https://help.ubuntu.com/community/Installation)

And welcome to the Old PC Club!

---

### Post by jarek05 on 2006-08-30
No there is no OS on the machine right now.
I can install DOS or DOS linux equivalent by puting HD in different laptop.
Do you know of small linux distro that would make my machine bootable with very basic functionality and hardware independent. What I mean by hardware independend that it will not load hardware specific drivers. More like generic drivers so later I can move this hard drive back to original laptop

---

### Post by lha on 2006-08-30
Hi jarek05,

A great starting point for you is Marc Herbert's page ["Installing Linux without any removable media"]("http://marc.herbert.free.fr/linux/win2linstall.html"). The page has some notes on Ubuntu, but the mentioned installer files are outdated.

---

