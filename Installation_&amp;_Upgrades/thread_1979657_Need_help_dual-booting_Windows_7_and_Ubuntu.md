---
title: "Need help dual-booting Windows 7 and Ubuntu"
date: 2012-05-13
forum: Installation &amp; Upgrades
---

### Post by pepperjinks on 2012-05-13
I'm new to Linux; received my friend's old laptop after he bought a new one. It's an HP, came pre-installed with Vista. 1GB RAM, one HDD with 120GBs, Athlon 64 X2 1.7GHz processor. I want to dual boot Windows 7 and Ubuntu because I can't afford to upgrade the hardware components right now and I know Ubuntu will run faster; I'll be using Windows 7 for games (compatibility) and Ubuntu for everything else.

I've done some reading. My intention is to create a Windows partition, an Ubuntu partition, and a data partition that can be shared between the two OSes should the need arise. There are just a lot of other things involved; a swap partition, for example (I don't understand what this is about--I assume it's for switching between the OSes).

**Basically**, I want to know:
 which partitions to create; 
how much space I should allocate for each of them; 
and how to set them all up when I install Windows 7, since that's the OS I need to install first.

Again, I only have 120 GBs to throw around, so I'll need some help with that. I have the most current version of Ubuntu burned to a DVD-RW (I did that yesterday). I also have an Active Killdisk DVD-RW that I'll use to wipe the hard drive.

Explanations for what I'm doing would be great. Any reading you think would help me would be awesome too. 

Thanks in advance. If I've left anything important out, just let me know.

---

### Post by wilee-nilee on 2012-05-13
This is a killer site for all kinds of stuff including dual booting.

[http://members.iinet.net.au/~herman546/index.html](http://members.iinet.net.au/~herman546/index.html)

---

### Post by jadtech on 2012-05-13
im sure there will be  a few people all with varied Idea's on partitioning I think just 50/ 50 would work in fact  50 or 60 gigs most likely will be way more then you will ever need for ubuntu .. 

frist thing I would do before any thing else pop the ubuntu dvd in the drive and boot see if you can boot  to test mode on with the live cd right off no tweaks or issues  you might find you need to go in bio's and set them to boot cd/dvd and USB first and then the hard drive ..

once you see if the Live disk you made will boot and test out good then I would move one to installing win7 hopefully win7 will be ok with the 1gb of ram it might be a bit of a struggle my guess is it was very slow with Vista  as I recall I never got vista to run well till after I got  the ram up to 2gb at 1gb it ran just slow and the themes colors and such were muted I want to say and games were out  the few I could get to run crashed alot unless i ran them in XP mode ..

aany how  the win7 install will wipe the whole drive when you install it just let it do its thing and install on the whole drive , once its installed and it boots then you can concern your self with shrinking volume on the window partition to by 60 gb to install ubuntu :)

---

### Post by jadtech on 2012-05-13
> **wilee-nilee said:**
> This is a killer site for all kinds of stuff including dual booting.

[http://members.iinet.net.au/~herman546/index.html](http://members.iinet.net.au/~herman546/index.html)

i used a site some what similar to this I found very  helpfull though I was more interested in manually partitioning ,most  because I feel to learn you have to do it  yourself  auto everything  dont teach you much really  unless it messes up  :)

---

### Post by Mark Phelps on 2012-05-14
Few pieces of advice ...

1) Install Win7 first.  Just use the whole drive and let it do the formatting.  Connect to the Internet and do any needed Windows Updates.  Keep doing this until there are no more updates.

2) Download and install the FREE version of Macrium Reflect on Win7.  Use the option to create and burn a Linux Boot CD.

3) Use the Win7 Disk Management Utility to shrink it down to 40 GB or so.  That will leave you some room for buffers and temp files -- which Win7 will need to boot and run.

4) Use Macrium Relfect to image off your Win7 setup to an external drive.

NOW, you have the means to quickly restore Win7 in the future if you should need to.

Boot from the Ubuntu CD/USB and use the Something Else option to create the partitions needed.  Do NOT use the Slider to do a side-by-side install because that risks corrupting the Win7 filesystem and rendering it unbootable.

---

### Post by pepperjinks on 2012-05-17
I've figured out how to do it. Thank you for all of your help, guys.

---

