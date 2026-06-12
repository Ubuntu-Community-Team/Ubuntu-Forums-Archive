---
title: "Ubuntu 9.04 to Ubuntu 10 switch"
date: 2010-11-10
forum: Installation &amp; Upgrades
---

### Post by ddm101 on 2010-11-10
Hello,

I've been an Ubuntu user for a couple of months now and I've been learning everything from this forum. I recently tried to play a video on Totem only for it to ask me for a plug-in. I installed the plug-in and everything went berserk. Pidgin wouldn't run anymore. Totem disappeared, and videos started playing on my browser. I reinstalled Totem and Pidgin only for Totem to work poorly. I can't seek through videos and the image has deteriorated, showing blue shadows at times.

Anyway, when trying to do a general update I was told my distribution was not supported anymore so I decided I wanted a fresh start. I downloaded Ubuntu 10 and burned it on a CD but I'm quite new at this, so I have a few questions.

1. Will the fresh install of Ubuntu 10 get rid of all the things I modified on 9.04? (hopefully that's a YES)
2. Should I make a back-up copy of my data before I make the switch?
3. What's the simplest way of making the transition?

Thanks a lot in advance,

Daniel

---

### Post by tommcd on 2010-11-11
> **ddm101 said:**
> 
1. Will the fresh install of Ubuntu 10 get rid of all the things I modified on 9.04? (hopefully that's a YES)
Yes it will. Just install Ubuntu 10.x to the same root partition that you had 9.04 on. You will be starting with a pristine unmodified Ubuntu 10.x.
> **ddm101 said:**
> 
2. Should I make a back-up copy of my data before I make the switch?
If you have a separate /home partition, then your data is safe. Just choose manual partitioning, choose to format the root partition and install Ubuntu 10.x to the existing root partition. Then choose *do not format* the /home partition. And choose mount point /home for your home partition. Leave the swap partition as swap.
If you do not have a separate /home partition, then you will need to backup your data or else it will be lost when you install the new Ubuntu 10.x.
> **ddm101 said:**
> 
3. What's the simplest way of making the transition?

Just do a fresh install of Ubuntu 10.x (BTW there is Ubuntu 10.04 LTS and the newer 10.10. There is no Ubuntu 10. That is why I am using the wild card 10.x here).
If you do not have a separate home partition, then this would be a good time to repartition your hard drive and create one. See this:
[http://www.psychocats.net/ubuntu/installseparatehome](http://www.psychocats.net/ubuntu/installseparatehome)
Write back if you need more help.

And welcome to the Ubuntu forums!

---

### Post by darkhelmetchris on 2010-11-11
Yes, I agree with tommcd.  The new installation of Ubuntu 10 should overwrite your old tweaks (except for tweaks in your own home folder if you're keeping your home folder).

As a general practice, I have been using one small partition for "/" (root) and a separate larger partition for "/home" (home) as it makes reloading a snap.  When you manually partition, you can say that you want to keep your home partition (retaining all your settings and data) and load only the OS into the root partition.  So very handy.  I have had only very minimal tweaks needed for this.

I'm not sure what could have happened to damage your old installation, but, it kind of sounds like an aborted update that has run amuck.

---

