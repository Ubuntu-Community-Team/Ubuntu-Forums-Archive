---
title: "Installation/boot Problems"
date: 2010-09-22
forum: Installation &amp; Upgrades
---

### Post by Juice92 on 2010-09-22
Hello everyone :]

I'm having problems installing the latest version of Ubuntu on my laptop. My laptop is completely wiped clean, and I'm trying to install Ubuntu as my natural operating system. 

The problem is, after the CD loads the main menu, and I select either, "Try Without Installing," or, "Install," a new screen comes up black page, and text starts loading on it, including multiple, "Begin:...Done." and other things. When that page disappears, the computer pretty much stops reading the CD and it stalls on a blank, black screen. Now, that's if I take out the splash command, if I leave it, it goes from the main menu straight to the non-CD reading, black, blank screen of doom.

How do I go about installing Ubuntu on my laptop?
Thank you!

---

### Post by Rubi1200 on 2010-09-22
Hi and welcome to the forums :)

What graphics card do you have installed and how much RAM?

---

### Post by gramirez2012 on 2010-09-22
I am new to linux and I am also having this problem when I attempt to install on a ThinkPad R50e. I also downloaded a beta version that worked, but I'd rather install a stable release. How can I fix this issue?

---

### Post by Rubi1200 on 2010-09-22
> **gramirez2012 said:**
> I am new to linux and I am also having this problem when I attempt to install on a ThinkPad R50e. I also downloaded a beta version that worked, but I'd rather install a stable release. How can I fix this issue?
Beta = bugs

Download and install the latest stable version 10.04.1.

Make sure you backup important data first!

---

### Post by gramirez2012 on 2010-09-22
> **Rubi1200 said:**
> Beta = bugs

Download and install the latest stable version 10.04.1.

Make sure you backup important data first!
Hi, what I'm saying is that with the beta version, I can get to the install screen. The current stable release, 10.04.1 is just giving me a blank screen.

---

### Post by Rubi1200 on 2010-09-22
Ok, as above for the OP; what graphics card and how much RAM is installed?

We cannot help you without certain basic information.

Thanks.

---

### Post by Juice92 on 2010-09-22
256 mb of ram
NVIDIA GeForce FX Go5200

I think those two are the answers to your questions. :]

---

### Post by gramirez2012 on 2010-09-22
> **Rubi1200 said:**
> Ok, as above for the OP; what graphics card and how much RAM is installed?

We cannot help you without certain basic information.

Thanks.
It is an Intel Extreme Graphics II (855GME), and the computer has 768MB RAM.

---

### Post by mörgæs on 2010-09-22
> **Juice92 said:**
> 256 mb of ram
NVIDIA GeForce FX Go5200

I think those two are the answers to your questions. :]

Then I would go for Lubuntu:

[http://ubuntuforums.org/showpost.php?p=9834517&postcount=261](http://ubuntuforums.org/showpost.php?p=9834517&postcount=261)

---

### Post by mörgæs on 2010-09-22
> **gramirez2012 said:**
> It is an Intel Extreme Graphics II (855GME), and the computer has 768MB RAM.

10.04 does not work well with Intel 855:
[https://wiki.ubuntu.com/X/Bugs/Lucidi8xxFreezes](https://wiki.ubuntu.com/X/Bugs/Lucidi8xxFreezes)

You could try some of the workarounds described in the link or install 9.10, plain and simple.

---

### Post by Juice92 on 2010-09-22
Is Lubuntu basically the same thing?
Could you tell me any major differences if there are any?

Also, "Remember to have wired internet access throughout the installation."
This doesn't have to necessary have to be on the same computer, right?

---

### Post by mörgæs on 2010-09-22
> **Juice92 said:**
> Is Lubuntu basically the same thing?
Could you tell me any major differences if there are any?

Lubuntu is another desktop environment. You can see a lot of demos on Youtube.

> **Juice92 said:**
> 
Also, "Remember to have wired internet access throughout the installation."
This doesn't have to necessary have to be on the same computer, right?

The computer, on which you are installing, should be connected during the process and the following boot.

---

### Post by Juice92 on 2010-09-22
Well then we have a problem..lol
The computer is completely cleared and can't get on the internet.

---

### Post by Rubi1200 on 2010-09-23
> **gramirez2012 said:**
> It is an Intel Extreme Graphics II (855GME), and the computer has 768MB RAM.
On my test laptop I applied the Glasen PPA workaround in the link that mörgæs kindly posted; in my case, it worked flawlessly, but of course everyone has a different setup so no guarantee.

Barring that, it's back to 9.10 until the issues with Intel 8xx chipsets are resolved (quite possibly in the next release). Also, 9.10 is stable and supported until April 2011, so why rush to get the latest and greatest?

---

### Post by mörgæs on 2010-09-23
> **Juice92 said:**
> Well then we have a problem..lol
The computer is completely cleared and can't get on the internet.

Just have a cable to the router, so Ubuntu (running from the CD during installation) can get to the web when it wants to.

---

