---
title: "Video card problem and upgrade!"
date: 2011-07-13
forum: Installation &amp; Upgrades
---

### Post by Newuser901 on 2011-07-13
One my video card died(8800gt) and I'm still trying to fix it. I have to take my last step and use a brush and try to clean out the socket to see if it works. I think It burned out or something. won't boot normally(seeminly) unless I take it out. Or else it just sits with the CPU phase lights on and give no beeps or indication of post. It seems to boot normally without the card. Tried taking out everything else and nothing. It's the only thing that seems to affect it. It's a factory OCed gigabyte 8800gt btw.(It's getting no signal to any monitor)

So, I'm thinking of upgrading and getting a new basic system instead of just rebuying a card and then turning the old one into a backup server or something.

I was looking at donig an AMD since it will be my first and it may be cheaper. I was looking at the 1100t type phenom 2s but something said buldozers were coming out. I could wait and upgrade. I'm looking into a system to build in taht area. If i can spend almost nothing on a cpu and board and upgrade it might be nice. but I hope it's better than teh q6600 intel I have now.

I coudl use some help. I'm not up on AMD. I was looking at this [MOBO]("http://www.newegg.com/Product/Product.aspx?Item=N82E16813128514"). Should I wait for a bulldozer or just get a 6 core now? I'm going for budget so I'm not sure what to do. but 180 is alot for a processor for me atm. Or would buldozer be overkill for a budget machine.

And what do I have to worry about with an AMD. I'm sure what I need to take into account. Especially when it comes to incompatible hardware.

I'll be running ubuntu on it.

---

### Post by tommcd on 2011-07-14
If you are on a budget, then stick with the current phenoms. The newer CPUs and the motherboards that support them will likely be more expensive than the currently available hardware.
Also, brand new hardware and motherboard chipsets can sometimes be problematic for linux compatibility. Older hardware will be more likely to be supported.
Here is a good site for linux hardware reviews: [http://www.phoronix.com/scan.php?page=home](http://www.phoronix.com/scan.php?page=home)
They have a hardware forums also.

---

### Post by Newuser901 on 2011-07-14
When you buy an AMD do you need to have more on the hyperthreading thing than the cpu needs? The 1100t says it's 4000t/s. Do you want more than that on the MOBO for the systems sake can you max it at the same speed as the CPU?

---

### Post by Newuser901 on 2011-07-14
Just to ask real quick(I have a hard time finding info in that large sticky for compatability) Do any of these have problems with compatability that anyone knows of?

[MOBO]("http://www.newegg.com/Product/Product.aspx?Item=N82E16813128521")
[CPU]("http://www.newegg.com/Product/Product.aspx?Item=N82E16819103913")
[VID]("http://www.newegg.com/Product/Product.aspx?Item=N82E16814500197")
[RAM]("http://www.newegg.com/Product/Product.aspx?Item=N82E16820220535")1 or 2 sets. 
I have a 650watt corsair PSU. The extreme ones. it's 3 years old but it should work.

I think that is around 635-730 dollars. 

Or should this be in teh newbie section? Don't mean to ask stupid or lazy seeming questions. I have some medical problems that make it hard for me to do certain things mentally. Combing through large text wears me out. 8)

---

### Post by tommcd on 2011-07-15
As near as I can tell from the nvidia website, that video card is only supported by the newest 275 driver. Ubuntu 11.04 only includes the 270 driver. So you may need to install the nvidia driver from the nvidia website manually if you do not wish to use the nouveau driver, or if nouveau does not work for that card, or if the nvidia-current driver in the Ubuntu repos does not work for that card.
I have not found any info on the motherboard. If you look at motherboards on newegg that have a lot of reviews, it is very common nowadays to see people mention linux compatibility in the reviews there. 
Besides the Phoronix website I mentioned earlier, here are 2 other sources for linux compatibility info:
[http://openbenchmarking.org/](http://openbenchmarking.org/)
And the LQ forums HCL:
[http://www.linuxquestions.org/hcl/index.php](http://www.linuxquestions.org/hcl/index.php)

---

