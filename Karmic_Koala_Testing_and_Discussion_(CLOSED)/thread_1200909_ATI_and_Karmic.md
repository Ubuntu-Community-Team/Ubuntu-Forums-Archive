---
title: "ATI and Karmic"
date: 2009-06-30
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by CaptainMark on 2009-06-30
I know I'm not alone when I say
 "The only reason I'm still using Intrepid is because I have an ATI card." 
I want to update to Jaunty and eventually Karmic but I'm in a pickle, like a lot of others out there when I found out ATI support for Jaunty was less than useless (no/rubbish 3d support, depending on your card) I was keeping my fingers crossed for a post release patch but never got it. Eventually having given up on Jaunty and with Karmic looming just after the summer I need to know what the support will be like for us ATI users?

My card isn't even detected by the open source drivers on the Jaunty install disk, I'm hoping at least that will be changed for Karmic. Or should I just splash the cash on a Nvidia??

---

### Post by QIII on 2009-06-30
This might be worth a try:

[http://ati.amd.com/products/catalyst/family/index.html](http://ati.amd.com/products/catalyst/family/index.html)

---

### Post by CaptainMark on 2009-06-30
Yeah it was the Catalyst I was referring to with the rubbish 3d support comment.  Plus with a card thats not recognised at all by Jaunty because i think it may have been too new at the time, and no onbaord graphics slot, i would have to obtain a recognised graphic card to first install the propietary drivers, bummer, too much hassel. Hence considering the Nvidia option, i hear they have good 'out of the box' useability.

---

### Post by QIII on 2009-06-30
Unfortunate.

I got great results from Catalyst.

Well.  Until all the manufacturers get serious about drivers for Linux platforms, we are all swinging in the breeze, I am afraid.  I wouldn't hold my breath.

I sure hate to see you have to spend a few quid on a new card, though.

---

### Post by CaptainMark on 2009-06-30
Ive read ATI have realeased the programming documentation for a huge load of thier cards, perhaps for Karmic or more likely the next LTS release due in april ATI users will have open source drivers that let their cards work at full whack straight out of the box.   Ah we can dream...

---

### Post by hockeyhead019 on 2009-06-30
yea i would honestly switch to nvidia... nothing against ATI but as you've stated it doesn't have great support for it in ubuntu... or at least not yet or that i know of

---

### Post by lavinog on 2009-06-30
What card do you have?
Ati dropped support for older cards so they can focus on newer cards.
The open source driver is supposed to have 3d support for the newer cards by the time karmic is released.
If your card is too new...you have to use the latest proprietary driver from ati's website.

---

### Post by CaptainMark on 2009-06-30
Ive got ATI radeon HD 2400 pro, Jaunty has no built in os driver for me. I have use another card to install the propiatery driver as a deb first then switch back.  Im hoping Karmic will at least have a driver that will let me veiw the desktop and install the propietary driver the easy way. Please oh please. Any ideas how i would find out short of waiting for the live cd to come out?

---

### Post by lavinog on 2009-06-30
ok that is odd, the 2400 series should be supported. You might have to disable desktop effects until you install the proprietary driver, or use the mesa driver.

---

### Post by CaptainMark on 2009-06-30
Nope just cant access any kind of graphical interface from the live cd, think its different for the AGP socket i dont have pci express.  Ive got it perfect on Intrepid, running propietary driver, full 2d/3d support, compiz an all. I just dont want to risk loosing it all by upgrading.

---

### Post by lavinog on 2009-06-30
It might be that the live cd is trying to use desktop effects.
To be honest the last three fglrx drivers (april through june) have had some video corruption issues on my boxes.
I have to use blender in windows at the moment because of it.

---

### Post by ssri on 2009-07-01
Fellow ATI intrepid squatter here.  From the looks of it, us ATI lusers will continue to enjoy crappy 3D performance on r500 cards till next year (Summer 2010)!  BTW, how long does support for intrepid run again? ;)

