---
title: "Trying to install VirtualBox"
date: 2015-06-16
forum: Installation &amp; Upgrades
---

### Post by RayTomes on 2015-06-16
I am on Ubuntu 14.04.2 LTS and a new Ubuntu user. I am trying to convert to Ubuntu from Win-XP. For some time I have used the common programs like Firefox, Thunderbird and so on to make it easy. There are a few windows programs that I won't be able to convert and want to continue to run. I have installed WINE but it looks like there is effort on every application and for a dummy this seems substantial. So I saw VirtualBox and decided to try that. I am guessing that it will run slower but requires no effort for each extra program that I want to run as I am actually running my existing Win-XP (I have dual boot at present). Is that right?

Anyway, I tried to install Virtual box using Ubuntu Software Centre. It asked me to insert my Ubuntu Installation DVD about 10 times to get additional bits of software. Then it just sat there. So I opened another workspace to do other things. Then my computer totally locked up and I had to do a hard power down and reboot. I did it all again several times and it never gets to showing it as installed.

Any suggestions please?

---

### Post by howefield on 2015-06-16
Virtualbox will run as a normal windows installation would except for being restricted by the virtualised hardware drivers that it will supply to the guest, hence the reason it is not a good way to play games, for instance. As long as your machine has sufficient resources to run both the host and guest operating systems simultaneously it should be fine, might help to know what the windows programs are and the specs of the machine ?

Assuming that you can download the relevant packages from the internet, no real reason to use the DVD, did you set it up that way deliberately  ?

---

### Post by RayTomes on 2015-06-16
I have no idea why it wanted the DVD, as no other software installation has asked for that. It was using the Ubuntu software centre and all other times it just got off the internet. I assumed that it wanted some extra bits that it knew were on the DVD.

My computer is a 32-bit processor with 2GB memory I think. I have 2 disks of 1 TB each. One of these is formatted to 3  partitions of 333 GB each and one of these is Win-XP and one is Ubuntu and the other essentially spare. I would just tell Windows it has the old C drive to use as is.

---

### Post by Vladlenin5000 on 2015-06-16
> **RayTomes said:**
> I have no idea why it wanted the DVD, as no other software installation has asked for that. It was using the Ubuntu software centre and all other times it just got off the internet. I assumed that it wanted some extra bits that it knew were on the DVD.

In a word: Dependencies. Whatever else you installed before didn't have dependencies that could came in the installation DVD, the one which isn't by default added to the software sources, users explicitly add it.
You better remove it. Since you're already using USC, just go Edit > Software Sources and untick the DVD.

> My computer is a 32-bit processor with 2GB memory I think.

Don't bother with virtual machines.
Stop using Windows XP at least online.
Always prefer the Ubuntu you already have. Please tell us what software you (think you) need, ie, the software you intended to install via WINE and later in a XP Virtual machine. You will be surprised (probably).

---

### Post by RayTomes on 2015-06-17
Thanks for reply Vladlenin

The list of things I might use from XP is probably long and boring.

1. I  definitely need to use CATS which is software that I have developed  with some help [http://www.cyclesresearchinstitute.org/cats/](http://www.cyclesresearchinstitute.org/cats/)
It is written in FreeBasic with ancient FORTRAN subroutines and it works.

2.  If I can I would use my old Corel Paint program for processing images  (from about 1994) which is superior to more modern software.

3. I have a number of little programs written in the Corel script language (CSC) that I do not wish to change or convert.

4. I like Irfanview, but I am finding Shotwell does much of what it does but by no means all.

5. I have hundreds of old QBasic programs.

I  have been using computers since the 1960s and have more stuff gathered  over the years than you can imagine. Of course the older it is the  harder it is to convert, and the less demanding it is of resources. I can live with a few things being a bit slow.

I  agree with you to stop using XP on line. That is my intention and is  easy enough because of Firefox and Thunderbird. Of my list, only Corel  Paint would possibly have impact on virtual machine speed I think.  Others are quite light.

---

### Post by RayTomes on 2015-06-17
Vladlenin, I unticked use DVD as you suggested and have now managed to install virtualbox.
I will give it a try keeping in mind your suggestion that I don't use it. At least in the short term it will save me a lot of boots.

---

### Post by Bucky Ball on 2015-06-17
Just a note: With 2Gb of RAM you are going to be running a little slim on RAM if you boot a virtual machine in Virtualbox when you do get it installed. The VM uses some of your installed RAM and the installed and running host OS uses the rest. With 2Gb that would mean 1Gb for each OS (VM client and host). That is not much and, depending on which OS is your host and which is your client and how resource hungry they are, may not be sufficient.

---

### Post by RayTomes on 2015-06-17
I have managed to create a Win-XP VM with a 20GB disk. Ideally I would like to use my real Win-XP C drive as a virtual drive also because it has 250GB+ of stuff on it that is what I will want to use. I found a page about this at [http://www.serverwatch.com/server-tutorials/using-a-physical-hard-drive-with-a-virtualbox-vm.html](http://www.serverwatch.com/server-tutorials/using-a-physical-hard-drive-with-a-virtualbox-vm.html) and I am wondering if this is all safe as long as I don't try to boot that drive in my VM? Alternatively I can use my real Win-XP D drive which is empty. If I don't do one of these I don't understand how I move data between my old Win-XP system and the new VM Win-XP.

---

### Post by RayTomes on 2015-06-17
BuckyBall, I wont be trying to run too much stuff at once. If I am using the VM Win-XP I will be happy to let Ubuntu do nothing much else.

---

### Post by RayTomes on 2015-06-20
Unless I could just run my C drive Win-XP as is without reinstalling 100 programs and directories, this isnt likely to be much use to me. So I will persist with learning Ubuntu for most of my needs and keep the dual boot. Thanks all.

---

