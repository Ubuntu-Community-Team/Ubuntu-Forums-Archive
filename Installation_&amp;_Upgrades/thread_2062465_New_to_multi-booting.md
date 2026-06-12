---
title: "New to multi-booting"
date: 2012-09-25
forum: Installation &amp; Upgrades
---

### Post by Aisaka_Tiger on 2012-09-25
Hi, it's me again. And as usual I've done some more, even more hardware upgrades.

I don't know if I mentioned this last time, but I now essentially, have a Intel 2500K and HD 6870. And probably going to wait to upgrade these further because as it stands they're pretty good. But that's just fluff that isn't important.

I updated my hard drives to having **my main OS drive a *80 GB SSD***. I'm planning on using this as my main OS drive(for my highest model of PC I've built, universally) for a very long time. Perhaps forever(or until something better than an SSD actually exists), far longer than my current GPU and CPU.

And this means that I want plenty of backup. The first thing I did with Windows 7 was install a bunch of basic stuff like graphics drivers, firefox, and ect. And then backed it up. Also installing an extra boot of vanilla Ubuntu through wubi. Which I am for some reason more comfortable using right now. Perhaps that I noticed I've already made some weird errors by messing with regedit for all of my big programs and games in my 

I've rambled on for far too long. What I'm getting at is that, since this will be my main OS drive to my major enthusiast hardware PC for a long time, I'd like to have as many operating system boots on this SSD as I can fit. And I honestly have no clue how to create more than two boots. 

For instance, I'd like to, along with my Windows 7 and Ubuntu boot up, extra Ubuntu boots in case something goes wrong with this one. Windows 8 preview for all of those program compatible with 8(so I don't have to rely on 7 expect for Windows 7 specific software), Linux Mint, and so on and so forth. I'd feel really secure if I could do that, that if a problem goes wrong with an OS boot of mine, I can just immediately get back in the game or program without spending the time to use a backup restoration. Also variety and capriciousness. But I have no idea how. Should I use GRUB? Does GRUB work with Windows and Linux both? Should I create an extra partition on my SSD in order to avoid accidentally saving over my old Windows and Linux operating systems? Does wubi conflict with making more than two boots? I don't know, but what I do know is that I want 3-7 operating systems on my SSD, main OS drive I have invested in.

[SIZE="7"]**tl;dr:** I want to make 3 or more boots, both Linux and Windows, but I have no idea how. Can I have help please?[/SIZE]

**Edit:** Apparently, there's a little something called EasyBCD. Which maybe I should look into. But I have no idea how it interacts with wubi and so forth. What I do know, is that I want the most effective and efficient way for when I boot up my computer, to have a selection that looks a bit like this:

Windows 7
Windows 8 (Preview)
Windows 8 (Preview)
Windows 8 (Preview)
Ubuntu
Ubuntu
Ubuntu
Kubuntu
Xubuntu
Lubuntu
Linux Mint

That would make me feel free to be very capricious, secure, and happy.

---

### Post by nshiell on 2012-09-25
A little off topic but have you thought about Virtualisation i.e. Virtual Box?
I have it, it lets me run any OS inside a window (so I can have multiple virtual PCs running at once).

---

### Post by cortman on 2012-09-25
You want to cram all that onto 80 GB?
I don't think that'll work, or at least it'll be a pinch.
Windows 7 is going to want at least 20-30 GB. I don't know about Win8, but I can't imagine it being much less.
10 GB each for the GNU/Linux installations will be a bit tight if you want to install many programs or save much data.
In any event, The simplest way to do it is simply to install in the order you listed them- i.e., Windows first, then Ubuntu, etc. The first GNU/Linux system you install will also install Grub, which will enable you to boot from any of those operating systems.

---

### Post by Starfleet on 2012-09-25
Aisaki, that sounds an interesting project. But some valid points have been raised above, particularly by cortman. You will not have the space to do what you want on an 80gb ssd if indeed you want your boot menu to look like your 'selection'. But I like your upgrades.

Firstly, I'm not too sure that so many operating systems are going to be a good thing, or even needed on one machine. But of course only you can answer that. I say this because out of the systems on your 'selection' you list it is probably only the Windows OS's that will break! In Linux, breakages are much less likely in the first instance and in my view are easier to fix than in many instances of a Windows collapse. Linux is a bit like a B17 bomber. It can take a lot of damage and still keep going so if you are thinking you will damage Ubuntu or any Linux distro easily, then don't.

I'm not an expert on multi booting, and I don't know much about Wubi. But nshiell makes a good point. If you don't want to do that, you need to be careful. Assuming you have the space on one or other of your drives I'd go for maybe three systems. I personnally wouldn't bother with Win8. I've reviewed it over the last 3 months and it's troublesome at present. Failures are quite common if you like to really use it. Win7 is much much better IMHO for the moment. Inyour position I'd go Win7, Ubuntu 12.04, and Mint if you like that. Grub2 will easily deal with all the bootups no problem. Each time you load an operating system after Windows, the Grub will update itself and you will see a nice neat bootup menu each time you start your machine letting you select which operating system you want to use. I would do just a little research to read up on multi booting first. I personally would not bother with Easybcd in your case. Grub is easier. 

Post back with any other finer detail points you are unsure of and I'm sure someone can help, maybe even me! Good luck.

---

### Post by oldfred on 2012-09-25
I have a 60GB flash drive with two Ubuntu versions installed in 30GB / (root) partitions. One has about 9GB used and the other is just an install with about 5GB used. 

Windows needs 30% free to work well. Ubuntu needs some free space but maybe not as much as Windows. With 80GB one Windows and maybe two more Linux could be installed but all data needs to be on your rotating drives. 

I prefer to have an operating system on every drive, not try to have too many on one drive.

I use Ubuntu, but like this logic.
 Creating a Dedicated Knoppix Partition for large drives
[http://www.troubleshooters.com/linux/knoppix/knoppix_partition.htm](http://www.troubleshooters.com/linux/knoppix/knoppix_partition.htm)
Except I have multiple Ubuntu installs and rotate newest install from drive to drive.

---