[http://www.phoronix.com/forums/showthread.php?t=17887](http://www.phoronix.com/forums/showthread.php?t=17887)

[http://www.phoronix.com/forums/showthread.php?t=14674](http://www.phoronix.com/forums/showthread.php?t=14674)

---

### Post by cottfcfan on 2009-07-01
You`re using the exact same ATI card as me.
Mine works fine.
1st follow this workaround.
[http://ubuntuforums.org/showthread.php?t=1130582](http://ubuntuforums.org/showthread.php?t=1130582)
use the safe option.
Reboot.
Then install the latest driver from ATI website.
[http://support.amd.com/us/gpudownload/linux/Pages/radeon_linux.aspx?type=2.4.1&product=2.4.1.3.1&lang=English](http://support.amd.com/us/gpudownload/linux/Pages/radeon_linux.aspx?type=2.4.1&product=2.4.1.3.1&lang=English)
Reboot.
Configure using ATI Catylist.
Works a treat 3D, Compiz, the lot.
Try it and post back.

---

### Post by CaptainMark on 2009-07-02
As posted earlier, I have my set configured fine with compiz and everything and full 3d performance as its been for ages. Its not that i have the trouble with, its the live cd because you cant configure drivers or settings on a live cd straight out of the box. And its really not a big deal, the point of the post was to determine future ubuntu/ati performance. Id like to be fully up to date with my OS, not held back by my graphics card.  Which 512mb (at least) card can i get for a good price, with good out of the box performance. Is nvidia a good bet?

Oh and intrepid support goes until April 2010. [http://en.wikipedia.org/wiki/List_of_Ubuntu_releases](http://en.wikipedia.org/wiki/List_of_Ubuntu_releases)

---

### Post by Dipper on 2009-07-27
I would really hope the developers of Ubuntu realize the pickle that ATI users are in and extend the Intrepid support period beyond April 2010.  Many ATI users have the option to bite the bullet and upgrade to nvidia.  But there are many of us laptop users who don't have that option and will be completely screwed if Intrepid support ends.

---

### Post by ztmike on 2009-07-27
> **CaptainMark said:**
> Nope just cant access any kind of graphical interface from the live cd, think its different for the AGP socket i dont have pci express.

Time to upgrade your computer to one that has PCI-E 

Why would you even want support for graphics on that old of a computer? As for people that have a PCI-E slot and have a ATI GPU that doesn't work with Linux..I say show them you mean business and stop supporting a company that doesn't care for its users. 

Nvidia is supporting us Linux users, and their cards are awesome. I picked up a used 8800GT for $75 and couldn't be happier..now Nvidia is beta testing the latest drivers for us Linux users which I believe is currently at build 190.18.

If people would stop buying ATI cards they would get the picture that they should be supporting ALL users not just Windows users.

---

### Post by QIII on 2009-07-27
> **ztmike said:**
>  If people would stop buying ATI cards they would get the picture that they should be supporting ALL users not just Windows users.

ATI does support its users, including Linux users.  ATI has Linux specific drivers that they constantly upgrade.

I'm no ATI evangelist.  I am happy with my nVidia machines.  I am happy with my ATI machines.

Both the "hate ATI" and "hate nVidia" crowds need to tone it down a bit.

---

### Post by ztmike on 2009-07-27
If ATI supported Linux users then why is it a known fact that they don't? They might support some but for the most part its shitty from what I've seen to say the least.

---

### Post by lavinog on 2009-07-27
> **ztmike said:**
> Time to upgrade your computer to one that has PCI-E 

Why would you even want support for graphics on that old of a computer? As for people that have a PCI-E slot and have a ATI GPU that doesn't work with Linux..I say show them you mean business and stop supporting a company that doesn't care for its users. 

Laptops cannot be upgraded.
When purchasing a laptop, you have to look towards the future. Since ATI decided to give documentation for their cards, I can expect that my laptop will work with open source drivers when proprietary support is dropped.
I expect that the open source radeon driver in Karmic will have 3d support with all cards.

> If people would stop buying ATI cards they would get the picture that they should be supporting ALL users not just Windows users.
I don't know much about ATI's business strategy, but I am pretty sure that the linux community can't paint a big enough picture.
Ignoring market share, and focusing on linux: what percentage of ATI linux users are affected by the current bugs?
ATI is going to focus on fixing the bugs that affect the largest percentage of linux users...which would not be gamers.
There was a statement once that pointed out that enterprise users come first. Why shouldn't they, businesses purchase many times more computers than everyday consumers. If ATI started focusing on fixing eye candy and gaming issues before enterprise issues, then they might have a problem.

I am not trying to be negative. ATI has good intentions with the linux community. Every organization has resource limits. If ATI invested all of their resources into their linux driver, with no expected gains in profit, they will cease to exist. Maybe they could get a paypal account.
Bugs take time to fix. How many bug free programs/drivers are there?

Does the nVidia driver support dri2?

---

### Post by QIII on 2009-07-27
> **ztmike said:**
> If ATI supported Linux users then why is it a known fact that they don't? They might support some but for the most part its shitty from what I've seen to say the least.

It's a known fact?  News to me.  My drivers work fine.  Full 3d support, Compiz, Java, Flash...

What have you "seen"?

---

### Post by CaptainMark on 2009-07-27
It all seems to depend alot on what setup your using, some ati cards work fine, others poorly some not at all. Personally i decide to jump the ati ship and landed on my feet in the nvidia rescue boat. works ten times better and infiinatley easier to install. No problems no bugs on my 8400gt.  Its a two sided arguement but nvidia definatley has the edge right now.

---

