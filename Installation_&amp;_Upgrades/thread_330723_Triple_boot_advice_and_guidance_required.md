---
title: "Triple boot advice and guidance required"
date: 2007-01-03
forum: Installation &amp; Upgrades
---

### Post by skew on 2007-01-03
I'm having some trouble trying to figure out the best way to proceed transititioning to a  temporary triple boot, dual drive system from a dual boot, dual drive sytem where the two OS's are currently on the master drive.  

 Bear with me while I describe my present configuration. I have two SATA drives in system. The master has both winxp & Ubuntu from which the system (grub) dual boots . The other SATA slave drive had various windows partitons (now empty). What I'd like to do is turn the second slave drive over completely to Ubuntu and leave the master drive as is with XP & ubuntu (for the time being).  Eventually I'd like one drive (Master)dedicated to xp and the other (slave) to Ubuntu.  

  So to review I'd like the option to triple boot from either of the three installed OS while I get the new ubuntu(slave) drive up and running properly.  The reason I need to keep the orginal Ubuntu on the master available is because it also runs the mythtv. My family would not be happy if it's out of service for very long. Considering how long it took me to get  Mythtv up and running in the first place... well..., better not to temp fate. :-? 

  How should I proceed?  Can I simply install Ubuntu from the cd onto the slave drive while the master is attached and have confidence that the resulting grub will give me three OS's from which to choose from or is that a pipe dream? I would like it if all the drives files systems were available to each OS that was in control.  

  I just don't want to risk losing my orginal OS's or operational access to them. 

I hope the above wasn't to confusing.  Any help would be GREATLY appreciated. Thx

Steve

---

### Post by skew on 2007-01-04
Anybody?!   

  So I guess this problem is either too ridiculasly simple to get a reply or nobody has an soultion that'll work?

Which is it?

---

### Post by hardyn on 2007-01-04
so you want to put a full new install onto your second drive?

what you could do is actully NOT triple boot, but change the boot device upon boot up, and map the first device to be acessed by the second... am i making any sence?

leave first disk alone.

boot ubuntu disk, install to sata1 (i don't know what the unix abbriv. for sata is) at this time i you should be able to map over the patitions from sata0... you need a new swap partition on the second device.

now when machine is booting, press esc (or whatever) to change boot device to the second drive.

if you are really concerned about destroying the first install, de-cable the first device during the install, and add the other drives to fstab manually.  using the new UUID system in fstab this should actully work pretty well, but i have not tried it myself.

---

### Post by skew on 2007-01-04
Wow Hardyn I'm sorry man but ya completely lost me. ](*,) 

  last night I actually installed from cd to the second drive while the master was detached from the system. But when both drives are reconnected I get all kinds of errors as they're both are called sda1, etc. 

   Maybe in the long run it'd just be easier delete the orginal Ubuntu partion amd start fresh. Not really what I wanted to do but I don't see any other option that I can grasp being a newbie and all.

A big thanks all the same. 

Steve

---

### Post by confused57 on 2007-01-04
> **skew said:**
> Wow Hardyn I'm sorry man but ya completely lost me. ](*,) 

  last night I actually installed from cd to the second drive while the master was detached from the system. But when both drives are reconnected I get all kinds of errors as they're both are called sda1, etc. 

   Maybe in the long run it'd just be easier delete the orginal Ubuntu partion amd start fresh. Not really what I wanted to do but I don't see any other option that I can grasp being a newbie and all.

A big thanks all the same. 

Steve

You may have already deleted your original Ubuntu partition...if you haven't, can you boot to the "master" original drive set as first boot device(connected to your sata #1 controller)?

---

### Post by Scaryclouds on 2007-01-04
At the risk of sounding obvious, and potentially wrong. Just pop you Ubuntu disk in, follow the normal installation process and select the hard drive you want overwritten. This should give up the triple boot you want.

But what I really sounds like you want to do is but your Ubuntu partition onto your currently slave drive. The easiest way to do this is ghosting that partition and then bringing it down onto your slave drive. This should save you a lto of setup time and frustration ;) Let me see if I can find some links for you.

---

### Post by Scaryclouds on 2007-01-04
[http://www.systemimager.org/](http://www.systemimager.org/)

Here I hope this helps.

---

### Post by skew on 2007-01-04
Thanks guys! I haven't actually  done anything overtly distructive yet, still sitting on my hands for the time being.
  
   I have a  tar backup of the orginal Ubuntu partion from the master that I had hoped to transfer to the slave. BUT, it didn't want to take. To many errors like "where is sda1? This isn't sda1!" etc.

   I'll have a look at your link.   At this point anything is better then following my currenttly planned path, which is tantamount to runnng blind with sissors.;)  

Steve

---

