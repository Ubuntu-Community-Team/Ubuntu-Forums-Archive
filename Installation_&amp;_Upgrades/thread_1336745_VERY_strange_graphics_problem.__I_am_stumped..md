---
title: "VERY strange graphics problem.  I am stumped."
date: 2009-11-24
forum: Installation &amp; Upgrades
---

### Post by parkland on 2009-11-24
OK.

I had a desktop computer with 9.04 , running 100%, for months.

Since I tried to install 9.10, there has been issues....huge issues.

Is there any settings in a graphics chipset that retain data??? Booting the 9.10 live cd arrives at an unsupported desktop resolution. 

Heres the really bad part- it now does it with the 9.04 live cd, and also the 8.xx cds I also have. It did NOT used to!!!!

I know this is not a failing hardware issue, because I was able to replicate it on the same board.

After 9.10 boots, the older cd's have the identical problem. 

I can not figure it out. All I want to do is get 9.04 & ext3 back on there so I can use it again.

---

### Post by jjcv on 2009-11-24
Your not going to get much help unless you provide more detail.  What is your graphics cart etc.

Try doing search on the specific card and see if anyone else has seen this sort of issue.

---

### Post by Mark Phelps on 2009-11-25
> **parkland said:**
> OK.

I had a desktop computer with 9.04 , running 100%, for months.

Since I tried to install 9.10, there has been issues....huge issues.

Is there any settings in a graphics chipset that retain data???

Basically, no.  BUT, you DID say that you TRIED to install 9.10.  So, how far did you get?  If you installed it and then encountered problems after rebooting, your installation changed the graphics settings, not the graphic chipset.

>  Booting the 9.10 live cd arrives at an unsupported desktop resolution. 

This kind of problem is exactly why everyone should try the LiveCD mode before an installation.  Had you done that, you would have discovered video problems.

>  Heres the really bad part- it now does it with the 9.04 live cd, and also the 8.xx cds I also have. It did NOT used to!!!

After 9.10 boots, the older cd's have the identical problem.  This doesn't make sense -- you either boot using a LiveCD or you boot to the installed OS.  Booting to a LiveCD doesn't use anything that you've already installed.

> All I want to do is get 9.04 & ext3 back on there so I can use it again.

Now THAT's a problem because there is no simple way to rollback to a prior Ubuntu release after an upgrade.

---

### Post by jaylsi on 2009-11-25
Is this nVidia card? I wonder if their new driver does a bios flush on the card that changes its behavior. I have a similar issue and I assume the card goes bad, but the timing is just too co-incident.

---

### Post by parkland on 2009-11-25
> **Mark Phelps said:**
> Basically, no.  BUT, you DID say that you TRIED to install 9.10.  So, how far did you get?  If you installed it and then encountered problems after rebooting, your installation changed the graphics settings, not the graphic chipset.

I installed using a different monitor, then updated and changed settings to make original monitor work



This kind of problem is exactly why everyone should try the LiveCD mode before an installation.  Had you done that, you would have discovered video problems.

 This doesn't make sense -- you either boot using a LiveCD or you boot to the installed OS.  Booting to a LiveCD doesn't use anything that you've already installed.

I know, but NONE of my ubuntu live CD's will successfully boot now, all end up at a non-displayable refresh or what not.

I thought my graphics card might be toast, but tried the same thing on an identical motherboard, and sure as heck, they all boot fine, till you boot 9.10 - then none boot. 

That is why i was asking if a graphics card can retain settings.



Now THAT's a problem because there is no simple way to rollback to a prior Ubuntu release after an upgrade.

I have not ever had a problem like this before, it really is impossible, non believable even...

---

### Post by parkland on 2009-11-25
> **jaylsi said:**
> Is this nVidia card? I wonder if their new driver does a bios flush on the card that changes its behavior. I have a similar issue and I assume the card goes bad, but the timing is just too co-incident.

This inspired me to do some googling-

I did NOT know that graphics cards could be updated, flashed, and reset... This makes tons of sense... something on the 9.10 live cd is flashing the graphics chipset. 

I can not find a motherboard graphics reset jumper, or a reset in the bios...resetting the main bios did nothing...

---

### Post by jaylsi on 2009-11-25
I believe you because I had the similar problem. Working fine in 8.04, and two weeks of 9.10, then it suddenly freezes. Then I tried all versions of live CDs, none of them works any more. I tried Vista, same thing. I think somehow the new system/driver causes card damage by either overheat or accidental bios overwrite, but I really have no idea what is going on.

---

### Post by JBAlaska on 2009-11-25
Are you SURE that your booting off the LiveCD's and not "passing through" to your HD install? Flushing the card's firmware..is well just silly.

---

### Post by Mark Phelps on 2009-11-25
> **parkland said:**
> This inspired me to do some googling-

I did NOT know that graphics cards could be updated, flashed, and reset... This makes tons of sense... 
That would be called flashing the firmware -- something you can do to any hardware device that includes EPROM chips -- but you need special software to do this. 

> something on the 9.10 live cd is flashing the graphics chipset. 
I know you think this is true, but I don't really see how that can happen because the LiveCD doesn't contain any firmware flashing capabilities.

> I can not find a motherboard graphics reset jumper, or a reset in the bios...resetting the main bios did nothing...
That's because there's nothing on the motherboard that has anything to do with video settings.  About the most you can do on some systems that have onboard graphics, is set some features there.  But the motherboard BIOS doesn't provide any way to configure features that are provided by plugin graphics cards.

All I can guess at this point is that, in the process of messing around with monitor configurations, you set the monitor frequency and/ or horizontal/vertical sync out of range -- something easy to do if the initial monitor had broader ranges than the second monitor.

---

### Post by parkland on 2009-11-26
> **Mark Phelps said:**
> That would be called flashing the firmware -- something you can do to any hardware device that includes EPROM chips -- but you need special software to do this. 


I know you think this is true, but I don't really see how that can happen because the LiveCD doesn't contain any firmware flashing capabilities.


I think the same, but I can not explain why this board will boot fine with every ubuntu cd i have, then after live 9.10 not boot any. And it is not passing through to hard disk, i quadruple checked. 




That's because there's nothing on the motherboard that has anything to do with video settings.  About the most you can do on some systems that have onboard graphics, is set some features there.  But the motherboard BIOS doesn't provide any way to configure features that are provided by plugin graphics cards.

All I can guess at this point is that, in the process of messing around with monitor configurations, you set the monitor frequency and/ or horizontal/vertical sync out of range -- something easy to do if the initial monitor had broader ranges than the second monitor.

My first monitor that didnt work was a 47" 1920x1080 lcd, one that worked was a 15" KDS CRT.

Is there any way something on the live CD crashes, and accidentally corrupts the video eeprom?
How could one check for that?

I am beyond my understanding & skill on this one...

---

