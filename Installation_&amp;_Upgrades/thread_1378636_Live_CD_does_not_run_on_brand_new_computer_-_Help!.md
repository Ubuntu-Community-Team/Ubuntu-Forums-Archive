---
title: "Live CD does not run on brand new computer - Help!"
date: 2010-01-11
forum: Installation &amp; Upgrades
---

### Post by rlwpub on 2010-01-11
I just bought a new emachines et1331g-03w I can get the cd to boot and give me the choices. When I select run from cd it acts like it is getting ready to load and then the screen goes black and hangs.

I have tried both 8.04.3 32-bit desktop and 9.10 32-bit desktop both give the same problem. Both cds work fine on other computers.

Any suggestions on where to start looking for the problem?

---

### Post by studmf on 2010-01-11
Give this a shot [**[COLOR=blue]http://maketecheasier.com/solving-ubuntu-karmic-black-screen-issue/2009/12/29[/COLOR]**]("http://maketecheasier.com/solving-ubuntu-karmic-black-screen-issue/2009/12/29")**[COLOR=blue].[/COLOR]**
 
You may consider a different computer if you can find something in the same price range. Emachines are notorious for powersupply/motherboard failures. Hope the above fixes your issue.

---

### Post by rlwpub on 2010-01-11
> **studmf said:**
> Give this a shot [**[COLOR=blue]http://maketecheasier.com/solving-ubuntu-karmic-black-screen-issue/2009/12/29[/COLOR]**]("http://maketecheasier.com/solving-ubuntu-karmic-black-screen-issue/2009/12/29")**[COLOR=blue].[/COLOR]**
 
You may consider a different computer if you can find something in the same price range. Emachines are notorious for powersupply/motherboard failures. Hope the above fixes your issue.

Actually ordered a better power supply for it. :)

It has the nvidia chipset with AMD cpu and not the intel chipset. But thanks for the reply.

---

### Post by studmf on 2010-01-11
I by no means meant to put down your PC, powersupply=great idea.  Did that solve your issue?

---

### Post by rlwpub on 2010-01-11
> **studmf said:**
> I by no means meant to put down your PC, powersupply=great idea.  Did that solve your issue?

Sadly it did not solve the problem. It said not to try it except on Intel, but I tried it anyway.

My gut feeling is it has something to do with the onboard video card. Just a gut feeling though.

I have also read reviews where people have installed the 64-bit version without any problems.

---

### Post by stantiques on 2010-01-11
Try to download the alternate Ubuntu install CD, its a text based install.

---

### Post by rlwpub on 2010-01-11
> **stantiques said:**
> Try to download the alternate Ubuntu install CD, its a text based install.

The alternate cd does not have the live cd on it. Want to get it working before I actually do an install.

---

### Post by Sef on 2010-01-11
> Try to download the alternate Ubuntu install CD, its a text based install.

The alternate CD is easy to install.  The only tricky part is if you manually partition the hard drive.   It is not hard, but the first time it can get a bit confusing to manually partition.  If you take the default option then it will take care of it automatically.

---

### Post by rlwpub on 2010-01-11
> **Sef said:**
> The alternate CD is easy to install.  The only tricky part is if you manually partition the hard drive.   It is not hard, but the first time it can get a bit confusing to manually partition.  If you take the default option then it will take care of it automatically.

It currently has Windows 7 on it. I want to have both ubuntu and windows 7 in a dual boot configuration. Will the alt cd handle that for me or do I need to shrink the windows 7 partition first?

---

### Post by Sef on 2010-01-11
> It currently has Windows 7 on it. I want to have both ubuntu and windows 7 in a dual boot configuration. Will the alt cd handle that for me or do I need to shrink the windows 7 partition first?

Options:

A) You can need to manually partition the hard drive.   

B) You can shrink the partition with Windows 7 partitioner.   Then use the alternate cd to install Ubuntu on the empty space.   There is an option for that on the alternate cd.

I would recommend B.

---

### Post by presence1960 on 2010-01-11
[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

At the menu screen of the Live CD hit F4 and select safe graphics mode.

If that does not work then try the alternate text based installer as suggested.

---

### Post by studmf on 2010-01-11
Have you thought about doing the windows install and running ubuntu from there?

---

### Post by isantop on 2010-01-11
I'm having the same problem, though it may be from an entirely different cause, given my vastly different hardware...

My sys specs:
AMD Sempron 3400+ @ 2.0 GHz
NVIDA Geforce 9500 GT
1.5GiB RAM
All other specs are identical to a stock Compaq Presario SR1620NX

Previous versions all ran fine, up to Karmic. I haven't tried an upgrade, but was skeptical of that working at all.

My guess was that the problem had to do with the (radical?) changes from Jaunty to Karmic, and until now, I've done without, which is fairly sad.

Now, I'm fed up with Windows 7, and I want to get Kubuntu working again. I tried the link to a solution earlier in this thread, but to no avail.

I'm relatively experienced, having run some form of Ubuntu constantly since version 6.10. Even so, I can't figure this one out, and any help would be great. I do want to be able to use the liveCD to check for any other problems before I install. 

Thanks.

EDIT: For some reason, it will sometimes get to X startup, where it will hang. I can move the move around, but it is a loading cursor, and doesn't animate.

---

### Post by rlwpub on 2010-01-12
> **presence1960 said:**
> [https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

At the menu screen of the Live CD hit F4 and select safe graphics mode.

If that does not work then try the alternate text based installer as suggested.

I did try the safe graphics mode and it still hung with a black screen.

I also tried marking out everything in the F6 menu and it did manage to get to a terminal prompt. You just could not type anything and the screen blinked on and off.

---

### Post by rlwpub on 2010-01-12
> **studmf said:**
> Have you thought about doing the windows install and running ubuntu from there?

This is my wifes new computer and she hates windows with a passion except to play games. So she would never go for having to run Ubuntu inside windows.

---

### Post by rlwpub on 2010-01-12
Is there a way to have the live cd display everything it is doing so I can see where it hangs?

---

