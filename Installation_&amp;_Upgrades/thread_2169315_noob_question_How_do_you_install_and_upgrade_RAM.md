---
title: "noob question: How do you install and upgrade RAM?"
date: 2013-08-21
forum: Installation &amp; Upgrades
---

### Post by FenrirXIII on 2013-08-21
Hello

My family has a:

 DELL XPS ONE (A2010)
32-bit Windows Vista Pre-Installed
260GB HDD
2GB RAM

since Vista was very faulty (permanent delete of files deletes but the the HDD bloats up with bytes as if the files weren't deleted).
I couldn't defrag and it wouldn't let me save because the computer thinks the HDD is full.

Since then, I upgraded it to:

32-bit Ubuntu 12.04LTS (doesn't allow 64-bit)
Change the HDD (because at one point the Original HDD fried due to overheating)
The pre-installed RAM is okay but sometimes acts slow... plus i think its time for an upgrade

Now my question is:

How do I install and upgrade a 4GB RAM (2 slots)? We don't have/can't find the owner's manual.

I've look online and I found this using [Crucial Memory Advisor Tool]("http://www.crucial.com/store/advisor.aspx") and gave me this:


[LIST]
[*]**Module Size: **4GB kit (2GBx2) 
[*]**Package: **240-pin DIMM 
[*]**Feature: **DDR2 PC2-6400 
[*]**Specs: **DDR2 PC2-6400 &#8226; CL=6 &#8226; Unbuffered &#8226; NON-ECC &#8226; DDR2-800 &#8226; 1.8V &#8226; 256Meg x 64 
[/LIST]

There is no A2010 model but there is XPS ONE 20 - and I assume that's the one. Am I on a right track?

I'm not very familiar installing RAMs, It should be just plug-and-play but I think there are some compatibility issues that I might overlook and fry the motherboard.
_Can you guys recommend me the best compatible RAM for the model (A2010)?_[B] [COLOR=#ff0000]Also, I've read that in 32-bit Vista the max RAM
is 3.5GB... would that also be the max RAM for 32-bit Ubuntu 12.04LTS?

[/COLOR][/B]My cousin tried installing RAMs on a computer that was given to him via plug-and-play install (just plugging in new RAMs lying about noob style)
 and it fried the motherboard! Smokes and everything!
So I'm kinda scared trying it on with the family computer. How easy is it to install? What are things I need to worry about or pay attention to?

Thanks in Advance

---

### Post by SweetAurora on 2013-08-21
First off, that computer can use 64bit. Just because it came with 32bit Windows, dosen't mean the computer is 32bit too. So you can easily upgrade to 4GB of DDR2 667 or 800MHz ram. 

Anyways, 32bit Ubuntu comes with the PAE kernel which makes use a special feature in CPU's to address BEYOND 3.5GB. I beleve up to something like 16 or 32GB max. Windows dosen't make use of it. Their way to "convince" you to buy a more pricey version of Windows to use all 4GB of ram.

Edit: The only thing that worries me is the Graphics Card. According to what I could find, it has a Radeon HD2400 in it. That card is no longer supported by ATI and has no drivers for Linux anymore beyond Ubuntu 12.04.1. So you if you want the PC to be happy and be of full use, install Ubuntu 12.04.1 to install the last drivers released for the card.

Here, download this version and use it. I'm almost certain you downloaded Ubuntu 12.04.2 on the main site. 12.04.1 is tucked away now, classified as an "old release". [http://old-releases.ubuntu.com/releases/12.04.0/](http://old-releases.ubuntu.com/releases/12.04.0/)

---

### Post by FenrirXIII on 2013-08-23
hello @SweetAurora

yeah right now i havent bought the rams but when i did install the 12.04.2LTS. so far for weeks it had been working smoothly... care to explain to me why to worry about the graphics card? what sort of issue am i going to be facing? i mean cause so far my family has been using it for movies, youtube, flash games on facebook and i didnt see any problem with that at all? we got a new HDD came to the mail today, this one is 500HDD (our old one that fried was 260GB.. and the temporary replacement is 160GB). should i still install the 12.04.2LTS or 12.04.1LTS to avoid conflicts in the future?

---

### Post by SweetAurora on 2013-08-24
12.04.1 will allow you use use the AMD provided ATI Drivers which will give you better graphics performance and possibly better power management on the card and have it run cooler. But if you are happy with how the card is performing now in 12.04.2, then you don't have to install 12.04.1. Just on 12.04.2, you will be stuck with the default open sourced ATI drivers that come with that version.

---

### Post by Thee on 2013-08-24
Installing RAM is really easy. But before you do, make sure that your motherboard supports that much RAM.

You need to know the model of your motherboard. Open up your PC case and look at the motherboard, you will see somewhere on the board printed the model number.
Then search for that model online (or the official site of the board manufacturer) and see how much RAM and what type of RAM your motherboard supports.

After you made sure the RAM that you are buying is compatible with your motherboard, all you really need to do is turn off and unplug your computer, open the case and put the RAM in the memory slot of your motherboard.
After you place the RAM in the slot, push it inside the slot and make sure the little plastic handles on the ends of the memory slot "click". After that, try to wiggle the ram a bit with your fingers, if it sits in the motherboard firmly, then its done.
Turn on the computer and the new RAM should be detected automatically

Good luck!

---

### Post by Buntu Bunny on 2013-08-24
You should able to find an owners manual online, like, at [Manual Owl]("http://www.manualowl.com/p/Dell/XPS-One/Manual/106191").

---

