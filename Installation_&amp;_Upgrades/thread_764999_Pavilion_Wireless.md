---
title: "Pavilion Wireless"
date: 2008-04-24
forum: Installation &amp; Upgrades
---

### Post by poopdog on 2008-04-24
Quick background: 

I'm not new to Linux. I ran it on my desktop for a while, but it was a couple years ago.

I really don't want to get heavy into the nuts and bolts of Linux.  I don't mind (and kind of like) command line, but I don't want to have to become a guru.

Situation:

I got an HP Pavilion 6000 about a year ago, but that last few versions of Ubuntu have not liked it very much.

During install I'll get this black screen and it'd freeze up.

There were some command line params to put into avoid this, but then I'd loose my USB when it came up.

Then I found people saying how to make this work, but I got fed up.

So naturally, when I was told that there was more Pavilion support, I was excited to install 8.04.

When I installed it, I was pleased to see that I didn't get that 'black screen' that the last few versions have done.

But my wireless card still doesn't work, and it's really frustrating.

My worry is that since a basic component like the wireless doesn't work, that there will be other compatibility issues as well.

Is the HP Pav just not a good choice to work with Ubuntu?

Should I wait a couple years until I get a new laptop to give this a try, or is the wireless issue a known "Big Issue?" 

I've heard that the company that makes the cards is notorious for not giving Linux support. Is that what I'm up against?

I'd appreciate any help/feedback/criticism.

---

### Post by Peter09 on 2008-04-24
Hi,
I think your card is the bcm42 (or similar) there is a driver in synaptic
bcmfw3.xxx fwcutter or similar.

This did the job on my sons pavilion.

PC

---

### Post by ssj3strife on 2008-04-24
Wireless is still a pain in the butt, regardless of your chosen Linux distro. It's usually a matter of finding the right package for your wireless chipset. If it's an Intel wireless, use the ipw package. Atheros chipset, use madwifi. Broadcomm... ugh, those are the worst, you might be able to get ndiswrapper to work for you. 

Do you know what chipset you have in your Pavillion?

---

### Post by Ayuthia on 2008-04-24
I have an HP Pavilion dv6000 (dv6338se) and most things worked right out of the box (currently using 64-bit Kubuntu 8.04).  In my opinion, since you have already done the install, you should try to get the wireless working.  Since you have already made it this far, I am thinking that wireless is probably going to be your main issue.  Most other things should work.

If I heard correctly, the 32-bit version of 8.04 no longer needs the boot parameters but the 64-bit does.

If you can, please post your wireless card info (lspci -nn).  We might be able to point you to some good options on getting your wireless to work.

---

### Post by poopdog on 2008-04-24
> **Ayuthia said:**
> If you can, please post your wireless card info (lspci -nn).  We might be able to point you to some good options on getting your wireless to work.

I'll get this info posted tonight.

Thanks for the help!

---

### Post by harry000 on 2008-04-24
Hi,

I have Pavilion dv5000 (I think the same wireless card as yours) and running Ubuntu 7.10

Basically, there are two solutions for making Broadcom Wireless card work:
1. bcm43xx-fwcutter
2. ndiswrapper

bcm43xx-fwcutter: This is the easiest solution. All you need to do is connect using wired connection first (you dont have to, but if you can connect using wired connection, it will just take a minute to make wireless card work. If you cannot connect to any wired connection, then you manually have to install bcm43xx-fwcutter package and then download the firmware). 
If you can connect using wired connection, just go to Restricted Manager, and enable the fwcutter from there. It will install the packege and download the firmware automatically, and your wireless connection will be working in no time.

But, it have problems. On my laptop, touchpad does not work very well if I have wireless working using fwcutter. It really gets annoying! 
And there is another problem: [http://ubuntuforums.org/showthread.php?t=703948](http://ubuntuforums.org/showthread.php?t=703948)

Ndiswrapper: This is the best possible solution. If you are able to get it work, it work flawlessly. 
Here are some link to get going. 
[https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper)

This one works for me perfectly:
[https://help.ubuntu.com/community/WifiDocs/Device/Broadcom_BCM4311_rev_01_(ndiswrapper](https://help.ubuntu.com/community/WifiDocs/Device/Broadcom_BCM4311_rev_01_(ndiswrapper))


PS: Another issue with my laptop is the graphics card. I have Radean 200M card and the current performance of Ubuntu is not very satisfying. Although, it gets installed quite easily using Restricted Manager, 3D effects also works... but the overall performance is sluggish.

---

### Post by Ayuthia on 2008-04-24
> **harry000 said:**
> Hi,

I have Pavilion dv5000 (I think the same wireless card as yours) and running Ubuntu 7.10

Basically, there are two solutions for making Broadcom Wireless card work:
1. bcm43xx-fwcutter
2. ndiswrapper

Actually, 8.04 is now using b43/b43legacy because bcm43xx is now depreciated.  As for the issues with the touchpad, that varies by model.  Mine has no problems and I am using the b43 drivers.

---

### Post by poopdog on 2008-04-24
> **harry000 said:**
> Hi,

I have Pavilion dv5000 (I think the same wireless card as yours) and running Ubuntu 7.10. 

Wow!  Thank you for this.

Yes, I believe our systems are pretty much the exact same thing except for stuff like drive space, screen size, etc.

Now I'm actually excited to go home and try this out.

Before I was dreading it, but it sounds like you had the answer I was looking for last time I went through all this.

I can't wait to get back onto Linux again.

I'll let you know how it goes.

---

### Post by carnitos on 2008-05-30
Hi folks, i have a pavilion dv6423 with kubuntu 8.04 Hardy Heron with the wireless working fine. Here's the URL:

[http://carnitos.wordpress.com/2008/05/30/pavilion-dv6000-broadcom-kubuntu-804/](http://carnitos.wordpress.com/2008/05/30/pavilion-dv6000-broadcom-kubuntu-804/)

Have a nice day! :)

---

