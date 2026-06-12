---
title: "1st timer with Linux"
date: 2010-07-20
forum: Installation &amp; Upgrades
---

### Post by dpuk44 on 2010-07-20
Hey All

Just after some help really. I am new to Linux as have never used it before. I am very used to running Windows but want to try moving to Linux.

I have a hp pavilion zd8000 laptop. I know its a little old and not brilliant but its fast enough for what I need and was hoping that running Linux instead of Windows will be even faster.

As I have never installed Linux before on any machine I really wanted to know how to do it? Will the drivers for my devices be available from the Linux software? A guide would be really helpful.

Thanks alot :)

Dale

---

### Post by Zimmer on 2010-07-20
a reasonable start to your reading could be here
[https://help.ubuntu.com/community/UserDocumentation](https://help.ubuntu.com/community/UserDocumentation)

[https://help.ubuntu.com/community/Installation](https://help.ubuntu.com/community/Installation)
Read how to download an ISO and burn to a CD so that you can try Ubuntu without actually installing, but running from the CD..
(things can take longer to open as you are using the CD to access stuff but it will give you an idea of how the hardware is suported.)

Do you intend to wipe out any Windows OS currently residing on the machine?
Do you intend to try and keep a Win install and install Ubuntu alongside?

---

### Post by dpuk44 on 2010-07-20
Hi Zimmer

Thanks for getting back to me. As to your questions

Do you intend to wipe out any Windows OS currently residing on the  machine?
**YES -** its an new hard drive

Do you intend to try and keep a Win install and install Ubuntu  alongside?
**NO**

---

### Post by oldfred on 2010-07-20
How much memory do you have? Some versions of Ubuntu work better with smaller amounts of RAM.
[https://help.ubuntu.com/community/Installation/SystemRequirements#Lightweight%20GUI%20alternative%20%28Xubuntu%29](https://help.ubuntu.com/community/Installation/SystemRequirements#Lightweight%20GUI%20alternative%20%28Xubuntu%29)

Is this computer old enough that BIOS limits mean the boot files have to be at the front of the drive?
[http://members.iinet.net.au/~herman546/p15.html#18](http://members.iinet.net.au/~herman546/p15.html#18)

If you manually partition and make / (root) only about 20-25GB it will be at the front of the drive. You can then add swap of about 2GB and a /home as the rest of the drive.
[https://help.ubuntu.com/community/InstallingANewHardDrive](https://help.ubuntu.com/community/InstallingANewHardDrive)
[https://help.ubuntu.com/community/HowtoPartition/OperatingSystemsAndPartitions](https://help.ubuntu.com/community/HowtoPartition/OperatingSystemsAndPartitions)
[https://help.ubuntu.com/community/PartitioningSchemes](https://help.ubuntu.com/community/PartitioningSchemes)

---

### Post by Zimmer on 2010-07-21
Fresh Ubuntu only ... (on what appears to be a 2005 vintage laptop with a gig of RAM) then
[http://www.psychocats.net/ubuntu/installing](http://www.psychocats.net/ubuntu/installing)

could be the guide for you...

of course, once you experience how easy it can be (and that might not be the first attempt ;) ), 
you will read lots more about how to tweak this and that, to play about with partitioning your disk manually etc.... and maybe install all over again in a slightly different way..

But as you are a first-timer (and we do not know how much you might already know about disk formatting and partitioning) and you are starting with a clean drive this would seem a sensible first step forward...

---

### Post by dpuk44 on 2010-07-21
Thanks Zimmer

That is perfect :)

If I encounter any hardware issues I will let you guys know (fingers crossed I wont).

Thanks again

Dale

---

### Post by Phil Stone on 2010-09-07
Hi dpuk44.

I use a Ready To Go OS mostly but have installed linux versions numerous times. I have found it best to set up a dual boot with Ready To Go as your usable os with the linux os as your secondary os. This is so that when you get too stuck you can can just switch into the os you are familiar with and come back to the challenge the next day.

Though I have to say the linux distro's are now quite advanced in terms of a gui usability that has become the expectation of a Ready To Go OS user. The only problem is that they now seem to do all of the actual manual stuff you want to do for you. So it seems you either get a system than runs on command lines that doesn't get you anywhere or a system that does it all for you. let me give you an example:

I tried to install a linux distro a while back i don't think it was gui then but i had the real problem of not being able to install a certain dependancy because it required that I had a dependency installer installed which required a dependancy and so on and so forth.. nowadays the linux distoro's come with a practically fully automated package manager that pretty much does it all for you  (this is why dual booting shouldn't be too much of a hassle) so it kinda bypasses the whole learning how to untar a gzipped tarball and install a package yourself kind of thing...

Well at least the internet works straight away. I can use and learn with this one I think, Happy Days 

Phil

---

