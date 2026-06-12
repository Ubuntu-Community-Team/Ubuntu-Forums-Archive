---
title: "RAMDISK: Compressed image found at block 0"
date: 2016-03-26
forum: Installation &amp; Upgrades
---

### Post by MibunoOokami on 2016-03-26
Hi everyone,

I'm in the middle of installing Linux onto a friend's old Compaq 700 and have run into an issue or two. 

Knowing Ubuntu is too big for 256MB, I tried Lubuntu mini live cd but right from the get go it can't connect to the internet for installation and I can't seem to get it to install without the internet. I tried Lubuntu alternate and that installed without a hitch but runs very, very slow. I decided to try using SlaxOS in RAM but got an error message about RAM being 60% used and that an error occurred that should never occur. Upon rebooting I saw what looked like an error ```
RAMDISK: Compressed image found at block 0
``` and I'm wondering if this error might be what is causing Lubuntu to be so slow.
When I say slow I mean after a reboot and no other programs running, firefox takes 137 seconds to load. That's after changing the swappiness to 10.

I have since done some searching but there seems to be very little useful info about solving this problem. The one [thread]("http://www.vanemery.com/Linux/Ramdisk/ramdisk.html") I did find does offer a solution, except it's pre grub2, and I've opened a couple of grub files but none contain the same information as the thread. 

Does anyone know how I can get rid of this RAMDISK error? Without buying new RAM?

---

### Post by ajgreeny on 2016-03-26
You should not actually need internet access to be able to install from the mini-iso CD version, but you will only be able to install a command-line system and then later add what DE you want using ethernet.

If you can use an ethernet connection, not wifi, you should be able to install a lubuntu-core system, but you may find that a full Lubuntu OS is struggling with only 256MB ram.

Can you add any more RAM? Even another 256MB will make quite a difference.

The alternative is to look at other OSs entirely, such as Puppy-Linux which will almost certainly run on that machine, though you may still have to work at it for wifi connection.

---

### Post by MibunoOokami on 2016-03-26
> **ajgreeny said:**
> You should not actually need internet access to be able to install from the mini-iso CD version, but you will only be able to install a command-line system and then later add what DE you want using ethernet.

My Livecd must not have burnt properly because I still get the same interface when selecting the install from command line option and regular install. As soon as it gets to the download part and wants a different mirror, if I select cancel and try and skip ahead it spits out another error message then moves back to the download stage.


> **ajgreeny said:**
> If you can use an ethernet connection, not wifi, you should be able to install a lubuntu-core system, but you may find that a full Lubuntu OS is struggling with only 256MB ram.

I didn't think it necessary to say I was using ethernet, computer is too old for wi-fi. Is there a difference between Lubuntu-core and Lubuntu-mini? I thought they were the same thing, then alternate and full.

> **ajgreeny said:**
> Can you add any more RAM? Even another 256MB will make quite a difference.

The alternative is to look at other OSs entirely, such as Puppy-Linux which will almost certainly run on that machine, though you may still have to work at it for wifi connection.

I'm convincing my friend to switch to Linux and sold it as being able to work on any machine including old ones like this. It'd be a bit embarrassing if I had to say he needs more RAM.

Would Lubuntu alternate or even Slax not work though if I could fix this RAMDISK compressed image error?

---

### Post by MibunoOokami on 2016-03-26
I gave DSL a go, it looks like that could work and be useful except it doesn't look like there's been a new release/any updates since 2012 and it doesn't like the built in mouse. The cursor has a mind of its own and likes to live at the very bottom of the screen. It did seem to co-operate with a USB mouse which I guess could be OK.  
 

 The size of the processor is unknown, it has 20GB HDD and 256MB RAM which I figured would be enough for my friend to become familiar with Linux and to make a decision about converting his  important everyday PC from Window$.
 

 As soon as I get my hands on some more blank CDs I'll try Puppy.

---

### Post by grahammechanical on 2016-03-26
> Is there a difference between Lubuntu-core and Lubuntu-mini?

If it is anything like the difference between Xubuntu-core & Xubuntu mini, then it is actually Ubuntu mini ISO in all cases. This is what I found recently when I tried installing xubuntu-core. You might find that Lubuntu minimum is Linux & Lubuntu core is Linux with LXDE and a very minimal version at that. You would then need to install Lubuntu desktop to get the standard set of applications.

By the way, I found the 15.10 version of Ubuntu mini ISO to be much improved. Selecting & installing desktop environments is now much more understandable for those with no experience of this ISO image.

Regards.


Regard

---

### Post by MibunoOokami on 2016-03-30
> **MibunoOokami said:**
> As soon as I get my hands on some more blank CDs I'll try Puppy.
There's something peculiar going on with Puppy, I've tried burning the iso several times but the disk keeps being spit out with an error message saying "failed to burn". Laptop is too old to be booted from USB ;)

> **grahammechanical said:**
> If it is anything like the difference between Xubuntu-core & Xubuntu mini, then it is actually Ubuntu mini ISO in all cases.

The so-called Lubuntu mini live cd is missing the "L" at the start up screen, just says Ubuntu. I would imagine that should still work though. I downloaded and burnt the ISO 2x so I have no doubt I downloaded the correct ISO.


> **grahammechanical said:**
> 
By the way, I found the 15.10 version of Ubuntu mini ISO to be much improved. Selecting & installing desktop environments is now much more understandable for those with no experience of this ISO image.

Hopefully the same will be able to be said when 16.04 is released coz I'm thinking of trying that one out.

---

### Post by MibunoOokami on 2016-03-31
Is there no way of removing the compressed image? Or is this a case of the RAM is somehow stuffed and needs more/to be replaced?

---

### Post by MibunoOokami on 2016-04-17
I managed to install a command-line system of Lubuntu without any error messages. Had removed RAM yeterday to give the machine a tidy up, so I'm unsure which of the two contributed to solving this compressed image at block zero issue.

The computer seems to be running fine, it's now just a matter of whether or not my friend will be impressed and make the change.

---

