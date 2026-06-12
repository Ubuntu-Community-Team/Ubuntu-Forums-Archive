---
title: "Trouble instaling Ubuntu:("
date: 2008-02-20
forum: Installation &amp; Upgrades
---

### Post by thdust on 2008-02-20
Hello. 
Today I was going to install Ubuntu for the first time. Always been useing Win. But sick of it..
Yesterday I read wery much on the net about Ubuntu and found out that my hardware was suported by Ubuntu, and decided to try that... This was my first time trying Linux so read on all the forums and help pages, and was realy fired up to try it. But it did not work:(

I did download Ubuntu dersktop 7.10 from the homepage. Both versons (64Amd and the other) Did burn the img file right. Everyting was god, so I started the PC with the CD in, and Ubuntu started up. Everyting was good. I picked Start up or Install Ubuntu. And it began to load.

On the 64AMD verson this happened:

A screen with :
Starting def.................... Ok
Starting pero.................. Ok
Checking bat.................. Ok
Running Local Boot........... Ok

Then nothing happend. So decided to download the PC verson..

On the PC verson this happened:

A screen with:
Starting def.................... Ok
Starting pero.................. Ok
Checking bat.................. Ok
Running Local Boot........... Ok

But this time it began to flash like it was detecting a graphic card or screen. Thia happened 6 times before this came on the screen:

Display server has been shut down about 6 times in 60 sek. It is likely something bad is going on. Waiting 2 min before trying again.

And I did try again about 10 times in secure mode and in both versons..

What is wrong?? Hope someone can help me. Realy wants to try Ubuntu..

My computer has this hardware..

Motherboard M2N32-SLI DELUXE (AMD sAM2)
Prosessor ATHLON 64 X2 6000+ S.AM2
Soundcard Onkyo pci se90
Graphic card Sapphire Radeon HD 2600 XT 256MB GDDR3, PCI-Express


Hope someone understand this and help me:)

Thanks from thdust:)

---

### Post by dstew on 2008-02-20
Probably, your Live CD is having a problem dealing with your hardware. This happens a lot. You can try kernel parameters to get the Live CD to boot if you want. To do this, you press F6 at the starting menu, and enter the parameters on the kernel line. Commonly used parameters are **noapic nolapic acpi=off**

If this doesn't  help, try the Alternate Install CD. It installs the same Ubuntu desktop system, but uses a text based installer that is more likely to work with your hardware. You get it from the same [Ubuntu download page]("http://www.ubuntu.com/getubuntu/download"), just check the box below the Start Download button.

---

### Post by wpshooter on 2008-02-20
Are you sure that you are trying the correct versions of Ubuntu for your hardware.

If your machine is AMD processor type make sure that you are trying either the 64bit version for AMD or the 32bit version for AMD.  

The reason I wonder about this is because you mention **PC version **in your original post.

Sorry, actually it looks like the 32bit is the same for both AMD and Intel.

You might want to try the ALTERNATE CD versions.

Good luck.

---

### Post by thdust on 2008-02-21
Hi again:) Today I tried what you said. First I pressed F6 and typed noapic ........ But the same happened:( The screen flimmered and the same waring came..

So i decided to try the altenate verson..

In that verson the instalation went like a dream. I formatted the partition with win and everything was fine. But when I was going to start up for the first time, the same happened:(
It begun to startup and it began to flash like it was detecting a graphic card or screen. Thia happened 6 times before this came on the screen:

Display server has been shut down about 6 times in 60 sek. It is likely something bad is going on. Waiting 2 min before trying again.

Don`t know what to do. A little bit pissed of becouse I formattet win and had to go next door to borrow a pc to write this...

Is it impossible to get my graphic card to work in linux?? Hope not since it is a brand new one, and am not planing to buy a new one. And realy want to try linux...

Hope someone has the answer..

---

### Post by zvacet on 2008-02-21
When system is start to  boot you will see grub and there select recovery mode.After you login type 

```
dpkg-reconfigure xserver-xorg
```

and when it comes to drivers section select** vesa **and continue to the end.Restart and you should have basic graphic.

---

### Post by thdust on 2008-02-21
What is grub?? Where can I select recovery mode?? And where am I gona write that code?? Shall I hold in some keys??

---

### Post by jalirious on 2008-02-21
you need to install via the alternative cd, boot into safe mode, then 

root@yourcomp> ./youratidriver.run

after downloading it into your windows partition, then copying it over to that directory 


(you can find your windows partition in /media/sda2 (or 1)/Users/yourusername/)

reboot, go into the top ubuntu option.

---

### Post by jalirious on 2008-02-21
[http://ati.amd.com/support/driver.html](http://ati.amd.com/support/driver.html)

---

### Post by thdust on 2008-02-21
I have instaled it from the altenete disc.. And I don`t have a winows partition...

---

### Post by zvacet on 2008-02-21
When you start comp you will see kernel names displayed on your screen.Last line you see show you countdown(how many sec until Ubuntu start to boot up).If you don´t see grub press Esc button and then it will show up and it look like this


Ubuntu 7.10, kernel 2.6.22-14-generic

Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)

Ubuntu 7.10, memtest86+

From there select recovery mode and then you will be asked for username and password.After  you typed that type command I posted you.

---

