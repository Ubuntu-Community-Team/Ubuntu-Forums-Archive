---
title: "How to make a NONperistant ubuntu installation"
date: 2016-03-20
forum: Installation &amp; Upgrades
---

### Post by harrispartyof3 on 2016-03-20
over the last few years ive noticed i seem to build up a lot of junk on my various machines as i stumble through projects and try to get things working. I'm wondering if there is a way to install ubuntu to a computer much like how the live usb works, only install ubuntu, add some programs, then make any future changes get reset at boot.

So the main question is, how to I install ubuntu and various programs to a computer, then prevent any future changes from being permanent?

This is mostly so I can have a machine that I do all the testing and figure out what needs to happen to get things working, restart said machine to remove all my changes, rinse and repeat. Making the changes not stick seems easier for me since i wont have to manually reinstall the os and reconfigure ssh every time, and easier for the machine since it wont be recopying all of the same files every couple weeks.

Maybe the only way is to modify a live usb disk and just boot to that and skip installing all together, but how would i go about configuring ssh on a live disk? since the majority of the time i wont be able to physically get to the machine.

---

### Post by sudodus on 2016-03-20
1. I think many people solve that problem by making backups images, and can restore from such an image, whenever the current system is borked. ***Clonezilla*** is a good tool to do that.

[http://clonezilla.org/](http://clonezilla.org/)


2. An alternative if you have an installed system, that you like, and don't want to save the things you have done, is to log in as ***guest***. But the guest user cannot modify the system at all.


3. Another alternative is to make a persistent live system, and backup your modifications (make several images), and restore from such an image, whenever the current system is borked. Such systems can be created with ***mkusb***.

[mkusb/persistent](https://help.ubuntu.com/community/mkusb/persistent)

[Backup and restore of persistent overlay data](https://help.ubuntu.com/community/mkusb/persistent#Backup_and_restore_of_persistent_overlay_data)

---

### Post by harrispartyof3 on 2016-03-20
hmm clonezilla looks promising for that, how would i invoke that from ssh? from my quick search it sounds like i have to boot to a clonezilla live usb and manually restore an image, might be a way to have clonezilla automatically restore when the machine boots to the clonezilla drive but that would require a bios edit to change the boot order or a physical connection of the clonezilla drive. maybe theres some fancy grub configuration that can be used to switch between clonezilla and the ubuntu installation every other boot, that would work, assuming thats possible

---

### Post by grahammechanical on 2016-03-20
You might be interested in Linux containers (LXD/LXC)

With LXD/LXC installed on Ubuntu we can start another instance of Ubuntu or another distribution inside a Linux container. Mess around with it as much as we want. And just destroy the container and start again with another new container.

Linux containers do not use the system resources that a VM would. We can have several containers active at the same time and switch between them using Ctrl+Alt+F8 for the first container. Ctrl+Alt+F9 for the second container. And so on. And switch back to the host Ubuntu using Ctrl+Alt+F7.

[https://insights.ubuntu.com/2015/04/28/getting-started-with-lxd-the-container-lightervisor/](https://insights.ubuntu.com/2015/04/28/getting-started-with-lxd-the-container-lightervisor/)

This developer is writing a series of blog posts about LXD. At the moment it seems that his blog site is offline. But here is the place to start.

[https://www.stgraber.org/2016/03/11/lxd-2-0-blog-post-series-012/](https://www.stgraber.org/2016/03/11/lxd-2-0-blog-post-series-012/)

Today he posted the third blog in the series of twelve. It is on planet.ubuntu.com or here

[https://www.stgraber.org/2016/03/19/lxd-2-0-your-first-lxd-container-312/](https://www.stgraber.org/2016/03/19/lxd-2-0-your-first-lxd-container-312/)


Regards.

---

### Post by Bucky Ball on 2016-03-20
And it also takes a good degree of time to clone a full image to a drive. Okay if you have that kind of time to spare everytime you boot the machine. This is not instantaneous like booting a kernel ...

Personally, I set up an install which I don't change for day to day things, just the way I like it, and have another install on another partition as a 'plaything' where I can experiment as much as I like. When its fully broken or you just want to get back to square one, then clone the original image back to the plaything partition.

---

### Post by sudodus on 2016-03-20
> **harrispartyof3 said:**
> hmm clonezilla looks promising for that, how would i invoke that from ssh? from my quick search it sounds like i have to boot to a clonezilla live usb and manually restore an image, might be a way to have clonezilla automatically restore when the machine boots to the clonezilla drive but that would require a bios edit to change the boot order or a physical connection of the clonezilla drive. maybe theres some fancy grub configuration that can be used to switch between clonezilla and the ubuntu installation every other boot, that would work, assuming thats possible

After reading this second post of yours, I think you should run your system in a virtual machine. Then you can manage it via ssh to the host system. It is very simple, don't save the current state. Keep the previous state of the virtual machine and restart it the next time.

The LXD/LXC system described by grahammechanical look interesting. But I don't know about managing it via ssh.

---

### Post by harrispartyof3 on 2016-03-20
how would i set up a virtual machine? would that be a job for virtualbox? ive heard of vmware, is that the same or something completely different? from other things ive seen over the years it sounds like vmware is the most popular choice for virtual machines so if its possible to use that i would prefer that since it should (in theory) have the most support if i end up needing it. I like the virtual machine idea over my original idea since ill be able to put it on my existing server and wont need an additional machine running solely for testing.

---

### Post by sudodus on 2016-03-20
- VirtualBox
- vmware
- kvm + virt-manager

There are probably other alternatives too.

I have used VirtualBox and kvm + virt-manager. I think all three tools (also vmware) should work well for you.

I suggest that you browse the internet for them and read what you find interesting. Then you can come back with questions here. If you decide to go the virtual machine path, you can ask a moderator to move your thread to the [virtualisation sub-forum](http://ubuntuforums.org/forumdisplay.php?f=308), where people who are interested and know more about it can find your thread and help you.

---

### Post by harrispartyof3 on 2016-03-20
it looks like vmware is aimed towards a much larger deployment than what im trying to do, so it looks like ill be using kvm since that seems to be command line friendly, and the server thats going to run this is headless. Thanks for everyones help, Ill now start my journey with virtual machines

---

### Post by Bucky Ball on 2016-03-20
Or you can start a new thread about virtualistation in the appropriate forum as the rest of this thread has nothing to do with. :)

FYI: Virtualbox is in the Ubuntu repositories and there's plenty of help available for it online here, on the [Virtualbox]("https://forums.virtualbox.org/") forum and elsewhere. Not saying you should use VB in preference to anything else, just saying. 

Good luck.

---

### Post by sudodus on 2016-03-20
> **Bucky Ball said:**
> Or you can start a new thread about virtualistation in the appropriate forum as the rest of this thread has nothing to do with. :)

FYI: Virtualbox is in the Ubuntu repositories and there's plenty of help available for it online here, on the [Virtualbox]("https://forums.virtualbox.org/") forum and elsewhere. Not saying you should use VB in preference to anything else, just saying. 

Good luck.

+1 Good luck :-)

---

